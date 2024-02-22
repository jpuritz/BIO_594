# Cassandra Cerasia
#### Week 4 Homework Problem Set
#### BIO 594
#### February 22 2024

## 1. 
50% (0.50) chances of the A or G allele at the SNP. Both A and G have the same allele frequencies.

Set 1:
$0.5^{3} = 0.125$

Set 2: 
$0.5^{5} = 0.03125$

Set 3: 
$0.5^{5} = 0.03125$

## 2. 
#### A. What are the observed genotype and allele frequencies? 
 Genotype Frequency = $\frac{Number of Genotype}{Total Individuals}$

Genotype Frequency SS = $\frac{11}{127}$

Genotype Frequency SS = $0.087$

Genotype Frequency SS- = $\frac{55}{127}$

Genotype Frequency SS- = $0.43$

Genotype Frequency S-S- = $\frac{61}{127}$

GenotypeFrequency S-S- = $0.48$

Allele Frequency = $\frac{(2 \cdot Number of Individuals Homozygotes) + Number of Heterozygotes}{2 \cdot Total Individuals}$

Allele Frequency S = $\frac{(2 \cdot 11) + 55}{2 \cdot 127}$

Allele Frequency S = $0.30$

Allele Frequency S- = $\frac{(2 \cdot 61) + 55}{2 \cdot 127}$

Allele Frequency S = $0.70$

Allele Frequency S = p = $0.30$

Allele Frequency S- = q = $0.70$

#### B. Given the observed allele frequencies, what are the genotypic frequencies expected under Hardy-Weinberg?  Using a chi-square test, how well do the observed genotype frequences agree with the HWE expecations?

Expected Genotypic Frequency SS = ${p^{2}}{\cdot Number of Individuals}$

Expected Genotypic Frequency SS = ${0.30^{2}}{\cdot 127}$

Expected Genotypic Frequency SS = $11.7$

Expected Genotypic Frequency S-S- = ${q^{2}}{\cdot Number of Individuals}$

Expected Genotypic Frequency SS = ${0.70^{2}}{\cdot 127}$

Expected Genotypic Frequency SS = $61.7$

Expected Genotypic Frequency SS- = ${2pq}{\cdot Number of Individuals}$

Expected Genotypic Frequency SS = ${2(0.30 \cdot0.70)}{\cdot 127}$

Expected Genotypic Frequency SS = $53.7$

$\chi^2 = \sum \frac{(Observed  SS - Expected SS)^2}{Expected SS} + \frac{(Observed  SS- - Expected SS-)^2}{Expected SS-} + \frac{(Observed  S-S- - Expected S-S-)^2}{Expected S-S-}$

$\chi^2 = \sum \frac{(11 - 11.7)^2}{11.7} + \frac{(61 - 61.7)^2}{61.7} + \frac{(55 - 53.7)^2}{53.7}$

$\chi^2 = \sum \frac{(- 0.70)^2}{11.7} + \frac{(-0.70)^2}{61.7} + \frac{(1.3)^2}{53.7}$

$\chi^2 = \sum \frac{0.45}{11.7} + \frac{0.45}{61.7} + \frac{1.8}{53.7}$

$\chi^2 = \sum 0.039 + 0.0073 + 0.04$

$\chi^2 = 0.080

For 2 alleles and 3 genotypes, degress of freedom = 1 

alpha = 0.05 significance 

$\chi^2$ table value = 3.841

0.080 < 3.841, the observed population does agree with Hardy Weinberg Expectations

#### C. What is the observed heterozygosity in this population and what is the expected heterozygosity?

Expected Genotypic Frequency SS- = ${2pq}{\cdot Number of Individuals}$

Expected Genotypic Frequency SS = ${2(0.30 \cdot0.70)}{\cdot 127}$

Expected Genotypic Frequency SS = $53.7$

Expected Heterozygosity = 53.7 

Observed Heterozygosity = 55 

## 3. 
#### A. What are the observed genotype and allele frequencies?

Genotype Frequency = $\frac{Number of Genotype}{Total Individuals}$

