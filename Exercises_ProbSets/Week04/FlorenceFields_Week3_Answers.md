# Problem Set 1
## Due 2/21/2024
### Instructions

* Please answer all questions using a Mardown or RMarkdown, showing all work.
* Please place your files in this same directory in the format of `YourName_Week4_Answers.md`
* Problem sets can be worked on collaboratively, but please note who you worked with in your answer document

Note, you can also use LATEX notation to format numbers and equations by putting them within `$$`

`$$  P_x = \frac{P}{x}$$`

becomes 

$$  P_x = \frac{P}{x}$$


See more information [here](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)

## Problems

## 1. Let's imagine a 5 bp section of a genome, and that there is a SNP (A/G) in basepair 3.  Assume that we are genotyping **one** heterozygous individual (50% chance of sequencing either allele).  Please calculate the probability for the following sequencing reads:
    
    **Set 1**
    
    ```
    AAATG
    AAATG
    AAATG
    ```
    - Calculating the probability of a binary event
    P = 0.5* 0.5* 0.5 = 0.125

        $$
        P = \frac{n!}{k!(n-k)!}*p^x*q^(n-k)
        P = \frac{3!}{3!(3-3)!}* \frac{1}{2}^3* \frac{1}{2}^0
        P = \frac{6}{6*1}* \frac{1}{8}* \frac{1}{1}
        P = 1* \frac{1}{8}* 1
        P = 0.125 
        $$
    

     **Set 2**

      ```
        AAATG
        AAATG
        AAATG
        AAATG
        AAATG
      ```
  
   -  P = 0.5* 0.5* 0.5* 0.5* 0.5 = 0.03125
        $$
        P = \frac{n!}{k!(n-k)!}*p^x*q^(n-k)
        P = \frac{5!}{5!(5-5)!}* \frac{1}{2}^5* \frac{1}{2}^0
        P = \frac{120}{120*1}* \frac{1}{32}* \frac{1}{1}
        P = 1* \frac{1}{32}* 1
        P = 0.03125
        $$
 

   **Set 3**

    ```
    AAATG
    AAGTG
    AAATG
    AAATG
    AAATG
    ```
    
    - In set 3 one of the 5 sequencing reads is AAGTG which means the number of times AAGTG can occur is 4 out of the 5 events
        P = 0.5* 0.5* 0.5* 0.5 = 0.15625
        $$
        P = \frac{n!}{k!(n-k)!}*p^x*q^(n-k)
        P = \frac{5!}{4!(5-4)!}* \frac{1}{2}^4* \frac{1}{2}^(5-4)
        P = \frac{120}{24*1}* \frac{1}{16}* \frac{1}{2}
        P = \frac{120}{768}
        P = 0.15625
        $$
    

## 2. Way back in old 1993, Spitze reported the following number of genotypes at the *PGI* allozyme locus in the *Daphnia* population in Nothing Pond:

|Genotype|Count|
|--------|-----|
|*SS*| 11|
|*SS-*|55|
|*S-S-*|61|

    A. What are the observed genotype and allele frequencies?
    B. Given the observed allele frequencies, what are the genotypic frequencies expected under Hardy-Weinberg?  Using a chi-square test, how well do the observed genotype frequences agree with the HWE expecations?
    C. What is the observed heterozygosity in this population and what is the expected heterozygosity?


- #### A
    ##### **Observed genotype frequencies**

    Total- 11+55+61 = 127

    p = *SS* = 11/127 = 0.0866 
    pq = *SS-* = 55/127 = 0.433   
    q = *S-S-* = 61/127 = 0.480  

    ##### **Observed allele frequencies**
    $$p = \frac{(2*11) + 55}{2(127)} = 0.303$$
    q = 1-0.303 = 0.697 0r $$q = \frac{55+2(61)}{254} = 0.697$$

