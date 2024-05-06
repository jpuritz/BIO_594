## Cassandra Cerasia
##### Dr. Puritz
##### BIO 594
##### 18 April 2024
```{bash}
Congrats!  You've finished the Filtering Exercise

 Please find out more about rad_haplotyper in this paper: "Willis, Stuart C., et al. "Haplotyping RAD loci: an efficient method to filter paralogs and account for physical linkage." Molecular Ecology Resources (2017).
 ```

 ### SNP Calling and FIltering 
 #### SNP Calling

 First I created the conda environment similar ot Ref.Ex
 ```
 conda create -n Week 11ddocent
 ```
 ```
 conda activate Week11
 ```
 Then I made a working firectory for this week.
 ```
 mkdir Week11.Ex
 ```
 ```
 cd Week11.Ex
 ```
 I then copied the data to the working directory.
 ```
cp /home/BIO594/Exercises/Week_11/*.fq.gz .
 ```
I then ran dDocent. 
```
dDocent
```
```
dDocent 2.9.7

Contact jpuritz@uri.edu with any problems


Checking for required software

All required software is installed!

dDocent version 2.9.7 started Tue Apr 16 14:01:05 EDT 2024

80 individuals are detected. Is this correct? Enter yes or no and press [ENTER]
```
```
80 individuals are detected. Is this correct? Enter yes or no and press [ENTER]
yes
Proceeding with 80 individuals
dDocent detects 80 processors available on this system.
Please enter the maximum number of processors to use for this analysis.
20

Do you want to quality trim your reads?
Type yes or no and press [ENTER]?
yes

Do you want to perform an assembly?
Type yes or no and press [ENTER].
yes

What type of assembly would you like to perform?  Enter SE for single end, PE for paired-end, RPE for paired-end sequencing for RAD protocols with random shearing, or OL for paired-end sequencing that has substantial overlap.
Then press [ENTER]
PE
Reads will be assembled with Rainbow
CD-HIT will cluster reference sequences by similarity. The -c parameter (% similarity to cluster) may need to be changed for your taxa.
Would you like to enter a new c parameter now? Type yes or no and press [ENTER]
yes
Please enter new value for c. Enter in decimal form (For 90%, enter 0.9)
0.9
Do you want to map reads?  Type yes or no and press [ENTER]
yes
BWA will be used to map reads.  You may need to adjust -A -B and -O parameters for your taxa.
Would you like to enter a new parameters now? Type yes or no and press [ENTER]
yes
Please enter new value for A (match score).  It should be an integer.  Default is 1.
1
Please enter new value for B (mismatch score).  It should be an integer.  Default is 4.
4
Please enter new value for O (gap penalty).  It should be an integer.  Default is 6.
6
Do you want to use FreeBayes to call SNPs?  Please type yes or no and press [ENTER]
yes

Please enter your email address.  dDocent will email you when it is finished running.
Don't worry; dDocent has no financial need to sell your email address to spammers.
cassandra.cerasia@uri.edu
```
dDocent then prompted me to set reference assembly cutoff values. 
```


                       Number of Unique Sequences with More than X Coverage (Counted within individuals)
   105000 +---------------------------------------------------------------------------------------------------------+
          |           +           +          +           +           +           +          +           +           |
          |*                                                                                                        |
   100000 |-***                                                                                                   +-|
          |    ****                                                                                                 |
          |        ******                                                                                           |
          |              ******                                                                                     |
    95000 |-+                  ***********                                                                        +-|
          |                               ******                                                                    |
          |                                     ******                                                              |
    90000 |-+                                         ******                                                      +-|
          |                                                 ******                                                  |
          |                                                       ******                                            |
    85000 |-+                                                           ******                                    +-|
          |                                                                   ******                                |
          |                                                                         ******                          |
    80000 |-+                                                                             *****                   +-|
          |                                                                                    ******               |
          |                                                                                          ******         |
          |                                                                                                ******   |
    75000 |-+                                                                                                    ***|
          |                                                                                                         |
          |           +           +          +           +           +           +          +           +           |
    70000 +---------------------------------------------------------------------------------------------------------+
          2           4           6          8           10          12          14         16          18          20
                                                           Coverage
```
```
Please choose data cutoff.  In essence, you are picking a minimum (within individual) coverage level for a read (allele) to be used in the reference assembly
4
```
```
                                 Number of Unique Sequences present in more than X Individuals
     3500 +---------------------------------------------------------------------------------------------------------+
          |            +             +            +            +            +             +            +            |
          |                                                                                                         |
          |                                                                                                         |
          |    *                                                                                                    |
     3000 |-+   *                                                                                                 +-|
          |      *                                                                                                  |
          |       *                                                                                                 |
          |        *                                                                                                |
     2500 |-+       *                                                                                             +-|
          |          *                                                                                              |
          |           **                                                                                            |
          |             **                                                                                          |
          |               **                                                                                        |
     2000 |-+               *****                                                                                 +-|
          |                      ***                                                                                |
          |                         *****                                                                           |
          |                              ********                                                                   |
     1500 |-+                                    ********                                                         +-|
          |                                              *************                                              |
          |                                                           *************                                 |
          |                                                                        *******************              |
          |            +             +            +            +            +             +           **************|
     1000 +---------------------------------------------------------------------------------------------------------+
          0            5             10           15           20           25            30           35           40
                                                     Number of Individuals

Please choose data cutoff.  Pick point right before the assymptote. A good starting cutoff might be 10% of the total number of individuals
8
```
```
At this point, all configuration information has been entered and dDocent may take several hours to run.
It is recommended that you move this script to a background operation and disable terminal input and output.
All data and logfiles will still be recorded.
To do this:
Press control and Z simultaneously
Type bg and press enter
Type disown -h and press enter
Now sit back, relax, and wait for your analysis to finish

dDocent assembled 2460 sequences (after cutoffs) into 1000 contigs

Using BWA to map reads
```
```
dDocent has finished with an analysis in /home/ccerasia/Week11.Ex

dDocent started Tue Apr 16 15:09:36 EDT 2024

dDocent finished Tue Apr 16 15:12:09 EDT 2024

After filtering, kept 3138 out of a possible 3280 Sites

dDocent 2.9.7
The 'd' is silent, hillbilly.
```
 #### SNP Filtering