Genotype Frequency A/A = $\frac{0}{10}$

Genotype Frequency A/A = $0$

Genotype Frequency A/G = $\frac{10}{10}$

Genotype Frequency A/G = $1.0$

Genotype Frequency G/G = $\frac{0}{10}$

GenotypeFrequency G/G = $0$

Allele Frequency = $\frac{(2 \cdot Number of Individuals Homozygotes) + Number of Heterozygotes}{2 \cdot Total Individuals}$

Allele Frequency A = $\frac{(2 \cdot 0) + 10}{2 \cdot 10}$

Allele Frequency A = $0.50$

Allele Frequency G = $\frac{(2 \cdot 0) + 10}{2 \cdot 10}$

Allele Frequency G = $0.5$

Allele Frequency A = p = $0.50$

Allele Frequency G = q = $0.50$

#### B. Given the observed allele frequencies, what are the genotypic frequencies expected under Hardy-Weinberg?  Using a chi-square test, how well do the observed genotype frequences agree with the HWE expecations?

Expected Genotypic Frequency A/A = ${p^{2}}{\cdot Number of Individuals}$

Expected Genotypic Frequency A/A = ${0.50^{2}}{\cdot 10}$

Expected Genotypic Frequency A/A = $2.5$

Expected Genotypic Frequency G/G = ${q^{2}}{\cdot Number of Individuals}$

Expected Genotypic Frequency G/G = ${0.50^{2}}{\cdot 10}$

Expected Genotypic Frequency G/G = $2.5$

Expected Genotypic Frequency A/G = ${2pq}{\cdot Number of Individuals}$

Expected Genotypic Frequency A/G = ${2(0.50 \cdot0.50)}{\cdot 10}$

Expected Genotypic Frequency A/G = $5$

$\chi^2 = \sum \frac{(Observed  A/A - Expected A/A)^2}{Expected A/A} + \frac{(Observed  A/G - Expected A/G)^2}{Expected A/G} + \frac{(Observed  G/G - Expected G/G)^2}{Expected G/G}$

$\chi^2 = \sum \frac{(0 - 2.5)^2}{2.5} + \frac{(10 - 5)^2}{5} + \frac{(0-2.5)^2}{2.5}$

$\chi^2 = \sum \frac{(- 2.5)^2}{2.5} + \frac{(5)^2}{5} + \frac{(-2.5)^2}{2.57}$

$\chi^2 = \sum \frac{6.25}{2.5} + \frac{25}{5} + \frac{6.25}{2.5}$

$\chi^2 = \sum 2.5 + 5 + 2.5$

$\chi^2 = 10

For 2 alleles and 3 genotypes, degress of freedom = 1 

alpha = 0.05 significance 

$\chi^2$ table value = 3.841

10 > 3.841, the observed population does not agree with Hardy Weinberg Expectations

#### C. Simulate one generation of random mating (you don't need to code this simulation; it can be by hand):
    * Pair off the ten indivduals into mating pairs
    * Randomly pick two expected offspring genotypes per pair (10 offspring genotypes)
    * Create a new genotype table from the offsrping only (should only be 10 genotypes)
    * Repeat subqestions A and B on the new genotype table

|Genotype|Count|
|--------|-----|
|A/A|2|
|A/G|5|
|GG|3|

#### A. What are the observed genotype and allele frequencies?

Genotype Frequency = $\frac{Number of Genotype}{Total Individuals}$

Genotype Frequency A/A = $\frac{2}{10}$

Genotype Frequency A/A = $0.2$

Genotype Frequency A/G = $\frac{5}{10}$

Genotype Frequency A/G = $0.5$

Genotype Frequency G/G = $\frac{3}{10}$

GenotypeFrequency G/G = $0.3$

Allele Frequency = $\frac{(2 \cdot Number of Individuals Homozygotes) + Number of Heterozygotes}{2 \cdot Total Individuals}$

Allele Frequency A = $\frac{(2 \cdot 2) + 5}{2 \cdot 10}$

Allele Frequency A = $0.45$