- #### B
    ##### **Expected genotypic frequencies expected under Hardy-Weinberg**
    
    (p + q)<sup> 2</sup> = p<sup> 2</sup> + 2pq + q<sup> 2</sup>
    

    p = *SS* = 0.303<sup> 2</sup> = 0.0918
    q = *S-S-* =  0.697<sup> 2</sup> = 0.4858
    pq = *SS-* = 2(0.303)(0.697) = 0.4858

 
    ##### **Expected genotype counts**
    p = *SS* = 0.303<sup> 2</sup>(127) = 11.66
    q = *S-S-* = 0.697<sup> 2</sup>(127) = 61.697
    pq *SS-* = 2(0.303)(0.697)(127) = 53.64

    ##### **Chi-square values**
    $$\frac{(11-11.66)^2}{11.66} + \frac{(55-53.64)^2}{53.64} + \frac{(61-61.697)^2}{61.697}$$
    0.0374 + 0.0345 + 0.00787 = 0.07977

    Number of alleles = 2
    Number of genotypes = 3
    Degrees of freedom = 3-2 = 1

    | Genotype | Observed | Expected | Chi-square |
|----------|----------|----------|------------|
| SS       |  11      | 11.66    | 0.0374      |
| SS-      |  55      | 53.64    | 0.0345      |
| S-S-     |  61      | 61.697   | 0.00787      |
| Total    |  127     | 126.997  | 0.07977      |

    Alpha is 0.05
    The calculated chi square of 0.07977 is less than the critical value for P < 3.84. 
    Showing that the population was in HW proportions. 
    The observed genotype frequences did agree with the HWE expecations

- #### C
    ##### **Observered Heterozygosity**
    pq = *SS-* = 55/127 = 0.433
    ##### **Expected Heterozygosity**
    He = 1 - (p<sup> 2</sup> + q<sup> 2</sup>)
    He = 1 - (0.303<sup> 2</sup> + 0.697<sup> 2</sup>)
    He = 1 - 0.578
    He = 0.422


## 3.  Let's imagine another small population with the following genotype counts at a single SNP:

