## Part 1

Copied `realdata` and `simulated` from the directory, `/home/BIO594/Exercises/Week_12` to my folder

    mkdir week12
    cp -r /home/BIO594/Exercises/Week_12/realdata/ ../ffields/week12/ 
    cp -r /home/BIO594/Exercises/Week_12/simulated/ ../ffields/week12/ 

    curl -L -O https://bitbucket.org/tguenther/bayenv2_public/raw/2b2b7f20bb62fedaf5ea10b57e30bcb2807994b9/calc_bf.sh
    chmod +x calc_bf.sh

Create ddocent environment

    mamba create -n week12 ddocent
    mamba activate week12


# Simulated data
* Filtering SNPs
```
    vcftools --vcf TotalRawSNPs.vcf --max-missing 0.5 --maf 0.001 --minQ 20 --recode --recode-INFO-all --out TRS  ##fileting genotypes called below 50%
###Output
After filtering, kept 80 out of 80 Individuals
Outputting VCF file...
After filtering, kept 2993 out of a possible 3025 Sites
```
```
    vcftools --vcf TRS.recode.vcf --minDP 5 --recode --recode-INFO-all --out TRSdp5  ##filtering genotypes that have less than 5 reads
###Output
After filtering, kept 80 out of 80 Individuals
Outputting VCF file...
After filtering, kept 2993 out of a possible 2993 Sites
```
```
    pop_missing_filter.sh TRSdp5.recode.vcf ../popmap 0.05 1 TRSdp5p05
###Output 
After filtering, kept 80 out of 80 Individuals
Outputting VCF file...
After filtering, kept 2993 out of a possible 2993 Sites
```
```
    dDocent_filters TRSdp5p05.recode.vcf TRSdp5p05
###Output
Number of sites filtered based on allele balance at heterozygous loci, locus quality, and mapping quality / Depth
 417 of 2993

Are reads expected to overlap?  In other words, is fragment size less than 2X the read length?  Enter yes or no.
yes
Is this from a mixture of SE and PE libraries? Enter yes or no.
yes
Number of additional sites filtered based on properly paired status
 0 of 2576

Number of sites filtered based on high depth and lower than 2*DEPTH quality score
 219 of 2576




                                               Histogram of mean depth per site
      300 +---------------------------------------------------------------------------------------------------------+
          |   +    +    +     +    +     +    +    +     +    +    +     +    +     +    +    +     +    +     +    |
          |                                               'meandepthpersite' using (bin($1,binwidt***:(1.0) ******* |
          |                                                                                     *** *               |
      250 |-+                                                                                 *** * ***           +-|
          |                                                                                   * * * * *             |
          |                                                                                  ** * * * *             |
          |                                                                                  ** * * * *             |
      200 |-+                                                                                ** * * * **          +-|
          |                                                                                  ** * * * **            |
          |                                                                                **** * * * **            |
      150 |-+                                                                            *** ** * * * ****        +-|
          |                                                                              * * ** * * * ** *          |
          |                                                                              * * ** * * * ** *          |
          |                                                                              * * ** * * * ** *          |
      100 |-+                                                                            * * ** * * * ** *        +-|
          |                                                                              * * ** * * * ** ***        |
          |                                                                          *** * * ** * * * ** * *        |
          |                                                                          * *** * ** * * * ** * *        |
       50 |-+                                                                       ** * * * ** * * * ** * *      +-|
          |                                                                         ** * * * ** * * * ** * ***      |
          |                                                                     ****** * * * ** * * * ** * * ****   |
          |   +    +    +     +    +     +    +    +     +    +    +     +    *** * ** * * * ** * * * ** * * * **** |
        0 +---------------------------------------------------------------------------------------------------------+
              12   15   18    21   24    27   30   33    36   39   42    45   48    51   54   57    60   63    66   69
                                                          Mean Depth

If distrubtion looks normal, a 1.645 sigma cutoff (~90% of the data) would be 5257.49261
The 95% cutoff would be 63
Would you like to use a different maximum mean depth cutoff than 63, yes or no
yes
Please enter new cutoff
71
Number of sites filtered based on maximum mean depth
 0 of 2576

Number of sites filtered based on within locus depth mismatch
 5 of 2407

Total number of sites filtered
 591 of 2993

Remaining sites
 2402

Filtered VCF file is called TRSdp5p05.FIL.recode.vcf

Filter stats stored in TRSdp5p05.filterstats
```
```


    vcfallelicprimitives -k -g TRSdp5p05.FIL.recode.vcf | sed 's:\.|\.:\.\/\.:g' > TRSdp5p05F.prim.vcf

    vcftools --vcf TRSdp5p05F.prim.vcf --recode --recode-INFO-all --remove-indels --out SNP.TRSdp5p05F
###Output
After filtering, kept 80 out of 80 Individuals
Outputting VCF file...
After filtering, kept 2076 out of a possible 2574 Sites

    filter_hwe_by_pop.pl -v SNP.TRSdp5p05F.recode.vcf -p popmap -c 0.5 -out SNP.TRSdp5p05FHWE
###Output
Processing population: PopA (20 inds)
Processing population: PopB (20 inds)
Processing population: PopC (20 inds)
Processing population: PopD (20 inds)
Outputting results of HWE test for filtered loci to 'filtered.hwe'
Kept 2076 of a possible 2076 loci (filtered 0 loci)
```
```
    vcftools --vcf SNP.TRSdp5p05FHWE.recode.vcf --maf 0.05 --recode --recode-INFO-all --out SNP.TRSdp5p05Fmaf05
###Output
After filtering, kept 80 out of 80 Individuals
Outputting VCF file...
After filtering, kept 1008 out of a possible 2076 Sites
```
#### Outlier detection programs

