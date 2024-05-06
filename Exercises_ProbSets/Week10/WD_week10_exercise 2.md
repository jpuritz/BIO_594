# Week 10 Exercise 2 

Make  directory for files 
```{bash}
mkdir Week10.Ex
```

Copy fq.gz files into my directory 
```{bash}
cp -R  Week10/ ../../wdunster/Week10.Ex
```

Following Ref.Ex change into the directory with the files and create a conda environment
```{bash}
cd Week10
mamba create -n Week10 ddocent
conda activate Week10 
```

These files have already been demultiplexed! So I skipped processing radtags and went to creating a list of uniq reads
 The first four lines simply set shell variables for various bits of AWK and perl code, 
 to make parallelization with GNU-parallel easier. The first line after the variables, 
 creates a set of forward reads for each individual by using mawk (a faster, c++ version of awk) 
 to sort through the fastq file and strip away the quality scores.  The second line does the same for the PE reads.  
 Lastly, the final line concatentates the forward and PE reads together (with 10 Ns between them) and then find the 
 unique reads within that individual and counts the occurences (coverage).
```{bash}
ls *.F.fq.gz > namelist #list all sample names and write into a namelist
sed -i'' -e 's/.F.fq.gz//g' namelist #search for .F.fq.gz and replaces it with nothing
AWK1='BEGIN{P=1}{if(P==1||P==2){gsub(/^[@]/,">");print}; if(P==4)P=0; P++}'
AWK2='!/>/'
AWK3='!/NNN/'
PERLT='while (<>) {chomp; $z{$_}++;} while(($k,$v) = each(%z)) {print "$v\t$k\n";}'
 
cat namelist | parallel --no-notice -j 8 "zcat {}.F.fq.gz | mawk '$AWK1' | mawk '$AWK2' > {}.forward"
cat namelist | parallel --no-notice -j 8 "zcat {}.R.fq.gz | mawk '$AWK1' | mawk '$AWK2' > {}.reverse"
cat namelist | parallel --no-notice -j 8 "paste -d '-' {}.forward {}.reverse | mawk '$AWK3' | sed 's/-/NNNNNNNNNN/' | perl -e '$PERLT' > {}.uniq.seqs"
```

Sequences with very small levels of coverage within an individual are likely to be sequencing errors.  
So, for assembly, we can eliminate reads with low copy numbers to remove non-informative data!
```{bash}
cat *.uniq.seqs > uniq.seqs
for i in {2..20}; #choosing to keep seqs for indv with copy numbers of 2-20
do 
echo $i >> pfile
done
cat pfile | parallel --no-notice "echo -n {}xxx && mawk -v x={} '\$1 >= x' uniq.seqs | wc -l" | mawk  '{gsub("xxx","\t",$0); print;}'| sort -g > uniqseq.data
rm pfile
```

View file uniqseq.data
```{bash}
more uniqseq.data
#output:
2	126508
3	122492
4	121026
5	119357
6	117552
7	115633
8	113606
9	111449
10	109143
11	106710
12	104198
13	101560
14	98723
15	95844
16	92812
17	89829
18	86728
19	83535
20	80401
```

Plot to the terminal 
```{bash}
gnuplot << \EOF 
 set terminal dumb size 120, 30
 set autoscale
 set xrange [2:20] 
 unset label
 set title "Number of Unique Sequences with More than X Coverage (Counted within individuals)"
 set xlabel "Coverage"
 set ylabel "Number of Unique Sequences"
 plot 'uniqseq.data' with lines notitle
 pause -1
 EOF

```

Choose a cut off value, or decide how much coverage allows an individual to be included in analysis-- honestly I do not understand why the tutorial chooses 4, but I will do the same
```{bash}
parallel --no-notice -j 8 mawk -v x=4 \''$1 >= x'\' ::: *.uniq.seqs | cut -f2 | perl -e 'while (<>) {chomp; $z{$_}++;} while(($k,$v) = each(%z)) {print "$v\t$k\n";}' > uniqCperindv
wc -l uniqCperindv
 ```

12699 uniqCperindv -- so we currently have 12699 uniq seqs 

Restrict data by the number of individuals a seq appears in. I believe this code is limiting it to sequences that appear in atleast 2 but no more than 10 individuals 

```{bash}
for ((i = 2; i <= 10; i++));
do
echo $i >> ufile
done
 
 cat ufile | parallel --no-notice "echo -n {}xxx && mawk -v x={} '\$1 >= x' uniqCperindv | wc -l" | mawk  '{gsub("xxx","\t",$0); print;}'| sort -g > uniqseq.peri.data
rm ufile
```

