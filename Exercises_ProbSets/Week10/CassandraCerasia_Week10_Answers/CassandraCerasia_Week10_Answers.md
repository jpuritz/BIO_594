### Cassandra Cerasia
#### April 11, 2024
## Exercise 2
I completed this using the [Reference Asssembly Tutorial](http://www.ddocent.com/assembly/) from dDocent. I found 1235 loci are in the dataset. 

First I made a directory for this week's assignment.
```{bash}
mkdir Week10.Ex
```
I then copied the filies into the directory I made above

```{bash}
(base) [ccerasia@KITT DATA]$  cp -R Week10 ../../ccerasia/Week10.Ex
```
Simillarly to what we did in Ref.Ex:
```{bash}
cd Week10
mamba create -n Week10 ddocent
```
I then restarted Kitt and activated it.
```{bash}
conda activate Week10 
```

As the assignment said, these files have already been demultiplexed. So I continued by creating a set of unique reads with counts for each individual. The first four lines of the below code set variables for the code. The fifth line creates forward reads for the individuals by using a version of awk to sort through the fastq file and strip the quality scores. The next line does the same thing for PE reads. THe last line concatonates the forward and PE reads together with 10 Ns in the middle and then finds the unique reads in the individual and counts the coverage.
```{bash}
ls *.F.fq.gz > namelist
sed -i'' -e 's/.F.fq.gz//g' namelist
AWK1='BEGIN{P=1}{if(P==1||P==2){gsub(/^[@]/,">");print}; if(P==4)P=0; P++}'
AWK2='!/>/'
AWK3='!/NNN/'
PERLT='while (<>) {chomp; $z{$_}++;} while(($k,$v) = each(%z)) {print "$v\t$k\n";}

cat namelist | parallel --no-notice -j 8 "zcat {}.F.fq.gz | mawk '$AWK1' | mawk '$AWK2' > {}.forward"
cat namelist | parallel --no-notice -j 8 "zcat {}.R.fq.gz | mawk '$AWK1' | mawk '$AWK2' > {}.reverse"
cat namelist | parallel --no-notice -j 8 "paste -d '-' {}.forward {}.reverse | mawk '$AWK3' | sed 's/-/NNNNNNNNNN/' | perl -e '$PERLT' > {}.uniq.seqs"
```

Next, I got rid of the reads with low copt numbers to get rid of uninformative data. This is to get rid of any sequencing errors. First I summed up the number within individual coverage levels of unique reads in the data set. This is a  BASH for loop sthat uses mawk to go through the first column and selects data above a a copy number from 2-20 and prints that to a file. 

```{bash}
cat *.uniq.seqs > uniq.seqs
for i in {2..20};
do 
echo $i >> pfile
done
cat pfile | parallel --no-notice "echo -n {}xxx && mawk -v x={} '\$1 >= x' uniq.seqs | wc -l" | mawk  '{gsub("xxx","\t",$0); print;}'| sort -g > uniqseq.data
rm pfile
```

To look at the data with the number of unique sequences that have a copy number of 2-20:
```{bash}
more uniqseq.data
```
I then plot that data using gnuplot:
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
```{bash}

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
```

Now that I have obtained the information regarding the number of reads with low copy numbers, I had to choose a cutoff value for the data I wished to keep. I aimed to choose a value that covers as much of the data as possible while eliminating sequences that are errors. I started with 4 as reccomended in the tutorial. 
```{bash}
parallel --no-notice -j 8 mawk -v x=4 \''$1 >= x'\' ::: *.uniq.seqs | cut -f2 | perl -e 'while (<>) {chomp; $z{$_}++;} while(($k,$v) = each(%z)) {print "$v\t$k\n";}' > uniqCperindv
wc -l uniqCperindv
```
This reduced the data to 12699 unique sequences. I then restricted the data by the number of different individuals the sequence appears within. I plot the data again before deciding a cutoff. 
```{bash}
for ((i = 2; i <= 10; i++));
do
echo $i >> ufile
done

cat ufile | parallel --no-notice "echo -n {}xxx && mawk -v x={} '\$1 >= x' uniqCperindv | wc -l" | mawk  '{gsub("xxx","\t",$0); print;}'| sort -g > uniqseq.peri.data
rm ufile
```
To plot the number of unique sequences present in more than X individuals: 
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
```{bash}

 Number of Unique Sequences present in more than X Individuals
     11000 +--------------------------------------------------------------------------------------------------------+
           |            +            +            +
 +            +            +            +            |
           |
                                                     |
           |*
                                                     |
     10000 |-**
                                                   +-|
           |   ***
                                                     |
           |      ***
                                                     |
           |         **
                                                     |
      9000 |-+         ***
                                                   +-|
           |              ***
                                                     |
           |                 ****
                                                     |
      8000 |-+                   ***
                                                   +-|
           |                        *****
                                                     |
           |                             ******
                                                     |
           |                                   *******
                                                     |
      7000 |-+                                        *******                                                     +-|
           |                                                 *******                                                |
           |
     ******                                          |
           |
           *******                                   |
                  ******                           +-|
           |
                        **********                   |
           |
                                  **********         |
           |            +            +            +
 +            +            +            +   ******   |
      5000 +--------------------------------------------------------------------------------------------------------+
           2            3            4            5
 6            7            8            9            10
                                                     Number of Individuals
```
I then needed to choose another cutoff value. This value should again be a cutoff value that captures as much of the data as possible while also eliminating sequences that do not have a great impact on the population scale. I tried 4 again per the tutorials reccomendation.
```{bash}
mawk -v x=4 '$1 >= x' uniqCperindv > uniq.k.4.c.4.seqs
wc -l uniq.k.4.c.4.seqs
``` 
This left me with 7989 sequences. I then converted the files back to fasta format.
```{bash}
cut -f2 uniq.k.4.c.4.seqs > totaluniqseq
mawk '{c= c + 1; print ">Contig_" c "\n" $1}' totaluniqseq > uniq.fasta
```
I then had my reduced data set and continued to start assembling reference contigs. FIrst, I extracted the forward reads from the fasta files I just made. This is done by using sed to replace the 10N separator I added a few steps back into a tab character and then uses cut to split the files into forward reads.
```{bash}
sed -e 's/NNNNNNNNNN/\t/g' uniq.fasta | cut -f1 > uniq.F.fasta
```
Then, I clustered all of the forward reads by 80% similarity. A low value is used at this step since other functions of rainbow will later break up clusters given the number and frequency of variants.
```{bash}
cd-hit-est -i uniq.F.fasta -o xxx -c 0.8 -T 0 -M 0 -g 1
```
```{bash}
================================================================
                            Output
----------------------------------------------------------------
total number of CPUs in the system is 80
Actual number of CPUs to be used: 80

total seq: 7989
longest and shortest : 116 and 116
Total letters: 926724
Sequences have been sorted

Approximated minimal memory consumption:
Sequence        : 1M
Buffer          : 80 X 17M = 1414M
Table           : 2 X 16M = 33M
Miscellaneous   : 4M
Total           : 1454M

Table limit with the given memory limit:
Max number of representatives: 248606
Max number of word counting entries: 6715988

# comparing sequences from          0  to       7238
.......---------- new table with     1234 representatives
# comparing sequences from       7238  to       7989
....................---------- new table with        0 representatives

     7989  finished       1234  clusters
```
I then convert the outputs of the cd-hit function to match the output for the first phase of rainbow. 
```{bash}
mawk '{if ($1 ~ /Cl/) clus = clus + 1; else  print $3 "\t" clus}' xxx.clstr | sed 's/[>Contig_,...]//g' | sort -g -k1 > sort.contig.cluster.ids
paste sort.contig.cluster.ids totaluniqseq > contig.cluster.totaluniqseq
sort -k2,2 -g contig.cluster.totaluniqseq | sed -e 's/NNNNNNNNNN/\t/g' > rcluster
```
I then got the number of clusters in rclusters.
```{bash}
cut -f2 rcluster | uniq | wc -l 
```
There are 1234 clusters. Next, I used rainbow to split clusters that were formed in the first step into smaller clusters that represented significant variants, or allele clusters. The first clustering step I completed found RAD loci, and this step splits the loci into alleles. This also aids in breaking up over clustered sequences. 
```{bash}
rainbow div -i rcluster -o rbdiv.out 
```
The output of this dev process is simillar to the previous output except the second column now is the new divided cluster_ID and there was an additional column made at the end of the file that holds the original cluster ID. The -f flag controls the minimum frequency of an allele that is needed to divide it into its own cluster. 
```{bash}
rainbow div -i rcluster -o rbdiv.out -f 0.5 -K 10
```
Next, I used paired ends to merge divided clusters. This aids to check the clustering and dividing of the previous steps that were based on the forward read only. If divided clusters represent allelese from the same homologus locus, they should have similar paired end reads (PE) and forward reads. Divided clusters that do not share similarity in the PE read represent cluster paralogs or representative regions. After the divided clusters are combined, all the forward and reverse reads are pooled and assembled for the specific cluster. 
```{bash}
rainbow merge -o rbasm.out -a -i rbdiv.out
```
Next, I used the -r parameter. This represents the minimum number of reads to assemble. I used a value of 2 as the tutorial reccomended as this is a reduced dataset.
```{bash}
rainbow merge -o rbasm.out -a -i rbdiv.out -r 2
```

rbasm then lists optimal and suboptimal contigs. I then isolated th eoptimal contigs from rainbow for RAD sequencing. First, this code looks at all the contigs for a specific cluster. If any conrigs have both forward and PE reads, the contig is considered optimal. If no overlap contigs exist, then the contig with the most assembled reads PE is outpit with the forward read conrig with a 10N spacer. If two contigs have the same number of reads, the longer contig is output.
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
Next, I aligned the resulting contigs and clustered them by sequence similarity with cd-hit. -M and -T represent instructions on memory usage (-M) and number of threads (-T). When set to 0, they use all that is avaluble. -c sets the percentage of sequence similarity to group contigs. The code below uses 90%. 
```{bash}
cd-hit-est -i rainbow.fasta -o referenceRC.fasta -M 0 -T 0 -c 0.9
```

```{bash}
     ================================================================
                            Output
----------------------------------------------------------------
total number of CPUs in the system is 80
Actual number of CPUs to be used: 80

total seq: 1235
longest and shortest : 373 and 233
Total letters: 310904
Sequences have been sorted

Approximated minimal memory consumption:
Sequence        : 0M
Buffer          : 80 X 17M = 1412M
Table           : 2 X 16M = 33M
Miscellaneous   : 4M
Total           : 1450M

Table limit with the given memory limit:
Max number of representatives: 248606
Max number of word counting entries: 10919214

# comparing sequences from          0  to         15
---------- new table with       15 representatives
# comparing sequences from         15  to         29
..............---------- new table with       14 representatives
# comparing sequences from         29  to         43
..............---------- new table with       14 representatives
# comparing sequences from         43  to         57
..............---------- new table with       14 representatives
# comparing sequences from         57  to         71
..............---------- new table with       14 representatives
# comparing sequences from         71  to         85
..............---------- new table with       14 representatives
# comparing sequences from         85  to         99
..............---------- new table with       14 representatives
# comparing sequences from         99  to        112
.............---------- new table with       13 representatives
# comparing sequences from        112  to        125
.............---------- new table with       13 representatives
# comparing sequences from        125  to        138
.............---------- new table with       13 representatives
# comparing sequences from        138  to        151
.............---------- new table with       13 representatives
# comparing sequences from        151  to        164
.............---------- new table with       13 representatives
# comparing sequences from        164  to        177
.............---------- new table with       13 representatives
# comparing sequences from        177  to        189
............---------- new table with       12 representatives
# comparing sequences from        189  to        201
............---------- new table with       12 representatives
# comparing sequences from        201  to        213
............---------- new table with       12 representatives
# comparing sequences from        213  to        225
............---------- new table with       12 representatives
# comparing sequences from        225  to        237
............---------- new table with       12 representatives
# comparing sequences from        237  to       1235
.....................---------- new table with      998 representatives

     1235  finished       1235  clusters
```
In real world data, it is difficult to know the correct number of reference contigs and takes a lot of data exploration. The script downloaded below automates this process. 
```{bash}
curl -L -O https://github.com/jpuritz/dDocent/raw/master/scripts/remake_reference.sh
```

I then remade the reference with the above script and parameters.
```{bash}
bash remake_reference.sh 4 4 0.90 PE 2
```
I then examined the reference.
```{bash}
head reference.fasta
```
Output:
```{bash}
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
```
```{bash}
wc -l reference.fasta
``` 
2470 lines

```{bash}
mawk '/>/' reference.fasta | wc -l 
```
### 1235 contigs

I then checked that everything followed the expected format.
```{bash}
mawk '/^NAATT.*N*.*CCGN$/' reference.fasta | wc -l
grep '^NAATT.*N*.*CCGN$' reference.fasta | wc -l
```
1235 contigs

1235 contigs

## 1235 loci are in the dataset.