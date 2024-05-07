# Assignment due on 4/18/2023


In the directory, `/home/BIO594/Exercises/Week_11`, you will find fastq files, library information, environmental info, and a popmap.

I would like you to complete the following and push it to your own folder in this repository directory.

* For the simulated data
  * Call SNPs
  * Filter the SNPs
 
Make new directory and copy the files from `/home/BIO594/Exercises/Week_11` into my week11 folder and create a ddocent environment 

	mkdir week11
	cp -r /home/BIO594/Exercises/Week_11_/ ../ffields/week11
	mamba create -n week_11 ddocent
	source activate week_11 #Does thesame thing as mamba activate Filter_Ex

Take a look at the data

	ll

Using the files `TotalRawSNPs.vcf` to begin the 3 step filter. filtering genotypes called below 50% 

	vcftools --gzvcf TotalRawSNPs.vcf --max-missing 0.5 --minQ 30 --mac 3 --recode --recode-INFO-all --out raw.g5mac3
```
###End Of Output###
After filtering, kept 80 out of 80 Individuals
Outputting VCF file...
After filtering, kept 1922 out of a possible 3025 Sites
```

Filter for genotypes that have less than 3 reads.

	vcftools --vcf raw.g5mac3.recode.vcf --minDP 3 --recode --recode-INFO-all --out raw.g5mac3dp3

	###EndOfOutput###
	After filtering, kept 80 out of 80 Individuals
	Outputting VCF file...
	After filtering, kept 1922 out of a possible 1922 Sites