Plot the data
```{bash}
gnuplot << \EOF 
set terminal dumb size 120, 30
set autoscale 
unset label
set title "Number of Unique Sequences present in more than X Individuals"
set xlabel "Number of Individuals"
set ylabel "Number of Unique Sequences"
plot 'uniqseq.peri.data' with lines notitle
pause -1
EOF
```

Choose a copy number cut off value of 4 ?? IS THIS SAYING SEQ IN 4 INDVS?
```{bash}
 mawk -v x=4 '$1 >= x' uniqCperindv > uniq.k.4.c.4.seqs
 wc -l uniq.k.4.c.4.seqs
```

There are now 7989 sequences 

Convert files back to FASTA format 
```{bash}
cut -f2 uniq.k.4.c.4.seqs > totaluniqseq
mawk '{c= c + 1; print ">Contig_" c "\n" $1}' totaluniqseq > uniq.fasta
```

I'm not sure if I should have filtered Illumina adapter but I will pretend the data is simulated so I don't have to 

Start assembling reference contigs 
Seperate the F reads into a F.fasta file 
```{bash}
sed -e 's/NNNNNNNNNN/\t/g' uniq.fasta | cut -f1 > uniq.F.fasta
```

Cluster forward reads by 80% similarity
```{bash}
cd-hit-est -i uniq.F.fasta -o xxx -c 0.8 -T 0 -M 0 -g 1
```

Convert the above output to match rainbow 
```{bash}
mawk '{if ($1 ~ /Cl/) clus = clus + 1; else  print $3 "\t" clus}' xxx.clstr | sed 's/[>Contig_,...]//g' | sort -g -k1 > sort.contig.cluster.ids
paste sort.contig.cluster.ids totaluniqseq > contig.cluster.totaluniqseq
sort -k2,2 -g contig.cluster.totaluniqseq | sed -e 's/NNNNNNNNNN/\t/g' > rcluster
```

Find the number of clusters 
```{bash}
cut -f2 rcluster | uniq | wc -l 
```
There are 1234 clusters or 1234 RAD loci?? 

Split loci clusters into allele clusters (sig variants)
```{bash}
rainbow div -i rcluster -o rbdiv.out 
```

Lower the -f paramets from 0.2 to 0.5 (min freq of allele to divide it into its own cluster)
```{bash}
rainbow div -i rcluster -o rbdiv.out -f 0.5 -K 10
```

Merge divided clusters -- all base on F so pair up with R 
```{bash}
rainbow merge -o rbasm.out -a -i rbdiv.out -r 2 #-r means min num reads to assemble
```

Retrieve optimal contigs from rainbow 
```{bash}
cat rbasm.out <(echo "E") |sed 's/[0-9]*:[0-9]*://g' | mawk ' {
if (NR == 1) e=$2;
else if ($1 ~/E/ && lenp > len1) {c=c+1; print ">dDocent_Contig_" e "\n" seq2 "NNNNNNNNNN" seq1; seq1=0; seq2=0;lenp=0;e=$2;fclus=0;len1=0;freqp=0;lenf=0}
else if ($1 ~/E/ && lenp <= len1) {c=c+1; print ">dDocent_Contig_" e "\n" seq1; seq1=0; seq2=0;lenp=0;e=$2;fclus=0;len1=0;freqp=0;lenf=0}
else if ($1 ~/C/) clus=$2;
else if ($1 ~/L/) len=$2;
else if ($1 ~/S/) seq=$2;
else if ($1 ~/N/) freq=$2;
else if ($1 ~/R/ && $0 ~/0/ && $0 !~/1/ && len > lenf) {seq1 = seq; fclus=clus;lenf=len}
else if ($1 ~/R/ && $0 ~/0/ && $0 ~/1/) {seq1 = seq; fclus=clus; len1=len}
else if ($1 ~/R/ && $0 ~!/0/ && freq > freqp && len >= lenp || $1 ~/R/ && $0 ~!/0/ && freq == freqp && len > lenp) {seq2 = seq; lenp = len; freqp=freq}
}' > rainbow.fasta
```

Align and cluster contigs by sequence similarity 
```{bash}
cd-hit-est -i rainbow.fasta -o referenceRC.fasta -M 0 -T 0 -c 0.9

#-c sets the %similarity to group contigs by 
```

Remake the reference 
```{bash}
bash remake_reference.sh 4 4 0.90 PE 2
```

Find number of lines in reference.fasta = 2x sequences 
```{bash}
wc -l reference.fasta
```
There are 2470 lines 

Count number of sequences
```{bash}
mawk '/>/' reference.fasta | wc -l 
```
There are 1235 seqs 

Make sure all sequences follow the correct format 
```{bash}
mawk '/^NAATT.*N*.*CCGN$/' reference.fasta | wc -l #all seqs start w/ NAATT followed by R1 and 10Ns, they end with CCGN
grep '^NAATT.*N*.*CCGN$' reference.fasta | wc -l 
```

