Jon’s code from class (Incomplete)
================

``` bash
mamba create -n week12 ddocent
mamba activate week12
```

``` bash
mkdir -p week12ds
cd week12ds
ln -s /home/BIO594/DATA/Week7/example/*.fq.gz .
```

``` bash
cd week12ds
dDocent
```

``` bash
cd week12ds
mkdir Filter
cd Filter
ln -s ../TotalRawSNPs.vcf
vcftools --vcf TotalRawSNPs.vcf --max-missing 0.5 --maf 0.001 --minQ 20 --recode --recode-INFO-all --out TRS
vcftools --vcf TRS.recode.vcf --minDP 5 --recode --recode-INFO-all --out TRSdp5
pop_missing_filter.sh TRSdp5.recode.vcf ../popmap 0.05 1 TRSdp5p05
dDocent_filters TRSdp5p05.recode.vcf TRSdp5p05
vcfallelicprimitives -k -g TRSdp5p05.FIL.recode.vcf | sed 's:\.|\.:\.\/\.:g' > TRSdp5p05F.prim
vcftools --vcf TRSdp5p05F.prim --recode --recode-INFO-all --remove-indels --out SNP.TRSdp5p05F
vcftools --vcf SNP.TRSdp5p05F.recode.vcf --maf 0.05 --recode --recode-INFO-all --out SNP.TRSdp5p05Fmaf05
```

``` bash
mamba install pgdspider
cp /home/BIO594/DATA/Week7/example/BSsnp.spid .
ln -s ../popmap .
PGDSpider2-cli -inputfile SNP.TRSdp5p05Fmaf05.recode.vcf -outputfile SNP.TRSdp5p05Fmaf05BS -spid BSsnp.spid 
BayeScan2.1_linux64bits SNP.TRSdp5p05Fmaf05BS -nbp 30 -thin 20
```

``` bash
cp /home/BIO594/DATA/Week7/example/plot_R.r .
```

``` r
source("~/week12ds/Filter/plot_R.r")
plot_bayescan("~/week12ds/Filter/SNP.TRSdp5p05Fmaf_fst.txt")
```

![](JonsCodeFromClass_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

    ## $outliers
    ## [1] 798 799 873 874 894
    ## 
    ## $nb_outliers
    ## [1] 5