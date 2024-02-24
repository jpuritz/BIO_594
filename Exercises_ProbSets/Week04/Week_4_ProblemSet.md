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

    **Set 2**

    ```
    AAATG
    AAATG
    AAATG
    AAATG
    AAATG
    ```

    **Set 3**

    ```
    AAATG
    AAGTG
    AAATG
    AAATG
    AAATG
    ```

2. Way back in old 1993, Spitze reported the following number of genotypes at the *PGI* allozyme locus in the *Daphnia* population in Nothing Pond:

|Genotype|Count|
|--------|-----|
|*SS*| 11|
|*SS-*|55|
|*S-S-*|61|

    A. What are the observed genotype and allele frequencies?
    B. Given the observed allele frequencies, what are the genotypic frequencies expected under Hardy-Weinberg?  Using a chi-square test, how well do the observed genotype frequences agree with the HWE expecations?
    C. What is the observed heterozygosity in this population and what is the expected heterozygosity?

3.  Let's imagine another small population with the following genotype counts at a single SNP:

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

4.  Take a look at Gel C below:

![img](./img/February%209%2C%202023/IMG_0524.jpeg)

Gel C is the banding pattern from two AFLP markers (the upper and lower sets of bands).
These are presence/absence markers.  So, there is a band or a null allele.

You could also read this as a table:

| Individuals | Genotype Uper Marker | Genotype Lower Marker |
|-------------|----------------------|------------------------|
| 6| Absent | Present |
|101 | Present | Absent| 
| 39 | Present | Present|
|14 | Absent | Absent| 
    
    A. Estimate the frequency (q) of the null allele of each of the two AFLP markers assuming HWE.
    
    B. Estimate the percentage of *band-present* individuals (not the overall frequencies) that are heterozygous at each of the two markers.  What biological principle does the difference between these two percentages illustrate?