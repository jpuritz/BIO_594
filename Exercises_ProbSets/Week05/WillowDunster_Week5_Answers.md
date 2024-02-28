# Willlow Dunster
#### Week 5 Problem Set
#### Bio 594
#### 28 February 2024

## 1. 
Q: What is the probability that a particular allele has at least one copy in the next generation?  The surprising answer quickly becomes independent of population size as *N* becomes larger.  (Hint: Use one minus the probability that the allele has no copies in the next generation and this equation: $\lim\limits_{\varepsilon \to \infty}(1+\varepsilon*x)^\frac{1}{\varepsilon} = e^x$)

probability allele does not get chosen to repro = 1 - $\frac{1}{2N}$

probability for a whole generation = (1 - $\frac{1}{2N})^2N$ but I don't understand why 

for an infinite pop e^x becomes 1/e

probability of non extinction = $1 - 1/e$


## 2. 
Q: Assuming that the actual size of the population in any year equals the effective population size in that year, estimate the average effective number over the entire 12-year period.

Ne = $\frac{t}{sum \frac{1}{Ni}}$

Ne = $\frac{12}{0.00305}$

Ne= 3934.43 --> 3935

## 3.
Q: A dairy farmer has a herd consisting of 200 cows and 2 bulls. What is the effective population size?

with unequual sex ratios Ne will rarely be greater than 2x rarer sex = 4

*N<sub>e</sub>* = $\frac{4N~m~ N~f~}{N~m~ N~f~}$

*N<sub>e</sub>* = $\frac{4 * 2 * 200}{2 * 200}$

*N<sub>e</sub>* = 4

## 4. 
Q: A rare triggerplant from Australia (Stylidium coroniforme) has only five known populations (Coates 1992). One of these populations has been monitored for several years, and over five years in the early 1980s: 2, 3, 25, 32, and 86 plants were recoreded. Assuming Ne = Nc in that year, estimate Ne as well as the average Nc over this period. What biological principle is illustrated by this example?

*N<sub>e</sub>* = $\frac{t}{sum \frac{1}{Ni}}$

*N<sub>e</sub>* = $\frac{5}{0.9162}$
*N<sub>e</sub>* = 5.457

avg *N<sub>c</sub>* = 29.6

This illustrates the biological principle that not all individuals in a population will/can mate. It can also show an inbreeding depression 


## 5. 
| Locality| A<sub>1</sub>A<sub>1</sub> | A<sub>1</sub>A<sub>2</sub> | A<sub>2</sub>A<sub>2</sub>|
|---------|--------------|---------|---------|
|Munich| 6|33|81|
|Innsbruck| 20|59|43|
|Verona|65|39|14|

A. Calculate the frequencies of the two alleles in each population

Allele Frequency = $\frac{(2 \cdot Number of Individuals Homozygotes) + Number of Heterozygotes}{2 \cdot Total Individuals}$

### Munich
Allele Freq A<sub>1 munich</sub> = $\frac{(2 \cdot 6) + 33}{2 \cdot 120}$
Allele Freq A<sub>1 munich</sub> = 0.1875

Allele Freq A<sub>2 munich</sub> = $\frac{(2 \cdot 81) + 33}{2 \cdot 120}$
Allele Freq A<sub>2 munich</sub> = 0.8125


### Innsbruck 
Allele Freq A<sub>1 innsbruck</sub> = $\frac{(2 \cdot 20) + 59}{2 \cdot 122}$
Allele Freq A<sub>1 innsbruck</sub> = 0.4057

Allele Freq A<sub>2 innsbruck</sub> = $\frac{(2 \cdot 43) + 59}{2 \cdot 122}$
Allele Freq A<sub>2 innsbruck</sub> = 0.5943

### Verona 
Allele Freq A<sub>1 verona</sub> = $\frac{(2 \cdot 65) + 39}{2 \cdot 118}$
Allele Freq A<sub>1 verona</sub> = 0.7161

Allele Freq A<sub>2 verona</sub> = 1- Allele Freq A<sub>1 verona</sub> 
Allele Freq A<sub>2 verona</sub> = 0.2839

B. Do any populations have excess heterozygotes?

Genotypic Freq A<sub>1</sub>A<sub>2</sub> = 2pq $\cdot NumberofIndividuals$

### Munich
Genotypic Freq A<sub>1</sub>A<sub>2</sub> = $(2 \cdot 0.1875 \cdot 0.8125) \cdot 120$
Genotypic Freq A<sub>1</sub>A<sub>2</sub> = 36.6 > observed

### Innsbruck
Genotypic Freq A<sub>1</sub>A<sub>2</sub> = $(2 \cdot 0.4057 \cdot 0.5943) \cdot 122$
Genotypic Freq A<sub>1</sub>A<sub>2</sub> = 29.4 << observed 

### Verona 
Genotypic Freq A<sub>1</sub>A<sub>2</sub> = $(2 \cdot 0.7161 \cdot 0.2839) \cdot 118$
Genotypic Freq A<sub>1</sub>A<sub>2</sub> = 24 < observed 

There is an excess of heterozygotes in Innsbruck and Verona

C. Do any populations have a deficit of heterozygotes?

Yes there is a deficit of heterozygotes in Munich 

D. Calculate FIS for each of the populations and how does this related to B and C?

$F_{IS} = \frac{H_exp - H_obs}{H_exp}$

### Munich 
$F_{IS} = \frac{36.6 - 33}{36.6}$
$F_{IS} = 0.098

### Innsbruck 
$F_{IS} = \frac{29.4 - 59}{29.4}$
$F_{IS} = -1.00

### Verona
$F_{IS} = \frac{24 - 39}{24}$
$F_{IS} = -0.625

B and C calculated the expected numbers of Ht in the populations. $F_{IS}$ calculates the . Values approaching 1 indicate less Ht while values approaching -1 indicate an excess of Ht. 












