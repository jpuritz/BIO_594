## Exercise Part 1

Ran the `Ref.Ex` command line and completed tutorial.

## Exercise Part 2

**They are 1235 loci**

Make a new directory for week 10 and copied the files from `/home/BIO594/DATA/Week10/` into my directory called `week10`
```
mkdir week10
cp -r /home/BIO594/DATA/Week10/ ../ffields/week10
```

Creating a ddocent environment and mamba activating 
```
mamba create -n week10_ex ddocent
mamba activate week10_ex
```
These files have been demultiplexed so I skipped a few steps from the tutorial to now create unique reads with counts for each indivduals.
- The first four lines simply set variables for various AWK and perl code, to make parallelization with GNU-parallel easier. 
- The sixth line creates a set of forward reads for each individual by using mawk (a faster, c++ version of awk) to sort through the fastq file and strip away the quality scores. 
- The second line does the same for the PE reads.
- The last line concatentates the forward and PE reads together with 10 Ns between them and finds the unique reads within that specific individual and counts its occurences.
```	
ls *.F.fq.gz > namelist
sed -i'' -e 's/.F.fq.gz//g' namelist
AWK1='BEGIN{P=1}{if(P==1||P==2){gsub(/^[@]/,">");print}; if(P==4)P=0; P++}'
AWK2='!/>/'
AWK3='!/NNN/'
PERLT='while (<>) {chomp; $z{$_}++;} while(($k,$v) = each(%z)) {print "$v\t$k\n";}'

cat namelist | parallel --no-notice -j 8 "zcat {}.F.fq.gz | mawk '$AWK1' | mawk '$AWK2' > {}.forward"
cat namelist | parallel --no-notice -j 8 "zcat {}.R.fq.gz | mawk '$AWK1' | mawk '$AWK2' > {}.reverse"
cat namelist | parallel --no-notice -j 8 "paste -d '-' {}.forward {}.reverse | mawk '$AWK3' | sed 's/-/NNNNNNNNNN/' | perl -e '$PERLT' > {}.uniq.seqs"
```

For assembly we will eliminate reads with low copy numbers to remove data that is non imformative 

	 cat *.uniq.seqs > uniq.seqs
	 for i in {2..20};
	 do
	 echo $i >> pfile
	 done
	 cat pfile | parallel --no-notice "echo -n {}xxx && mawk -v x={} '\$1 >= x' uniq.seqs | wc -l" | mawk  '{gsub("xxx","\t",$0); print;}'| sort -g > uniqseq.data
	 rm pfile


Viewing the contents in the uniseq.data

```
more uniqseq.data

#Output
2       126508
3       122492
4       121026
5       119357
6       117552
7       115633
8       113606
9       111449
10      109143
11      106710
12      104198
13      101560
14      98723
15      95844
16      92812
17      89829
18      86728
19      83535
20      80401
```

Using gnuplot we will will plot this data in the terminal
	
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

	#Output
	
                        Number of Unique Sequences with More than X Coverage (Counted within individuals)
     130000 +-------------------------------------------------------------------------------------------------------+
            |           +          +           +          +           +          +           +          +           |
     125000 |**                                                                                                   +-|
            |  ******                                                                                               |
            |        ******                                                                                         |
     120000 |-+            *****                                                                                  +-|
            |                   ******                                                                              |
     115000 |-+                       ******                                                                      +-|
            |                               ******                                                                  |
     110000 |-+                                   *****                                                           +-|
            |                                          ******                                                       |
     105000 |-+                                              ******                                               +-|
            |                                                      ******                                           |
            |                                                            ******                                     |
     100000 |-+                                                                ****                               +-|
            |                                                                      ***                              |
      95000 |-+                                                                       ****                        +-|
            |                                                                             ******                    |
      90000 |-+                                                                                 *****             +-|
            |                                                                                        **             |
            |                                                                                          ****         |
      85000 |-+                                                                                            *****  +-|
            |           +          +           +          +           +          +           +          +       *** |
      80000 +-------------------------------------------------------------------------------------------------------+
            2           4          6           8          10          12         14          16         18          20
                                                            Coverage
