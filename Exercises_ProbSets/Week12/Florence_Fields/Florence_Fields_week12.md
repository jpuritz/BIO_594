## Part 1

Copied `realdata` and `simulated` from the directory, `/home/BIO594/Exercises/Week_12` to my folder

    mkdir week12
    cp -r /home/BIO594/Exercises/Week_12/realdata/ ../ffields/week12/ 
    cp -r /home/BIO594/Exercises/Week_12/simulated/ ../ffields/week12/ 

Create ddocent environment

    mamba create -n week12 ddocent
    mamba activate week12


### Simulated data
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
### Outlier detection programs

PCAdapt (done in R)

Outflank (done in R)


