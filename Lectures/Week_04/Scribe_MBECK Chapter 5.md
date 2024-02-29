Chapter 5: Random Mating Populations Hardy-Weinberg Principle

Caitlin Randall 

Genetic Basics/Laws:

Law of dominance

Law of segregation 

Law of independent Assortment

Allele Vs Genotype: 

Allele: a version of the same gene 

Genotype: The genetic constitution of an individual organism 

Two types of Models: 

1. Conceptual: represent complex reality
2. Mathematical: used to specify empirical quantities that can be measured

Hardy Weinberg principle: mathematical model used in population genetics to calculate and simplify genetic variation in a population across multiple generations, especially at a given locus or loci. 

1. Random Mating
2. No mutation
3. Infinite population size
4. No natural selection
5. No immigration/gene flow

1 =(p+q)2= p2 + 2pq + q2

P=probability. Of major allele 

Q=probability of minor allele 

\*observed and expected genotype frequencies used to determine whether a natural population is following HW proportions ]

Limitations: 

1. Small sample size, Chi square test can not be used when frequency is five or less
2. Loci with many alleles such as microsatellites
  1. Solution: permutation tests: uses computer based randomizations to analyze data
3. Every 100 tests of HW proportions where all 100 tested loci ar ein HW proportions would be rejected 5 times due to 0.5 p value (false positive aka type I error), in spite of HW proportions
  1. Solution: Bonferroni correction, which provides an appropriate adjustment to the significance level. Adjusts to make the P value divided by number of tests you're doing. Used a lot for microsatellites
  2. Q value: false discovery rate adjustment

To test for HW proportions 

1. Calculate expected frequencies of genotypes
2. Use these values and HW equation to calculate \# of expected individuals for each genotype within population
3. Then calculate chi square value using the equation, determine the degrees of freedom
4. Degrees of freedom is used to determine significance level .05

HW is used to determine unexpected variations 

Examples: 

DATA AA: 1 Aa: 18 aa: 1

P= f(A) 20/20\*2=0.5 

Q=f(a)= (1-p)=0.5

Expected(AA)= 0.5 x 0.5=0.25 x 20=5

Expected(Aa)=2pq= 2(.5)(.5) 10

\*\*multiplied by two because there are two possible unions (Aa or aA)

Example 2

Observed

P=f(D) 2(9) + 41/ 60\*2 =59/120= 0.49

q=f(d) 2(10) +41/2(60)=0.51

Expected: 

Frequency of DD= (0.49)(0.49)= 0.24 

Number of Individuals: frequency x n 0.24x 60

Frequency of Dd= 2(0.49)(0.51) =0.5 

Number of Individuals 0.5 x60=30 30 

Frequency of dd=(0.51)(0.51)= .26

Number of individuals: .26 x 60=15.6 

To determine chi square: 

DD X2= sum( (14.4-9)2 /14.4 + (41-30)2/30 + (15.6-10)2/15.6 )

X2= 2.025 + 4.033 + 2.01

X2= 8.06833

Degree of freedom determined by number of genotypes/ alleles 

Number of genotypes: 3

Number of alleles: 2

Degrees of freedom: 1

Refer to chart: 8.06833 \>3.841 Rejected hypothesis because we would have a less than 0.00458 likelihood of getting this data & this sample population & in Hardy Weinberg principles. 

Alleles

1. Dominant alleles
2. Recessive Alleles
3. Null alleles: caused by substitutions at microsatellite loci, which prevents primers from binding and therefore no PCR amplification product for testing, in animals no protein product/enzymatically functional protein if located at a allozyme loci/protein coding loci

Heterozygous=1 of each 

Homozygous=2 of the same allele 

Expectation maximum (EM) algorithm: used to determine genotypic frequencies within a sample based upon phenotype, which can be used to determine allelic frequencies using gene counting 

Sex linkage: responsible for the greater occurrence of recessive disorders and recessive traits

Homogametic: same alleles (female in mammals xx) (male in birds ZZ)

Heterogametic: two different alleles (male in mammals xy) (female in birds ZW)

Genetic variation: Average expected heterozygosity: which can be calculated by subtracting homozygosity 

Discussion: 

Statistical power

Question1 : Is statistically power actually a power analysis? I noticed the similarities between what influences power and a power analysis, but samples size affects power, and the goal of the power analysis is to determine the sample size.

Power analysis should be conducted before determining statistical power 

Question 2: How I understand it is that HW proportions describe a stable distribution of alleles and genotypes, but HW equilibrium is the lack of change, so allele and genotype frequencies remain constant and within a population if genotype frequencies match the HW proportions, the population is in equilibrium. So, doesn't this mean HW equilibrium and HW proportions are one in the same?

Author is making a semantic point-- to point out the potentially confusing language around HW proportions, you can't technically test for those conditions because they can't ever be met. 

Question 3: Does this mean that the question "Which multiple testing correction method should we use?" is redundant?

Trying to show that there isn't a relationship between the genotypes and phenotypes