WD_week11_exercise1.md

Copy files to my folder 
```{bash}
$ cp -R Week_11/ ../../wdunster/
```
Take a look at the data 
```{bash}
$ ls | grep "F" | wc -l 
80 

ls Week_11
#We have a reference that the data will be run against in reference.fasta
#There is also already a TotalRawSNPs.vcf but I still think we are suppossed to run dDocent as that is SNP calling
```
SNP fiiltering? 
Filter the variants -- kept if genotyped in 50% of idv, min qual score 30, minor allele count 3 
```{bash}
$ vcftools --gzvcf TotalRawSNPs.vcf --max-missing 0.5 --mac 3 --minQ 30 --recode --recode-INFO-all --out raw.g5mac3
After filtering, kept 1962 out of a possible 3284 Sites
```
Filtering individual < 3 reads 
```{bash}
$ vcftools --vcf raw.g5mac3.recode.vcf --minDP 3 --recode --recode-INFO-all --out raw.g5mac3dp3 
After filtering, kept 1962 out of a possible 1962 Sites
```

```{bash}
mamba create -n Week11 ddocent
source activate Week11
```

```{bash}
$ vcftools --vcf raw.g5mac3dp3.recode.vcf --missing-indv #create file for missing data
$ cat out.imiss

```
This data had almost no missing data

Create a list of indv with > 50% missing data
```{bash}
mawk '$5 > 0.5' out.imiss | cut -f1 > lowDP.indv
```

List and remove above indv
```{bash}
move lowDP.indv --recode --recode-INFO-all --out raw.g5mac3dplm
```

Filter by mean depth -- genotype call rate 95%
```{bash}
vcftools --vcf raw.g5mac3dplm.recode.vcf --max-missing 0.95 --maf 0.05 --recode --recode-INFO-all --out DP3g95maf05 --min-meanDP 20
```

Now we need to filter by mean depth for each locality 
```{bash}
cat popmap #view population map 

#create a list of just indv for each population
mawk '$2 == "PopA"' popmap > 1.keep && mawk '$2 == "PopB"' popmap > 2.keep && mawk '$2 == "PopC"' popmap > 3.keep && mawk '$2 == "PopD"' popmap > 4.keep  

#Estimate missing data for each site 
vcftools --vcf DP3g95maf05.recode.vcf --keep 1.keep --missing-site --out 1
vcftools --vcf DP3g95maf05.recode.vcf --keep 2.keep --missing-site --out 2
vcftools --vcf DP3g95maf05.recode.vcf --keep 3.keep --missing-site --out 3
vcftools --vcf DP3g95maf05.recode.vcf --keep 4.keep --missing-site --out 4

#Combine lists of missing data to make a badloci sheet 
cat 1.lmiss 2.lmiss 3.lmiss 4.lmiss | mawk '!/CHR/' | mawk '$6 > 0.1' | cut -f1,2 >> badloci

#Filter out indv from each pop using VCFtools 
vcftools --vcf DP3g95maf05.recode.vcf --exclude-positions badloci --recode --recode-INFO-all --out DP3g95p5maf05

#filter for allele balance between 0.25-0.75 
vcffilter -s -f "AB > 0.25 & AB < 0.75 | AB < 0.01" DP3g95p5maf05.recode.vcf > DP3g95p5maf05.fil1.vcf

#See how many loci we have now = 1155
mawk '!/#/' DP3g95p5maf05.fil1.vcf | wc -l 

#Filter out sites with reads from both strands 
vcffilter -f "SAF / SAR > 100 & SRF / SRR > 100 | SAR / SAF > 100 & SRR / SRF > 100" -s DP3g95p5maf05.fil1.vcf > DP3g95p5maf05.fil2.vcf

#access mapping quality ratio between reference and alternative alleles 
vcffilter -f "MQM / MQMR > 0.9 & MQM / MQMR < 1.05" DP3g95p5maf05.fil2.vcf > DP3g95p5maf05.fil3.vcf

vcffilter -f "PAIRED > 0.05 & PAIREDR > 0.05 & PAIREDR / PAIRED < 1.75 & PAIREDR / PAIRED > 0.25 | PAIRED < 0.05 & PAIREDR < 0.05" -s DP3g95p5maf05.fil3.vcf > DP3g95p5maf05.fil4.vcf

mawk '!/#/' DP3g95p5maf05.fil4.vcf | wc -l

vcffilter -f "QUAL / DP > 0.25" DP3g95p5maf05.fil4.vcf > DP3g95p5maf05.fil5.vcf

cut -f8 DP3g95p5maf05.fil5.vcf | grep -oe "DP=[0-9]*" | sed -s 's/DP=//g' > DP3g95p5maf05.fil5.DEPTH

mawk '!/#/' DP3g95p5maf05.fil5.vcf | cut -f1,2,6 > DP3g95p5maf05.fil5.vcf.loci.qual

mawk '{ sum += $1; n++ } END { if (n > 0) print sum / n; }' DP3g95p5maf05.fil5.DEPTH
4705.11

python -c "print int(4705.11+3*(4705.11**0.5))"
4910

paste DP3g95p5maf05.fil5.vcf.loci.qual DP3g95p5maf05.fil5.DEPTH | mawk -v x=4910 '$4 > x' | mawk '$3 < 2 * $4' > DP3g95p5maf05.fil5.lowQDloci

vcftools --vcf DP3g95p5maf05.fil5.vcf --site-depth --exclude-positions DP3g95p5maf05.fil5.lowQDloci --out DP3g95p5maf05.fil5

vcfallelicprimitives DP3g95p5maf05.fil5.vcf --keep-info --keep-geno > DP3g95p5maf05.prim.vcf

vcftools --vcf DP3g95p5maf05.prim.vcf --remove-indels --recode --recode-INFO-all --out SNP.DP3g95p5maf05

```