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

1. Let's imagine a 5 bp section of a genome, and that there is a SNP (A/G) in basepair 3.  Assume that we are genotyping **one** heterozygous individual (50% chance of sequencing either allele).  Please calculate the probability for the following sequencing reads:
    
    **Set 1**
    
    ```
    AAATG
    AAATG
    AAATG
    ```
    ```
    My Answer:
    0.125 
    ```

    **Set 2**

    ```
    AAATG
    AAATG
    AAATG
    AAATG
    AAATG
    ```
    ```
    My Answer:
    0.03125 
    ```
    **Set 3**

    ```
    AAATG
    AAGTG
    AAATG
    AAATG
    AAATG
    ```
    ```
    My Answer:
    0.03125 
    ```
2. Way back in old 1993, Spitze reported the following number of genotypes at the *PGI* allozyme locus in the *Daphnia* population in Nothing Pond:

|Genotype|Count|
|--------|-----|
|*SS* (homozygous dominant) | 11|
|*SS-* (heterozygous) |55|
|*S-S-* (homozygous recessive) |61|

    A. What are the observed genotype and allele frequencies?
    
    Allele frequency (Observed): 
   
    p=S
    
    p=2(# of individuals homozygous for p)+# of heterozygotes/2(total number of individuals)
    p = 2(11)+55/254 = 22+55/254 = 
    
     *0.303149*
      
    q=S-
    
    q=2(# of individuals homozygous for q)+# of heterozygotes/2(total number of individuals) 
    q=2(61)+55/254 = 122+55/254 = 

     *0.69695*
    
    Genotype frequency (Observed): 
    
    SS = 11/127 = *0.0866*
    SS- = 55/127 = *0.433*
    S-S- = 61/127 = *0.480*
    
      
    B. Given the observed allele frequencies, what are the genotypic frequencies expected under Hardy-Weinberg?  Using a chi-square test, how well do the observed genotype frequences agree with the HWE expecations?
    
    Expected genotype frequency of SS (homozygous dominant):
    = (p)^2(N) 
    where... 
    p = allele frequency of the p (major) allele 
    N = total number of individuals in the sample 
    
    (0.303)^2 x 127 = 
          *11.66 homozygous dominant individuals expected in a sample of 127 individuals if that population is in HW proportions*
    
    Expected genotype frequency of SS- (heterozygous): 
    = 2(p)(q)(N) 
    where...
    p = allele frequency of the p (major) allele 
    q = allele frequency of the q (minor) allele
    N = total number of individuals in the sample 
    
    2(.303)(0.697) x 127 = 
        *53.64 heterozygous individuals expected in a sample of 127 individuals if that population is in HW proportions*
        
    Expected genotype frequency of S-S- (homozygous recessive):
    = (q)^2(N) 
    where... 
    q = allele frequency of the q (minor) allele 
    N = total number of individuals in the sample 
    
    (0.697)^2 x 127 = 
          *61.7 homozygous recessive individuals expected in a sample of 127 individuals if that population is in HW proportions*
          
    x^2 = (summation) (observed-expected)^2/expected 
        = ((11.66-11)^2/11.66) + ((55-53.64)^2/53.64) + ((61.7-61)^2/61.7) = 0.03736 + 0.03448 + 0.007941 
        = *0.07978* 
        
        degrees of freedom (given 2 alleles and 3 genotypes) = 1 
        significance level = 0.05 
        
        x^2 at 1 dof at a significance level of 0.05 = 3.841
        3.841 > 0.07978; therefore, the observed proportions of genotypes within the sample agree with HW proportions (fail to reject the null hypothesis)
        
    C. What is the observed heterozygosity in this population and what is the expected heterozygosity?
    
    The observed heterozygosity in this population is *0.433* and the expected heterozygosity in this population is *0.422*

3.  Let's imagine another small population with the following genotype counts at a single SNP:

|Genotype|Count|
|--------|-----|
|A/A|0|
|A/G|10|
|GG|0|

    A. What are the observed genotype and allele frequencies?
    
    Allele frequency (Observed): 
   
    p=A
    
    p=2(# of individuals homozygous for p)+# of heterozygotes/2(total number of individuals)
    p = 2(0)+10/2(10) = (0+10)/20 = 0.5
    
     *0.5*
      
    q=G
    
    q=2(# of individuals homozygous for q)+# of heterozygotes/2(total number of individuals) 
    q = 2(0)+10/2(10) = (0+10)/20 = 0.5

     *0.5*
    
    Genotype frequency (Observed): 
    
    A/A = 0/10 = *0.0*
    A/G = 10/10 = *1.0*
    G/G = 0/10 = *0.0*
    
    B. Given the observed allele frequencies, what are the genotypic frequencies expected under Hardy-Weinberg?  Using a chi-square test, how well do the observed genotype frequences agree with the HWE expecations?
    
    Expected genotypic frequency of the A/A genotype: 
     = p^2(N)
     = 0.5^2(10)
     = 2.5
     *2.5 individuals within this population will be expected to have a A/A genotype*
     
     Expected genotypic frequency of the A/G genotype: 
     = 2(p)(q)(N)
     = 2(0.5)(0.5)(10)
     = 5 
     *5 individuals within this population will be expected to have a A/G genotype* 
     
     Expected genotypic frequency of the G/G genotype: 
     = (q)^2(N)
     = (0.5)^2(10)
     = 2.5 
     *2.5 individuals within this population will be expected to have a G/G genotype*
     
     x^2 = (summation of) (observed-expected)^2/expected 
         = ((0-2.5)^2/2.5) + ((10-5)^2/5) + ((0-2.5)^2/2.5) 
         = 2.5 + 5 + 2.5 
         = 10 
    
     degrees of freedom (given 2 alleles and 3 genotypes) = 1 
        significance level = 0.05 
        
        x^2 at 1 dof at a significance level of 0.05 = 3.841
       
        therefore, because 10>3.841, we can conclude this population is not in HW proportions, and therefore we must reject the null hypothesis. 
      
    C. Simulate one generation of random mating (you don't need to code this simulation; it can be by hand):
        * Pair off the ten indivduals into mating pairs
        * Randomly pick two expected offspring genotypes per pair (10 offspring genotypes)
        * Create a new genotype table from the offspring only (should only be 10 genotypes)
        * Repeat subquestions A and B on the new genotype table
        |Genotype|Count|
        |--------|-----|
        |A/A|3|
        |A/G|6|
        |G/G|1|
        
        A. Observed Allele and Genotype Frequencies 
        
        Observed allele frequencies: 
        p = A
        A frequency = 2(3)+6/2(10) 
                    = 6+6/20
                    = 12/20
                    = 0.6 
                    
        q = G 
        G frequency = 2(1)+6/2(10)
                    = 2+6/20
                    = 8/20
                    = 0.4
                    
         Observed genotype frequencies: 
         A/A genotype = 3/10 = 0.3
         A/G genotype = 6/10 = 0.6
         G/G genotype = 1/10 = 0.1 
         
        B. Expected Genotype frequencies & agreement with HW? 
        A/A = p^2(N)
            = (0.6)^2(10)
            = 3.6 
            *3.6 individuals with the A/A genotype are expected in this population of 10 individuals* 
            
        A/G = 2(p)(q)(N)
            = 2(0.6)(0.4)(10)
            = 4.8 
            *4.8 individuals with the A/G genotype are expected in this population of 10 individuals* 
            
        G/G = q^2(N)
            = (0.4)^2(10)
            = 1.6 
            *1.6 individuals with the G/G genotype are expected in this population of 10 individuals*
            
            
        x^2 = summation (expected-observed)^2/expected
            = ((3.6-3.0)^2/3.6) + ((4.8-4.0)^2/4.8) + ((1.6-1.0)^2/1.6) 
            = (0.1) + (0.13333) + (0.225) 
            = 0.45833
            
       degrees of freedom (given 2 alleles and 3 genotypes) = 1 
        significance level = 0.05 
        
        x^2 at 1 dof at a significance level of 0.05 = 3.841
        
        therefore, because 0.45833<3.841, this population is in HW proportions and therefore we can refuse to reject the null hypothesis. 

4.  Take a look at Gel C below:

![img](./img/February%209%2C%202023/IMG_0524.jpeg)

Gel C is the banding pattern from two AFLP markers (the upper and lower sets of bands).
    
    A. Estimate the frequency (q) of the null allele of each of the two AFLP markers assuming HWE. 
    I'm guessing that the group of 14 individuals are homozygous for the null allele since there is no signal at all on the gel and I am also just going to assume that the absence of the signal for the 6 and 101 group also means that those individuals are carriers of the null allele, but I don't fully understand but anyways here is my best guess: 
    q = 2(14) + 6 + 101 / 2(6+101+39+14)
      = 135/320 
      = 0.422 
    
    B. Estimate the percentage of *band-present* individuals (not the overall frequencies) that are heterozygous at each of the two markers.  What biological principle does the difference between these two percentages illustrate?
    
    I also don't understand this question that well, but given I can see a single band (meaning heterozygous) for (6+101) individuals out of a total of (6+101+39+14) individuals I will say (107/160) 66.875% of band present individuals are heterozygous at each of the two markers. 
    
    Also, I am guessing that the difference between these two percentages has to do with random assortment and some sort of linkage, most likely sex linkage, given that theoretically we would expect that the homozygous individuals (both bands or no bands) would have similar numbers and that the heterozygous individuals (either the bottom band or the top band) would also have similar proportions, but especially in the heterozygotes, we see vastly different proportions, suggesting that the group of individuals with the top band allele is probably linked to the sex determining locus of the X chromosome, given both genders will have the x chromosome, and the bottom band allele is probably more closely associated with the y chromosome (but I feel like i don't really know)