Allele Frequency G = $\frac{(2 \cdot 3) + 5}{2 \cdot 10}$

Allele Frequency G = $0.55$

Allele Frequency A = p = $0.45$

Allele Frequency G = q = $0.55$

#### B. Given the observed allele frequencies, what are the genotypic frequencies expected under Hardy-Weinberg?  Using a chi-square test, how well do the observed genotype frequences agree with the HWE expecations?

Expected Genotypic Frequency A/A = ${p^{2}}{\cdot Number of Individuals}$

Expected Genotypic Frequency A/A = ${0.45^{2}}{\cdot 10}$

Expected Genotypic Frequency A/A = $2.03$

Expected Genotypic Frequency G/G = ${q^{2}}{\cdot Number of Individuals}$

Expected Genotypic Frequency G/G = ${0.55^{2}}{\cdot 10}$

Expected Genotypic Frequency G/G = $3.03$

Expected Genotypic Frequency A/G = ${2pq}{\cdot Number of Individuals}$

Expected Genotypic Frequency A/G = ${2(0.50 \cdot0.50)}{\cdot 10}$

Expected Genotypic Frequency A/G = $4.95$

$\chi^2 = \sum \frac{(Observed  A/A - Expected A/A)^2}{Expected A/A} + \frac{(Observed  A/G - Expected A/G)^2}{Expected A/G} + \frac{(Observed  G/G - Expected G/G)^2}{Expected G/G}$

$\chi^2 = \sum \frac{(2 - 2.03)^2}{2.03} + \frac{(5 - 4.95)^2}{4.95} + \frac{(3-3.03)^2}{3.03}$

$\chi^2 = \sum \frac{(-0.03)^2}{2.03} + \frac{(0.05)^2}{4.95} + \frac{(-0.03)^2}{3.03}$

$\chi^2 = \sum \frac{0.0006}{2.03} + \frac{0.0025}{4.95} + \frac{0.0006}{3.03}$

$\chi^2 = \sum 0.0003 + 0.0005 + 0.0002$

$\chi^2 = 0.001

For 2 alleles and 3 genotypes, degress of freedom = 1 

alpha = 0.05 significance 

$\chi^2$ table value = 3.841

10 > 3.841, the observed population does not with Hardy Weinberg

0.001 < 3.841, the observed population does agree with Hardy Weinberg Expectations

## 4. 
#### A. Estimate the frequency (q) of the null allele of each of the two AFLP markers assuming HWE.

For any individual with a null allele:

Allele Frequency q = $\frac{(6 + 101 + (2 \cdot 14))}{2 \cdot ((6 + 101 + 14) +39)}$

Allele Frequency q = $\frac{135}{2 \cdot (160)}$

Allele Frequency q = $\frac{135}{320}$

Allele Frequency q = $0.42$

Upper Null Allele: $\frac{6+14}{2 \cdot (160)}$

Upper Null Allele: $\frac{20}{320}$

Upper Null Allele: $0.06$

Lower Null Allele: $\frac{101+14}{2 \cdot (160)}$

Lower Null Allele: $\frac{115}{320}$

Lower Null Allele: $0.4$



 ####  B. Estimate the percentage of *band-present* individuals (not the overall frequencies) that are heterozygous at each of the two markers.  What biological principle does the difference between these two percentages illustrate?
 % Band Present Heterozygous= $\frac{Individuals With 1 band + Individuals With 1 band}{Number Individuals}$

  % Band Present Heterozygous Upper= $\frac{101}{160} \cdot 100$

  % Band Present Heterozygous Upper= $0.631 \cdot 100$

  % Band Present Heterozygous Upper= 63.1%

  
  % Band Present Heterozygous Lower = $\frac{6}{160} \cdot 100$

  % Band Present Heterozygous Lower= $0.0375 \cdot 100$

  % Band Present Heterozygous Lower= 3.75%

  Difference between two percentages = 63.1% - 3.75% = 59.4%
  The biological principle the difference between the two percentages represents could maybe be a measure of genetic variation, but I am a little unsure. Maybe the percentage could also be a measure of selection. 






