First I made a directory. 
```
mkdir FilterSNPs
```
```
cd FilterSNPs/
```
Then, I linked the output VCF file docent created to this new directory.
``` 
ln -s ../TotalRawSNPs.vcf .
```
I then used VCFtools to begin filtering. 
```
vcftools --vcf TotalRawSNPs.vcf --max-missing 0.5 --minQ 30 --mac 3 --recode --recode-INFO-all --out raw.g5mac3
```
In this tool, the file name is after the --vcf flag. The --max-missing 0.5 tells it to filter genotypes called below 50% across all individuals. --mac 3 tells the code to filter SNPs that have a minor allele count less than three. 

```
VCFtools - 0.1.16
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
        --vcf TotalRawSNPs.vcf
        --recode-INFO-all
        --mac 3
        --minQ 30
        --max-missing 0.5
        --out raw.g5mac3
        --recode

After filtering, kept 80 out of 80 Individuals
Outputting VCF file...
After filtering, kept 1961 out of a possible 3280 Sites
Run Time = 1.00 seconds
```
There is now a filtered VCF called raw.g5mac3.recode.vcf. The following code recoded genotypes that have less than three reads. 

```
vcftools --vcf raw.g5mac3.recode.vcf --minDP 3 --recode --recode-INFO-all --out raw.g5mac3dp3
```