Evaluated potential errors (counts the # of potential genotyping errors due to low read depth)

	curl -L -O https://github.com/jpuritz/dDocent/raw/master/scripts/ErrorCount.sh
	chmod +x ErrorCount.sh
	./ErrorCount.sh raw.g5mac3dp3.recode.vcf

```
###Ouput###
ac3dp3.recode.vcf  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100  3046  100  3046    0     0   8235      0 --:--:-- --:--:-- --:--:--  8235
(week_11) [ffields@KITT Week_11]$ chmod +x ErrorCount.sh
(week_11) [ffields@KITT Week_11]$ ./ErrorCount.sh raw.g5mac3dp3.recode.vcf
This script counts the number of potential genotyping errors due to low read depth
It report a low range, based on a 50% binomial probability of observing the second allele in a heterozygote and a high range based on a 25% probability.
Potential genotyping errors from genotypes from only 1 read range from 0.0 to 0.0
Potential genotyping errors from genotypes from only 2 reads range from 0.0 to 0.0
Potential genotyping errors from genotypes from only 3 reads range from 46.125 to 154.98
Potential genotyping errors from genotypes from only 4 reads range from 21.875 to 110.6
Potential genotyping errors from genotypes from only 5 reads range from 13.96875 to 105
80 number of individuals and 1922 equals 153760 total genotypes
Total genotypes not counting missing data 153749
Total potential error rate is between 0.0005331335488360899 and 0.0024102920994608095
SCORCHED EARTH SCENARIO
WHAT IF ALL LOW DEPTH HOMOZYGOTE GENOTYPES ARE ERRORS?????
The total SCORCHED EARTH error rate is 0.0075837891628563435.
```

getting rid of individuals that were poorly sequenced

	vcftools --vcf raw.g5mac3dp3.recode.vcf --missing-indv

Examine output

	cat out.imiss
Data had very low percentages of missing data.

Because the data had 0.01% or lower of missing data we can eithe skip the step of creating a list of idvivuals with a certain % of missing data to remove of remove indivuals with less than 1% of missing data. I choose not to go through with this step.

Filter by mean depth of genotypes applying a call rate of 95%

	vcftools --vcf raw.g5mac3dp3.recode.vcf --max-missing 0.95 --maf 0.05 --recode --recode-INFO-all --out DP3g95maf05 --min-meanDP 20

```
###End of Output###
After filtering, kept 80 out of 80 Individuals
Outputting VCF file...
After filtering, kept 1153 out of a possible 1922 Sites
```

Next filter by a population specific call rate

	cat popmap #view population

Creating 2 list for each population, using VCFtools to estimat missing data and generating files 1.lmiss and 2.Lmiss

	mawk '$2 == "PopA"' popmap > 1.keep && mawk '$2 == "PopB"' popmap > 2.keep && mawk '$2 == "PopC"' popmap > 3.keep && mawk '$2 == "PopD"' popmap > 4.keep
	vcftools --vcf DP3g95maf05.recode.vcf --keep 1.keep --missing-site --out 1
	vcftools --vcf DP3g95maf05.recode.vcf --keep 2.keep --missing-site --out 2
	vcftools --vcf DP3g95maf05.recode.vcf --keep 3.keep --missing-site --out 3
	vcftools --vcf DP3g95maf05.recode.vcf --keep 4.keep --missing-site --out 4

Combining all lmiss files and making a list of loci about the threshold of 10% missing data to remove

	cat 1.lmiss 2.lmiss 3.lmiss 4.lmiss | mawk '!/CHR/' | mawk '$6 > 0.1' | cut -f1,2 >> missingdata

Removing any of the loci that only had two populations so our overall filter caught all of these

	vcftools --vcf DP3g95maf05.recode.vcf --exclude-positions missingdata --recode --recode-INFO-all --out DP3g95p5maf05

	mawk '/#/' DP3g95maf05.recode.vcf

filters out loci with an allele balance below 0.25 and above 0.75

	vcffilter -s -f "AB > 0.25 & AB < 0.75 | AB < 0.01" DP3g95p5maf05.recode.vcf > DP3g95p5maf05.fil1.vcf

Shows the amount of loci in the vcf file 

	mawk '!/#/' DP3g95p5maf05.recode.vcf | wc -l
	###Output###
	1153

	mawk '!/#/' DP3g95p5maf05.fil1.vcf | wc -l
	###Output###
	1147

Filtering out reads from both strands
	
	vcffilter -f "SAF / SAR > 100 & SRF / SRR > 100 | SAR / SAF > 100 & SRR / SRF > 100" -s DP3g95p5maf05.fil1.vcf > DP3g95p5maf05.fil2.vcf

The # of loci in the file now

	mawk '!/#/' DP3g95p5maf05.fil2.vcf | wc -l
	#Output
	1147

ratio of Looks at mapping qualities between reference and alternate alleles

	vcffilter -f "MQM / MQMR > 0.9 & MQM / MQMR < 1.05" DP3g95p5maf05.fil2.vcf > DP3g95p5maf05.fil3.vcf

Looks at the discrepancy  paired reads supporting reference or alternate alleles.
	
	vcffilter -f "PAIRED > 0.05 & PAIREDR > 0.05 & PAIREDR / PAIRED < 1.75 & PAIREDR / PAIRED > 0.25 | PAIRED < 0.05 & PAIREDR < 0.05" -s DP3g95p5maf05.fil3.vcf > DP3g95p5maf05.fil4.vcf

Removing any locus that has a quality score below 1/4 of the depth.

	vcffilter -f "QUAL / DP > 0.25" DP3g95p5maf05.fil4.vcf > DP3g95p5maf05.fil5.vcf

The # of loci in the file now

	mawk '!/#/' DP3g95p5maf05.fil5.vcf | wc -l
	#Output
	1145


Creates a list of the depth of each locus

	cut -f8 DP3g95p5maf05.fil5.vcf | grep -oe "DP=[0-9]*" | sed -s 's/DP=//g' > DP3g95p5maf05.fil5.DEPTH

Creates a list of quality scores.

	mawk '!/#/' DP3g95p5maf05.fil5.vcf | cut -f1,2,6 > DP3g95p5maf05.fil5.vcf.loci.qual

Calculates the mean depth

	mawk '{ sum += $1; n++ } END { if (n > 0) print sum / n; }' DP3g95p5maf05.fil5.DEPTH
	#output
	4705.66

Calculate the mean plus 3X the square of the mean

	python2.7 -c "print int(4705.66+3*(4705.66**0.5))"
	#output
	4911

Paste the depth and quality files together and find the loci above the cutoff that do not have quality scores 2 times the depth

	paste DP3g95p5maf05.fil5.vcf.loci.qual DP3g95p5maf05.fil5.DEPTH | mawk -v x=4911 '$4 > x' | mawk '$3 < 2 * $4' > DP3g95p5maf05.fil5.lowQDloci

Removing those sites and recalculate the depth across loci with VCFtools

	vcftools --vcf DP3g95p5maf05.fil5.vcf --site-depth --exclude-positions DP3g95p5maf05.fil5.lowQDloci --out DP3g95p5maf05.fil5
```
###End of Output###
After filtering, kept 80 out of 80 Individuals
Outputting Depth for Each Site
After filtering, kept 1099 out of a possible 1145 Sites
```
Cuting the VCFtools output to only depth scores

	cut -f3 DP3g95p5maf05.fil5.ldepth > DP3g95p5maf05.fil5.site.depth

Calculates the average depth by dividing the above file by the number of individuals 80

	mawk '!/D/' DP3g95p5maf05.fil5.site.depth | mawk -v x=80 '{print $1/x}' > meandepthpersite

Plot Histogram 

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

	
                                              Histogram of mean depth per site
     140 +----------------------------------------------------------------------------------------------------------+
         |   +   +  +   +   +   +   +   +  +  **   +   +   +   +  +   +   +   +   +  +   +   +   +   +   +  +   +   |
         |                                    **          'meandepthpersite' using (bin($1,binwidth)):(1.0) ******* |
     120 |-+                                  **                                                                  +-|
         |                                  *****                                                                   |
         |                                  *****                                                                   |
         |                                  *****                                                                   |
     100 |-+                                *****                                                                 +-|
         |                                  *****                                                                   |
         |                                  ******                                                                  |
      80 |-+                               *******                                                                +-|
         |                                 *******                                                                  |
         |                                 *******                                                                  |
      60 |-+                               *******                                                                +-|
         |                                 ********                                                                 |
         |                                 ********                                                                 |
      40 |-+                               ********                                                               +-|
         |                                 ********                                                                 |
         |                               ***********                                                                |
         |                               *************                                                              |
      20 |-+                            **************                                                            +-|
         |                              **************                                                              |
         |   +   +  +   +   +   +   +  *****************   +   +  +   +   +   +   +  +   +   +   +   +   +  +   +   |
       0 +----------------------------------------------------------------------------------------------------------+
         10  15  20 25  30  35  40  45  50 55  60  65  70  75  80 85  90  95 100 10 110 115 120 125 130 13 140 145 150
                                                         Mean Depth

Combining both filters to produce another VCF file. I'll keep the mean cut off but I thats realy not necessary

	vcftools --vcf  DP3g95p5maf05.fil5.vcf --recode-INFO-all --out DP3g95p5maf05.FIL --max-meanDP 102.5 --exclude-positions DP3g95p5maf05.fil5.lowQDloci --recode

	###End of Output###
	After filtering, kept 80 out of 80 Individuals
	Outputting VCF file...
	After filtering, kept 1099 out of a possible 1145 Sites


Appling HWE filter
converting our variant calls to SNPs first 
	
	vcfallelicprimitives DP3g95p5maf05.FIL.recode.vcf --keep-info --keep-geno > DP3g95p5maf05.prim.vcf

Feeding the VCF file into VCFtools to remove indels.

	vcftools --vcf DP3g95p5maf05.prim.vcf --remove-indels --recode --recode-INFO-all --out SNP.DP3g95p5maf05

	###End of output###
	After filtering, kept 80 out of 80 Individuals
	Outputting VCF file...
	After filtering, kept 935 out of a possible 1165 Sites

Uploading the HWE script

	curl -L -O https://github.com/jpuritz/dDocent/raw/master/scripts/filter_hwe_by_pop.pl
	chmod +x filter_hwe_by_pop.pl
	./filter_hwe_by_pop.pl

Applying the HWE filter 


	perl filter_hwe_by_pop.pl -v SNP.DP3g95p5maf05.recode.vcf -p popmap -o SNP.DP3g95p5maf05.HWE -h 0.01
	
	###Output###
	Processing population: PopA (20 inds)
	Processing population: PopB (20 inds)
	Processing population: PopC (20 inds)
	Processing population: PopD (20 inds)
	Outputting results of HWE test for filtered loci to 'filtered.hwe'
	Kept 933 of a possible 935 loci (filtered 2 loci)

	Final filter shows they are 933 SNPs
	mawk '!/#/' SNP.DP3g95p5maf05.HWE.filtered.vcf | wc -l

