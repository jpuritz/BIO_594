---
layout: post
title: Bio 594 Problem Set 1
categories:
tags: 
---

I collaborated with Caitlin on this problem set 

1. Let's imagine a 5 bp section of a genome, and that there is a SNP (A/G) in basepair 3.  Assume that we are genotyping **one** heterozygous individual (50% chance of sequencing either allele).  Please calculate the probability for the following sequencing reads:
    
    **Set 1**
    
    ```
    AAATG
    AAATG
    AAATG
    ```

    0.5 probability of A or G 
    Use the product rule for the 3 occurances 
    = 0.5^3
    = 0.125

    **Set 2**

    ```
    AAATG
    AAATG
    AAATG
    AAATG
    AAATG
    ```
    0.5 probability of A or G for 5 occurances 
    = 0.5^5
    = 0.03125

    **Set 3**

    ```
    AAATG
    AAGTG
    AAATG
    AAATG
    AAATG
    ```
    = 0.5^5
    = 0.03125


2. Way back in old 1993, Spitze reported the following number of genotypes at the *PGI* allozyme locus in the *Daphnia* population in Nothing Pond:

|Genotype|Count|
|--------|-----|
|*SS*    | 11|
|*SS-*   |55|
|*S-S-*  |61|

    A. What are the observed genotype and allele frequencies?
        Genotype frequency = # genotype (SS) / # total indv
                        SS = 11/127
                           = 0.087
                       SS- = 55/127
                           = 0.433
                      S-S- = 61/127
                           = 0.480
        Allele frequency = 
                       p = S
                       p = (2(# indv homozygous p) + # heterozygotes)/ 2(total # indiv)
                         = 2(11) + 55 / 2(127)
                         = 0.303
                       q = S-
                       q = 2(# indv homozygous q) + # heterozygotes/ 2(total # indiv)
                         = 2(61) + 55/ 2(127)
                         = 0.697
                         
    B. Given the observed allele frequencies, what are the genotypic frequencies expected under Hardy-Weinberg?  Using a chi-square test, how well do the observed genotype frequences agree with the HWE expecations?
        expected genotypic freq p = p^2 * #indv
                                  = 0.303^2 * 127
                                  = 11.66
                                q = q^2 * #indv
                                  = 0.697^ * 127
                                  = 61.698
                               pq = 2pq * 127
                                  = 2(0.303)(0.697) * 127
                                  = 53.643
        Chi Squared = (observed - expected)^2 / expected
                    = ((11 - 11.66)^2 / 11.66 ) + ((61-61.698)^2 / 61.698) + ((55-53.643)^2/53.643)
                    = 0.037 + 0.008 + 0.034
                    = 0.079

                    0.079 < 3.841 the observed freq agree with HW expectations

    C. What is the observed heterozygosity in this population and what is the expected heterozygosity?
        Expected heterozygosity = 2pq
                                = 53.643
        observed heterozygosity = 55

3.  Let's imagine another small population with the following genotype counts at a single SNP:

    |Genotype|Count|
    |--------|-----|
    |A/A     |0|
    |A/G     |10|
    |GG      |0|
        
    A. What are the observed genotype and allele frequencies?
        genotype freq = # genotype / # total indv
                  A/A = 0/10
                      = 0
                  A/G = 10/10
                      = 1
                  G/G = 0/10
                      = 0
        allele freq = p^2 + 2pq + q^2
                  p = (2(# indv homozygous p) + # heterozygotes)/ 2(total # indiv)
                  p = A
                    = 2(0) + 10 / 2(10)
                    = 0.5
                  q = G
                    = 2(0) + 10 / 2(10)
                    = 0.5 
    B. Given the observed allele frequencies, what are the genotypic frequencies expected under Hardy-Weinberg?  Using a chi-square test, how well do the observed genotype frequences agree with the HWE expecations?
        expected genotypic freq p = p^2 * #indv
                                  = 0.5^2 * 10
                                  = 2.5
                                q = q^2 * #indv
                                  = 0.5^2 * 10
                                  = 2.5
                               pq = 2pq * 10
                                  = 2(0.5)(0.5) * 10
                                  = 2.5
        Chi Squared = (observed - expected)^2 / expected
                    = (0-2.5)^2 / 2.5 + (10-2.5)^2/ 2.5 + (0-2.5)^2/2.5
                    = 27.5 
                    27.5 > 3.84 so the observed freq are not under HW equilibrium 

    C. Simulate one generation of random mating (you don't need to code this simulation; it can be by hand):
        * Pair off the ten indivduals into mating pairs
        * Randomly pick two expected offspring genotypes per pair (10 offspring genotypes)
        * Create a new genotype table from the offsrping only (should only be 10 genotypes)
        * Repeat subqestions A and B on the new genotype table

        New genotype table
        | Genotype | Counts |
        |----------|--------|
        | AG       | 4      | 
        | AA       | 4      |
        | GG       | 2      |
    
        genotype freq = # genotype / # total indv
                  A/A = 4/10
                      = 0.4
                  A/G = 4/10
                      = 0.4
                  G/G = 2/10
                      = 0.2
        allele freq = p^2 + 2pq + q^2
                  p = (2(# indv homozygous p) + # heterozygotes)/ 2(total # indiv)
                  p = A
                    = 2(4) + 4 / 2(10)
                    = 0.6
                  q = G
                    = 2(2) + 4 / 2(10)
                    = 0.4            
                    
        expected genotypic freq p = p^2 * #indv
                                  = 0.6^2 * 10
                                  = 3.6
                                q = q^2 * #indv
                                  = 0.4^2 * 10
                                  = 1.6
                               pq = 2pq * 127
                                  = 2(0.6)(0.4) * 10
                                  = 4.8
        Chi Squared = (observed - expected)^2 / expected
                    = ((4-3.6)^2 / 3.6) + ((2-1.6)^2 / 1.6) + ((4-4.8)^2/4.8)
                    = 0.044 + 0.1 + 0.133
                    = 0.277

        0.277 < 3.841 the observed freq agree with HW expectations

4.  Take a look at Gel C below:
    Gel C is the banding pattern from two AFLP markers (the upper and lower sets of bands).
        A. Estimate the frequency (q) of the null allele of each of the two AFLP markers assuming HWE.
            q = null allele 
            p^2 + 2pq + q^2 = 1
            q = # hom / 2(#hom + #het)

            A. = 88 + 32 / 2(130 + 120) 
               = 0.24
            B. = 109 + 52 / 2(89 + 161)
               = 0.322
            C. = 6 + 101 + 14 / 2(39 + 121)
               = 0.378
            
        B. Estimate the percentage of *band-present* individuals (not the overall frequencies) that are heterozygous at each of the two markers.  What biological principle does the difference between these two percentages illustrate?
            #heterozygotes / total 
            A. = 130/250
               = 0.52
               = 52%
            B. = 89/500
               = 0.356
               = 35.6%
            C. = 39/160
               = 0.244
               = 24.4%
            I don't think I understand the last part of the question. My first though is that these populations are likely not in HW equilibrium because of the differences in the percentage of heterozygotes in the populations.