|Genotype|Count|
|--------|-----|
|A/A|0|
|A/G|10|
|GG|0|

    A. What are the observed genotype and allele frequencies?
    B. Given the observed allele frequencies, what are the genotypic frequencies expected under Hardy-Weinberg?  Using a chi-square test, how well do the observed genotype frequences agree with the HWE expecations?
    C. Simulate one generation of random mating (you don't need to code this simulation; it can be by hand):
        * Pair off the ten indivduals into mating pairs
        * Randomly pick two expected offspring genotypes per pair (10 offspring genotypes)
        * Create a new genotype table from the offsrping only (should only be 10 genotypes)
        * Repeat subqestions A and B on the new genotype table
- #### A
    ##### **Observed genotype frequencies**
    Total- 0+10+0 = 10

    p = *AA* = 0/10 = 0
    pq = *AG* = 10/10 = 1   
    q = *GG* = 0/10 = 0

    ##### **Observed allele frequencies**
    $$p = \frac{(2*0) + 10}{2(10)} = 0.5$$
    q = 1-0.5 = 0.5 0r $$q = \frac{10+2(0)}{2(10)} = 0.5$$

- #### B
    ##### **Expected genotypic frequencies expected under Hardy-Weinberg**
    (p + q)<sup> 2</sup> = p<sup> 2</sup> + 2pq + q<sup> 2</sup>
    p = *AA* = 0.5<sup> 2</sup> = 0.25
    q = *GG* =  0.5<sup> 2</sup> = 0.25
    pq = *AG* = 2(0.5)(0.5) = 0.5

    ##### **Expected genotype counts**
    p = *AA* = 0.5<sup> 2</sup> (10)= 2.5
    q = *GG* =  0.5<sup> 2</sup> (10)= 2.5
    pq *AG* = 2(0.5)(0.5) (10)= 5

     ##### **Chi-square values**
    $$\frac{(0-2.5)^2}{2.5} + \frac{(0-2.5)^2}{2.5} + \frac{(10-5)^2}{5}$$
    2.5 + 2.5 + 5 = 10

    Number of alleles = 2
    Number of genotypes = 3
    Degrees of freedom = 3-2 = 1

    | Genotype | Observed | Expected | Chi-square |
    |----------|----------|----------|------------|
    | AA       |  0       | 2.5      | 2.5        |
    | AG       |  10      | 10       | 5          |
    | GG       |  0       | 2.5      | 2.5        |
    | Total    |  10      | 10       | 10         |
    
    Alpha is 0.05
    The calculated chi square of 10 is more than the critical value for P > 3.84. 
    Showing that the population was not in HW proportions. 
    The observed genotype frequences did not agree with the HWE expecations

- #### C
```
Pairing off the 10 indivduals into mating pairs
```

   | Genotype | Count    |
    |----------|----------|
    | AA       |  3       | 
    | AG       |  6      | 
    | GG       |  1       | 
    | Total    |  10      | 
    
   ##### **Observed genotype frequencies**

   p = *AA* = 3/10 = 0.3
   pq = *AG* = 6/10 = 0.6   
   q = *GG* = 1/10 = 0.1

   ##### **Observed allele frequencies**
   $$p = \frac{(2*3) + 6}{2(10)} = 0.6$$
    q = 1-0.6 = 0.4 0r $$q = \frac{6+2(1)}{2(10)} = 0.4$$
    
   ##### **Expected genotypic frequencies expected under Hardy-Weinberg**
   (p + q)<sup> 2</sup> = p<sup> 2</sup> + 2pq + q<sup> 2</sup>
   p = *AA* = 0.6<sup> 2</sup> = 0.36
   q = *GG* =  0.4<sup> 2</sup> = 0.16
   pq = *AG* = 2(0.6)(0.4) = 0.48

   ##### **Expected genotype counts**
   p = *AA* = 0.6<sup> 2</sup> (10)= 3.6
   q = *GG* = 0.4<sup> 2</sup> (10)= 1.6
   pq *AG* = 2(0.6)(0.4) (10)= 4.8

   ##### **Chi-square values**
   $$\frac{(3-3.6)^2}{3.6} + \frac{(6-4.8)^2}{4.8} + \frac{(1-1.6)^2}{1.6}$$
    0.1 + 0.3 + 0.225 = 10

    Number of alleles = 2
    Number of genotypes = 3
    Degrees of freedom = 3-2 = 1

    | Genotype | Observed | Expected | Chi-square |
    |----------|----------|----------|------------|
    | AA       |  3       | 3.6      | 0.1        |
    | AG       |  6       | 4.8      | 0.3        |
    | GG       |  1       | 1.6      | 0.225      |
    | Total    |  10      | 10       | 0.625      |

   Alpha is 0.05
   The calculated chi square of 0.625 is less than the critical value for P < 3.84. 
    Showing that the population was within in HW proportions. 
    The observed genotype frequences did agree with the HWE expecations

## 4.  Take a look at Gel C below:

![img](./img/February%209%2C%202023/IMG_0524.jpeg)

Gel C is the banding pattern from two AFLP markers (the upper and lower sets of bands).
    
    A. Estimate the frequency (q) of the null allele of each of the two AFLP markers assuming HWE.
    
    B. Estimate the percentage of *band-present* individuals (not the overall frequencies) that are heterozygous at each of the two markers.  What biological principle does the difference between these two percentages illustrate?
- #### A
   Total number of indivuals with the null allele from gel C:  6 + 101 + 39+ 14 = 160
   Note: NA = no band (null)/lower band present, BN = upper band present/no band, AB = upper band present/lower band present, NN = no band/no band

   | Genotype  | Count    |
    |----------|----------|
    | NA       |  6       | 
    | BN       |  101     | 
    | AB       |39        |
    | NN       | 14       |
    | Total    |  160     | 

   ##### **Genotype frequency **
   NA = 6/160 = 0.0375
   BN = 101/160 = 0.63125
   AB = 39/160 = 0.24375
   NN = 14/160 = 0.0875

   ##### **allele frequency of q**
  $q = \frac{6+2(14)+101}{2(160)} = 0.422$

- #### B
   NA = 6/160 = 0.0375 = 37.5%
   BN = 101/160 = 63.13%
 I want to say these percentages show the presenence of genetic varition within the population but one percentage is low while the other is above the 50th percentile 

    

    