PCAdapt (done in R as a markdown)
Outflank (done in R as a markdown)

Outliers files were merged. Next generate a VCF with only neutral SNPs

### VCF with only neutral SNPs

mawk '!/#/' SNP.DP3g98maf01_85INDoutFIL.NO2a.HWE.FIL.recode.vcf | cut -f1,2 > totalloci
NUM=(`cat totalloci | wc -l`)
paste <(seq 1 $NUM) totalloci > loci.plus.index
cat outliers.txt | parallel "grep -w ^{} loci.plus.index" | cut -f2,3> outlier.loci.txt

head outlier.loci.txt



# Real data
#### Outlier detection programs
* BayeScan
```
cp /home/BIO594/DATA/Week7/example/BSsnp.spid .
ln -s ../popmap .
mamba install pgdspider

PGDSpider2-cli -inputfile SNP.DP3g98maf01_85INDoutFIL.NO2a.HWE.FIL.recode.vcf -outputfile SNP.TRSdp5p05FBS -spid BSsnp.spid
```
```
BayeScan2.1_linux64bits SNP.TRSdp5p05FBS -nbp 30 -thin 20
```
```
cp /home/ffields/week12/realdata/plot_R.r .
```

``` ran in Rstudio
source("plot_R.r")
plot_bayescan("SNP.TRSdp5p05FH_fst.txt")
bs <-plot_bayescan("SNP.TRSdp5p05FH_fst.txt")
 bs$outliers

###Ouptput###
$outliers
integer(0)

$nb_outliers
[1] 0
```

* Run BayEnv
```
PGDSpider2-cli -inputfile SNP.DP3g98maf01_85INDoutFIL.NO2a.HWE.FIL.recode.vcf -outputfile SNP.TRSdp5p05FBayEnv.txt -spid SNPBayEnv.spid
```
```
WARN  22:05:19 - PGDSpider configuration file not found! Loading default configuration.
initialize convert process...
read input file...
read input file done.
write output file...
write output file done.
```
```
bayenv2 -i SNP.TRSdp5p05FBayEnv.txt -p 16 -k 100000 -r 63479 > matrix.out
```
```
tail -13 matrix.out | head -12 > matrix
```
```
cat environ
```
```
ln -s /usr/local/bin/bayenv2 .

calc_bf.sh SNP.TRSdp5p05FBayEnv.txt environ matrix 16 10000 2 #Recieves error
```
```
paste <(seq 1 923) <(cut -f2,3 bf_environ.environ ) > bayenv.out
cat <(echo -e "Locus\tBF1\tBF2") bayenv.out > bayenv.final
```
``` To be done in R
table_bay <- read.table("bayenv.final",header=TRUE)
plot(table_bay$BF1)

table_bay[which(table_bay$BF1 > 100),]
```