The cut off value of 4 is choosen to capture as mush diveristy in the data while removing sequences that are errors
    
    parallel --no-notice -j 8 mawk -v x=4 \''$1 >= x'\' ::: *.uniq.seqs | cut -f2 | perl -e 'while (<>) {chomp; $z{$_}++;} while(($k,$v) = each(%z)) {print "$v\t$k\n";}' > uniqCperindv

Number of sequences

	wc -l uniqCperindv
    #Output
    12699 uniqCperindv

The data has now been reduced to 12699 sequences

Restricting the data by the number of different individuals a sequence appears within.

	for ((i = 2; i <= 10; i++));
	do
	echo $i >> ufile
	done

	cat ufile | parallel --no-notice "echo -n {}xxx && mawk -v x={} '\$1 >= x' uniqCperindv | wc -l" | mawk  '{gsub("xxx","\t",$0); print;}'| sort -g > uniqseq.peri.data
	rm ufile

Ploting the data:

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

	#Output
	
                                 Number of Unique Sequences present in more than X Individuals
     11000 +--------------------------------------------------------------------------------------------------------+
           |            +            +            +             +            +            +            +            |
           |                                                                                                        |
           |*                                                                                                       |
     10000 |-**                                                                                                   +-|
           |   ***                                                                                                  |
           |      ***                                                                                               |
           |         **                                                                                             |
      9000 |-+         ***                                                                                        +-|
           |              ***                                                                                       |
           |                 ****                                                                                   |
      8000 |-+                   ***                                                                              +-|
           |                        *****                                                                           |
           |                             ******                                                                     |
           |                                   *******                                                              |
      7000 |-+                                        *******                                                     +-|
           |                                                 *******                                                |
           |                                                        ******                                          |
           |                                                              *******                                   |
      6000 |-+                                                                   ******                           +-|
           |                                                                           **********                   |
           |                                                                                     **********         |
           |            +            +            +             +            +            +            +   ******   |
      5000 +--------------------------------------------------------------------------------------------------------+
           2            3            4            5             6            7            8            9            10
                                                     Number of Individuals
Chose a cutoff value of 4.
    
    mawk -v x=4 '$1 >= x' uniqCperindv > uniq.k.4.c.4.seqs
	wc -l uniq.k.4.c.4.seqs

    #Output
    7989 uniq.k.4.c.4.seqs
The data reduced to 7989 sequences
Convert sequences back into a fasta format

    cut -f2 uniq.k.4.c.4.seqs > totaluniqseq
	mawk '{c= c + 1; print ">Contig_" c "\n" $1}' totaluniqseq > uniq.fasta

#### Assembling reference contigs
Extracting the forward reads into a fasta file by replacing the 10N separator into a tab character and then using the cut function to split the files into forward reads

    sed -e 's/NNNNNNNNNN/\t/g' uniq.fasta | cut -f1 > uniq.F.fasta

Clustering all of the forward reads by 80% similarity

    cd-hit-est -i uniq.F.fasta -o xxx -c 0.8 -T 0 -M 0 -g 1

Converting the output of CD-Hit to match the ouput of the first phase of rainbow

     mawk '{if ($1 ~ /Cl/) clus = clus + 1; else  print $3 "\t" clus}' xxx.clstr | sed 's/[>Contig_,...]//g' | sort -g -k1 > sort.contig.cluster.ids
	 paste sort.contig.cluster.ids totaluniqseq > contig.cluster.totaluniqseq
	 sort -k2,2 -g contig.cluster.totaluniqseq | sed -e 's/NNNNNNNNNN/\t/g' > rcluster

Finding the exact number of clusters.

	cut -f2 rcluster | uniq | wc -l
    #Output
    1234

Splitting the loci into alleles

    rainbow div -i rcluster -o rbdiv.out