```
VCFtools - 0.1.16
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
        --vcf raw.g5mac3.recode.vcf
        --recode-INFO-all
        --minDP 3
        --out raw.g5mac3dp3
        --recode

After filtering, kept 80 out of 80 Individuals
Outputting VCF file...
After filtering, kept 1961 out of a possible 1961 Sites
Run Time = 1.00 seconds
```
Checking the error: 
```
curl -L -O https://github.com/jpuritz/dDocent/raw/master/scripts/ErrorCount.sh
chmod +x ErrorCount.sh 
./ErrorCount.sh raw.g5mac3dp3.recode.vcf 
```
```
This script counts the number of potential genotyping errors due to low read depth
It report a low range, based on a 50% binomial probability of observing the second allele in a heterozygote and a high range based on a 25% probability.
Potential genotyping errors from genotypes from only 1 read range from 0.0 to 0.0
Potential genotyping errors from genotypes from only 2 reads range from 0.0 to 0.0
Potential genotyping errors from genotypes from only 3 reads range from 48.25 to 162.12
Potential genotyping errors from genotypes from only 4 reads range from 22.25 to 112.496
Potential genotyping errors from genotypes from only 5 reads range from 14.40625 to 109
80 number of individuals and 1961 equals 156880 total genotypes
Total genotypes not counting missing data 156380
Total potential error rate is between 0.0005429482670418212 and 0.002453101419618877
SCORCHED EARTH SCENARIO
WHAT IF ALL LOW DEPTH HOMOZYGOTE GENOTYPES ARE ERRORS?????
The total SCORCHED EARTH error rate is 0.0076927995907405036.
```
Next, we get rid of individuals who sequenced poorly. This is done by assessing individual levels of missing data with the following command. 
```
vcftools --vcf raw.g5mac3dp3.recode.vcf --missing-indv
```
 ```
VCFtools - 0.1.16
(C) Adam Auton and Anthony Marcketta 2009

Parameters as interpreted:
        --vcf raw.g5mac3dp3.recode.vcf
        --missing-indv

 After filtering, kept 80 out of 80 Individuals
Outputting Individual Missingness
After filtering, kept 1961 out of a possible 1961 Sites
Run Time = 0.00 seconds
```
To plot the data: 
```
mawk '!/IN/' out.imiss | cut -f5 > totalmissing
gnuplot << \EOF
set terminal dumb size 120, 30
set autoscale
unset label
set title "Histogram of % missing data per individual"
set ylabel "Number of Occurrences"
set xlabel "% of missing data"
binwidth=0.01
bin(x,width)=width*floor(x/width) + binwidth/2.0
set lmargin 10
plot 'totalmissing' using (bin($1,binwidth)):(1.0) smooth freq with boxes
pause -1
EOF
```
```



                                          Histogram of % missing data per individual
       70 +---------------------------------------------------------------------------------------------------------+
          |*****************************************************          +         +          +         +          |
          |                                                   '*otalmissing' using (bin($1,binwidth)):(1.0) ******* |
       60 |-+                                                  *                                                  +-|
          |                                                    *                                                    |
          |                                                    *                                                    |
          |                                                    *                                                    |
       50 |-+                                                  *                                                  +-|
          |                                                    *                                                    |
          |                                                    *                                                    |
       40 |-+                                                  *                                                  +-|
          |                                                    *                                                    |
          |                                                    *                                                    |
       30 |-+                                                  *                                                  +-|
          |                                                    *                                                    |
          |                                                    *                                                    |
       20 |-+                                                  *                                                  +-|
          |                                                    *                                                    |
          |                                                    *****************************************************|
          |                                                    *                                                    |
       10 |-+                                                  *                                                  +-|
          |                                                    *                                                    |
          |          +         +          +         +          *          +         +          +         +          |
        0 +---------------------------------------------------------------------------------------------------------+
        0.005      0.006     0.007      0.008     0.009       0.01      0.011     0.012      0.013     0.014      0.015
                                                       % of missing data
```
Approximately 68 individuals have less than 0.01 missing data and the other 12 have between 0.01 and 0.015 missing data. Since all of the individuals have less than 0.5 missing data, this is a good cutoff to use.
Next, I restricted the data to variants that are called in a high percentage of individuals and filtered by mena depth of genotypes. 
```
vcftools --vcf raw.g5mac3dp3.recode.vcf --max-missing 0.95 --maf 0.05 --recode --recode-INFO-all --out DP3g95maf05 --min-meanDP 20
```
```
After filtering, kept 80 out of 80 Individuals
Outputting VCF file...
After filtering, kept 1150 out of a possible 1961 Sites
Run Time = 0.00 seconds
```
Next, I accessed the popmap in the directory above. 
```
head ../popmap
```
Then, I used these commands. 
```
mawk '$2 == "PopA"' ../popmap > A.keep
mawk '$2 == "PopB"' ../popmap > B.keep
mawk '$2 == "PopC"' ../popmap > C.keep
mawk '$2 == "PopD"' ../popmap > D.keep
```
Then, I used VCFtools to estimate the missign data in each population. 
```
vcftools --vcf DP3g95maf05.recode.vcf --keep A.keep --missing-site --out A

vcftools --vcf DP3g95maf05.recode.vcf --keep B.keep --missing-site --out B

vcftools --vcf DP3g95maf05.recode.vcf --keep C.keep --missing-site --out C

vcftools --vcf DP3g95maf05.recode.vcf --keep D.keep --missing-site --out D
```
All outputs were: 
```
After filtering, kept 20 out of 80 Individuals
Outputting Site Missingness
After filtering, kept 1150 out of a possible 1150 Sites
Run Time = 0.00 seconds
```

I then combined these four files and listed the loci at the threshold of 10% missing data needed to be removed with the following line of code:

```
cat A.lmiss B.lmiss C.lmiss D.lmiss | mawk '!/CHR/' | mawk '$6 > 0.1' | cut -f1,2 >> badloci
```
In the second line of code, the the "AB > 0.25 & AB < 0.75" tells the computer to filter out loci with an allele balance below 0.25 and above 0.75. However, it still includes those that are near zero based on "AB < 0.01" The last condition is to account for loci thatare fixed carients.  The -s tells the compter to apply the filter to all sites and not only just alleles. T
```
vcftools --vcf DP3g95maf05.recode.vcf --exclude-positions badloci --recode --recode-INFO-all --out DP3g95p5maf05

vcffilter -s -f "AB > 0.25 & AB < 0.75 | AB < 0.01" DP3g95p5maf05.recode.vcf > DP3g95p5maf05.fil1.vcf
```
Next, to see how many loci are in the VCF file, I used the mawk statments below. 
```
mawk '!/#/' DP3g95p5maf05.recode.vcf | wc -l
1150
```
```
mawk '!/#/' DP3g95p5maf05.fil1.vcf | wc -l
1142
```
8 loci were filtered.
The filter below then filters out sites that have reads from both strands. It is keeping loci that have over 100 times more forward alternate reads than reverse alternate reads and 100 times more forward reference reads than reverse reference reads and rhe reciprocol. 
```
vcffilter -f "SAF / SAR > 100 & SRF / SRR > 100 | SAR / SAF > 100 & SRR / SRF > 100" -s DP3g95p5maf05.fil1.vcf > DP3g95p5maf05.fil2.vcf
```
I then used mawk again to see how many loci are in the VCF file. 
```
mawk '!/#/' DP3g95p5maf05.fil2.vcf | wc -l
1142
```
Next, I used the following filter to examine the ratio of mapping qualities between reference and alterante alleles. This is because RADseq loci and alleles all begin at the same genomic location and there should not be a major discrepancy between the mapping qualities of two alleles. 
```
 vcffilter -f "MQM / MQMR > 0.9 & MQM / MQMR < 1.05" DP3g95p5maf05.fil2.vcf > DP3g95p5maf05.fil3.vcf
 ```
 Again, seeing how many loci are in the VCF file. 
 ```
  mawk '!/#/' DP3g95p5maf05.fil3.vcf | wc -l
  1142
  ```
The next filter applied examines if there is a discrepancy in the properly paired statys for reads that suport reference or alternate alleles.
```
vcffilter -f "PAIRED > 0.05 & PAIREDR > 0.05 & PAIREDR / PAIRED < 1.75 & PAIREDR / PAIRED > 0.25 | PAIRED < 0.05 & PAIREDR < 0.05" -s DP3g95p5maf05.fil3.vcf > DP3g95p5maf05.fil4.vcf
```
Again, seeing how many loci are in the VCF file.
```
mawk '!/#/' DP3g95p5maf05.fil4.vcf | wc -l
1142
```
I am unsure why the loci are not decreasing. 
The next filter is to look at the ratio of locus quality scores to depth. 
```
vcffilter -f "QUAL / DP > 0.25" DP3g95p5maf05.fil4.vcf > DP3g95p5maf05.fil5.vcf
```
Again, checking the number of loci in the file. 
```
mawk '!/#/' DP3g95p5maf05.fil5.vcf | wc -l
1140
```
Next, I created a list of the depth of each locus. 
```
cut -f8 DP3g95p5maf05.fil5.vcf | grep -oe "DP=[0-9]*" | sed -s 's/DP=//g' > DP3g95p5maf05.fil5.DEPTH
```
Then, I created a list of quality scores. 
```
mawk '!/#/' DP3g95p5maf05.fil5.vcf | cut -f1,2,6 > DP3g95p5maf05.fil5.vcf.loci.qual
```
Then, I calculated the mean depth. 
```
mawk '{ sum += $1; n++ } END { if (n > 0) print sum / n; }' DP3g95p5maf05.fil5.DEPTH
4702.36
```
Then, I calcualted the mean plus 3x the square of the mean. 
```
python2.7 -c "print int(4703+3*(4703**0.5))"
4908
```
Then, I pasted the depth and quality files together and found the loci above the cutiff that do not have quality scores  2 times the depth. 
```
paste DP3g95p5maf05.fil5.vcf.loci.qual DP3g95p5maf05.fil5.DEPTH | mawk -v x=4908 '$4 > x' | mawk '$3 < 2 * $4' > DP3g95p5maf05.fil5.lowQDloci
```
I then removed those cites and recalculated the depth across loci using vcftools. 
```
vcftools --vcf DP3g95p5maf05.fil5.vcf --site-depth --exclude-positions DP3g95p5maf05.fil5.lowQDloci --out DP3g95p5maf05.fil5
```