Lowing -f to 0.5
    
    rainbow div -i rcluster -o rbdiv.out -f 0.5 -K 10
    
Merging the clusters

    rainbow merge -o rbasm.out -a -i rbdiv.out -r 2

Extracting optimal contigs for RAD sequenecing Checking for overlap between F and PE reads in the contigs
    
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

Aligning and clustering by sequence similarity using CD-hit

    cd-hit-est -i rainbow.fasta -o referenceRC.fasta -M 0 -T 0 -c 0.9

Remaking the reference

    bash remake_reference.sh 4 4 0.90 PE 2

Examined the Reference
    
    head reference.fasta
    #Output
    >dDocent_Contig_1
    NAATTCATGGGATTCCCTGAGAGCACGAACGTCATTTACATCTAATACTCATTGGCACGTCATGCATTGGCAAAGACGAGTAGTTAGTGATAACGCCTAATCACCACGTCAACTGAANNNNNNNNNNGTGGGGTAGCGGGATAGTAAGCCCCCTGGATTGTCCTATTGACTGCGAAGACAAATAGCAGAGGTTCATACGCTCGGTCCTTTGCGCAGAGGACGGACGATTCGGACGCTATCCTAATTTTGCCGN
    >dDocent_Contig_2
    NAATTCGTTTGCCCACGGCTTCCACTAAAAGTTGCCCGCAGAACGGATCACTCCAGTATATGCTGCAGTTTGGATGTGAGAGCGGATAGTTTTGCTAATCATCCACGGGCCGTTAGTNNNNNNNNNNCGTAAGGCATCGGATTTACACGGTATACGTCCGATGCATTGCTTGTACCCACGTCCGAATTCATCGACGTGCGCACTCCTGATTATAACTTAACAATAGTCATAACGCCGGGCTCCCTGGTTCCGN
    >dDocent_Contig_3
    NAATTCACGGCTATCAACTAGGATGGTGGTTACTATTAGTGAGTGCTGTGTATTTCCGCTGCCGTCACTTGCAAGGCAGTAAACCCTTGGTGGCACGTGTAATCCAGCGTATGCAATNNNNNNNNNNCCTGGCCATAGTATTGCTCTAGCATAAAACAAGAGTTATGTATCTTGCCTTCCGGCTAGTCACCTATAGTGATTTGAGCTATTGAAAAGTCACGTTGACTGGAGGTAGAGAGTGGAATACTTCCGN
    >dDocent_Contig_4
    NAATTCAGCAACTCAAGTAATTCTGTGACTGCCACACCTTTCACCTGTAAGGCACTCGCGTACATCATTAGATCTTATTTGAAAGACCTGGCGTCGCCAATGTTGTCCGCAATAATCNNNNNNNNNNTGCGTACTCACGTTGTTATATAATGCAGCCGTCACACAATTTCGTGGATCGGCTACGGTGCGGGACTGAGACATACGTACGGTCAATAGGAGTAATAATCGCTTCATCATGATACTGGCTGTCCGN
    >dDocent_Contig_5
    NAATTCTCTGGCATTAATACCTTTATTTCTTTCCCGGAATTTGGTCCATACGCCAAAACCACATTAACTTTACACAGACCATGTCCTCGACGGTCGAATTTAGACAAATTTCTAGTGNNNNNNNNNNCCGTTATTGAACCGAACTATCCTGTTTGATTCGGGGCCTTGGATTTTGACTGGCGTAAGTGCACCGAATTTATAGTATACAATTTTTCACGGGGTAGACGAGTGCGATATCGATCGAGTGAACCGN

Finding ou how many lines are in this file
    
    wc -l reference.fasta
    #Output
    2470 reference.fasta

Number of sequences
    
    mawk '/>/' reference.fasta | wc -l
    #Output
    1235 

Testing all sequences
    
    mawk '/^NAATT.*N*.*CCGN$/' reference.fasta | wc -l
	grep '^NAATT.*N*.*CCGN$' reference.fasta | wc -l
    #Output
    1235