```
After filtering, kept 80 out of 80 Individuals
Outputting Depth for Each Site
After filtering, kept 1090 out of a possible 1140 Sites
Run Time = 0.00 seconds
```
Then, I took the VCF output and cut it to the depth scores only. 
```
cut -f3 DP3g95p5maf05.fil5.ldepth > DP3g95p5maf05.fil5.site.depth

mawk '!/D/' DP3g95p5maf05.fil5.site.depth | mawk -v x=31 '{print $1/x}' > meandepthpersite
```

After this, I plot the mean depth per site. 
```
gnuplot << \EOF 
set terminal dumb size 120, 30
set autoscale
set xrange [10:150] 
unset label
set title "Histogram of mean depth per site"
set ylabel "Number of Occurrences"
set xlabel "Mean Depth"
binwidth=1
bin(x,width)=width*floor(x/width) + binwidth/2.0
set xtics 5
plot 'meandepthpersite' using (bin($1,binwidth)):(1.0) smooth freq with boxes
pause -1
EOF
```
```


                                              Histogram of mean depth per site
     60 +-----------------------------------------------------------------------------------------------------------+
        |   +   +   +  +   +   +   +   +   +   +  +   +   +   +   +   +   +  +   +   +   +   +   +   +  +   +   +   |
        |                                                 'meandepthpersite' using (bin($1,binwidth)):(1.0) ******* |
        |                                                                                                      **   |
     50 |-+                                                                                                    ** +-|
        |                                                                                                      **   |
        |                                                                                                    ****   |
        |                                                                                                    *****  |
     40 |-+                                                                                                  *******|
        |                                                                                                    *******|
        |                                                                                                   ********|
     30 |-+                                                                                                 ********|
        |                                                                                                   ********|
        |                                                                                                   ********|
        |                                                                                               **  ********|
     20 |-+                                                                                             **  ********|
        |                                                                                               **  ********|
        |                                                                                               ** *********|
        |                                                                                               ** *********|
     10 |-+                                                                                            *************|
        |                                                                                           ** *************|
        |                                                                                       ********************|
        |   +   +   +  +   +   +   +   +   +   +  +   +   +   +   +   +   +  +   +   +   +  *****+******************|
      0 +-----------------------------------------------------------------------------------------------------------+
        10  15  20  25 30  35  40  45  50  55  60 65  70  75  80  85  90  9 100 105 110 115 120 125 13 135 140 145 150
                                                         Mean Depth
```
I think I did something wrong here since my mean depth is so high but I am not sure how to proceed since they are all so high. 

Then, I combined both filters to produce another VCF file. 
```
vcftools --vcf  DP3g95p5maf05.fil5.vcf --recode-INFO-all --out DP3g95p5maf05.FIL --max-meanDP 102.5 --exclude-positions DP3g95p5maf05.fil5.lowQDloci --recode 
```
```
After filtering, kept 80 out of 80 Individuals
Outputting VCF file...
After filtering, kept 1090 out of a possible 1140 Sites
Run Time = 0.00 seconds
```
The next filter is HWE. It has been found (Heng Li) that HWE is a good filter to remove errenous variant calls. We should not apply it across the board as population structure will make deviaitons from HWE as well. 
First, I converted the variante calls to SNPS with vcfallelicprimatives. This decomposes complex variant calls into phased SNO and INDEL genotypes. It keeps the INFO flags for loci and genotypes. Then, this goes to VCFtools to remove INDELSs.
```
vcfallelicprimitives DP3g95p5maf05.FIL.recode.vcf --keep-info --keep-geno > DP3g95p5maf05.prim.vcf
```
```
vcftools --vcf DP3g95p5maf05.prim.vcf --remove-indels --recode --recode-INFO-all --out SNP.DP3g95p5maf05
```
```
After filtering, kept 80 out of 80 Individuals
Outputting VCF file...
After filtering, kept 906 out of a possible 1158 Sites
Run Time = 0.00 seconds
```
Then, I applied the HWE filter. 

```
perl filter_hwe_by_pop.pl -v SNP.DP3g95p5maf05.recode.vcf -p popmap -o SNP.DP3g95p5maf05.HWE -h 0.01


Processing population: PopA (20 inds)
Processing population: PopB (20 inds)
Processing population: PopC (20 inds)
Processing population: PopD (20 inds)
Outputting results of HWE test for filtered loci to 'filtered.hwe'
Kept 904 of a possible 906 loci (filtered 2 loci)
```

