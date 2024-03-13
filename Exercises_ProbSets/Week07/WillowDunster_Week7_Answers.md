# Willlow Dunster
#### Week 7 Problem Set
#### Bio 594
#### 13 March 2024

## 1. 
Q: Cross and Birley (1986) studied restriction site variation in the region of alccohol dehydrogenase (*Adh*)gene of *D. melanogaster* ina  population descended from flies trapped at a Dutch fruit market in Groningen.  The following data was collected:

| *Adh* Allele | *Eco*RI Allele| Individuals|
|-------------|----------------|------------|
|*Adh<sup>F</sup>*| *Eco*RI<sup>+</sup> | 22|
|*Adh<sup>S</sup>*| *Eco*RI<sup>+</sup> | 4|
|*Adh<sup>F</sup>*| *Eco*RI<sup>-</sup> | 3|
|*Adh<sup>S</sup>*| *Eco*RI<sup>-</sup> | 5|

Where *Adh<sup>F</sup>* and *Adh<sup>S</sup>* are the allozyme alleles of *Adh* and *Eco*RI<sup>+</sup> and *Eco*RI<sup>-</sup> indicate the presence or absence of an *Eco*RI restriction site 3.5 kb downstream
   * Test for the presence of linkage disequilibrium
   * If significant, express *D* relative to its theoretical maximum or minimum.

   $ D = (G1G4)-(G2G3)$ 
   where G1 and G4 are homozygous gametetypes 

   I do not know which alleles are homozygous and heterozygous so I do not know which ones to designate G1/G4 and G2/G3 


Haplotype $f$
| Haplo | Equation | $f$ | 
|-------|----------|-----|
| $F^+  $ | $\frac{22}{34}$ | 0.65 | 
| $S^+  $ | $\frac{4}{34}$ | 0.12 |
| $F^-  $ | $\frac{3}{34}$ | 0.09 |
| $S^-  $ | $\frac{5}{34}$ | 0.15 |

   Allelic $f$ 
   $ f = \frac{numalleles}{all alleles}$

| Allele | Equation | $f$ | 
|--------|----------|-----|
| $F$ | $\frac{25}{25+9}$ | 0.735 | 
| $S$ | $\frac{9}{25+9}$ | 0.265 |
| $+$ | $\frac{26}{26+8}$ | 0.765 |
| $-$ | $\frac{8}{26+8}$ | 0.235 |

$ D = (x_{11})(x_{22})-(x_{12})(x_{21})$
$= (0.65)(0.15)-(0.12)(0.09)$ $= 0.0867$ 

$ D = 0.0867 > 0 --> D_{max}$

$D_{max} = $ smaller of $x_{12}$ or $x_{21}$ = 0.09

$D^{prime} = \frac{D}{D_{max}} = \frac{0.0867}{0.09} = 0.96$

## 2. 
Q: Three linked loci in a random mating population have the gametic frequencies shown in the table below. Calculate the linkage disequilibrium *D*/*D<sub>max</sub>* between each pair of genes. Explain why the results seem paradoxical.

|Genotype | Frequency|
|---------|------|
| *ABC*| 0.25|
| *ABc*| 0|
| *AbC*| 0.25|
|*Abc*| 0|
|*aBC* | 0|
|*aBc* | 0.25|
|*abC* | 0|
|*abc*|0.25|

1 = A, B, C
2 = a, b, c 

$ D = (x_{111})(x_{222})-(x_{112})(x_{121})(x_{122})(x_{211})(x_{212})(x_{221}) = (0.25)(0.25)-(0)(0.25)(0)(0)(0.25)(0) = 0.0625$

$D^{prime} = \frac{D}{D_{max}} = \frac{0.0867}{0} = 0 $

I know it said between pairs of alleles but I do not know how to seperate them all

## 3.
Q: Two populations are examined for the same pair of loci with the following results in terms of two-locus gamete numbers:

|Population|Gamete| Count|
|----------|------|-------|
| Pop 1| AB | 720|
| Pop 1| Ab | 180|
| Pop 1| aB | 80|
| Pop 1| ab | 20|
| Pop 2| AB | 300|
| Pop 2| Ab | 2700|
| Pop 2| aB | 700|
| Pop 2| ab | 6300|

These two populations are now combined to form a third:

|Population|Gamete| Count|
|----------|------|-------|
| Pop 3| AB | 1020|
| Pop 3| Ab | 2880|
| Pop 3| aB | 780|
| Pop 3| ab | 6320|

* Calculate the two-locus gamete frequencies for each population and the gameticphase imbalance (linkage disequilibrium). Is any population out of linkage equilibrium?

Pop 1 
|Population|Gamete| Count| Gamete $f$ |
|----------|------|------|------------|
| Pop 1| AB | 720| $\frac{720}{1000} = 0.72$ |
| Pop 1| Ab | 180| $\frac{180}{1000} = 0.18$ |
| Pop 1| aB | 80| $\frac{80}{1000} = 0.08$ |
| Pop 1| ab | 20| $\frac{20}{1000} = 0.02$ |

$ D = (x_{11})(x_{22})-(x_{12})(x_{21})$
$= (0.72)(0.02)-(0.18)(0.08)$ $= 0$ 

pop 1 is in linkage equilibrium

Pop 2
|Population|Gamete| Count| Gamete $f$ |
|----------|------|------|------------|
| Pop 2| AB | 300| $\frac{300}{10,000} = 0.03$ |
| Pop 2| Ab | 2700| $\frac{2700}{10,000} = 0.27$ |
| Pop 2| aB | 700| $\frac{700}{10,000} = 0.07$ |
| Pop 2| ab | 6300| $\frac{6300}{10,000} = 0.63$ |

$ D = (x_{11})(x_{22})-(x_{12})(x_{21})$
$= (0.03)(0.63)-(0.27)(0.07)$ $= 0$ 

pop 2 is in linkage equilibrium


Pop 3 
|Population|Gamete| Count | Gamete $f$ |
|----------|------|-------|------------|
| Pop 3| AB | 1020| $\frac{1020}{11,000} = 0.09$ |
| Pop 3| Ab | 2880| $\frac{2880}{11,000} = 0.26$ |
| Pop 3| aB | 780| $\frac{780}{11,000} = 0.07$ |
| Pop 3| ab | 6320| $\frac{6320}{11,000} = 0.57$ |

$ D = (x_{11})(x_{22})-(x_{12})(x_{21})$
$= (0.09)(0.57)-(0.26)(0.07)$ $= 0.0331$ 

pop 3 is not in linkage equilibrium (D = 0.0331 > 0)

* What is the effect of pooling of the two populations on linkage equilibrium?

Pooling the two populations resulted in linkage disequilibrium where D = 0.0331

* Suppose that the recombination rate between loci A/a and B/b is 0.1. What is the expected disequibrium in the offspring of population 3 (the parental gene pool), assuming random mating? In the second generation?

$D_{expectedparental} = p(AB)p(ab)-p(Ab)p(aB) = (0.09)(0.57)-(0.26)(0.07) = 0.0331$

F1 generation 

$p(Ab) = p(AB)(1-r)= (0.09)(1-0.1) = 0.081 $

$p(aB) = p(ab)(1-r) = (0.57)(1-0.1) = 0.513$

$D_{F1} = p(AB)p(ab)-p(Ab)p(aB) = (0.09)(0.57)-(0.081)(0.513) = 0.0097$

$D_{F2} = p(AB)p(ab)-p(Ab)p(aB) = (0.09)(0.57)-(0.081)(0.513) = 0.0097

I think I got this wrong because D will not change from F1 to F2 and it should be decreasing because there is recombination? 


* Can this single episode of admixture be detected in the population established from population 3 after two generations of random mating? Can it be detected in the genotype frequencies at the A/a locus after two generations of random mating? Can it be detected in the genotype frequencies at the B/b locus after two generations of random mating?

I do not know how to answer this question. I think it can still be detected in population 3 after 2 generations because D is not equal to 0. 

## 4.  
Q: A continuous trait is distributed approximately according to a normal distribution with mean 100 and standard deviation of 15.  What proportion of the population is expected to have a phenotypic value above 130?  Below 85?  Above 85?

Above 130
$z = \frac{x-mean}{SD} = \frac{130-100}{15} = 2$

from a normal distribution table Z=2 = 0.03

Below 85
$z = \frac{x-mean}{SD} = \frac{85-100}{15} = -1$

from a normal distribution table z = -1 = 0.16

Above 85 
becaue its normal above 85 = 1 - below 85
$ = 1-0.16 - 0.84


## 5. 
Q: A genetically heterogeneous population of wheat has a variance in the number A days to maturation of 40, whereas two inbred populations derived from it have a variance in the number of days to maturation of 10.  

* What is the genotypic variance (V<sub>G</sub> or $\sigma_{g}^2$), the environmental variance (V<sub>E</sub> or $\sigma_{e}^2$), and the broad sense heritablilty *H*<sup>2</sup>, of days to maturation in this population?

$V_G = variance of inbred pops$

$V_E = variance of heterogenous pop$

$H^2 = \frac{V_G}{V_P}$

$V_P = V_G + V_E $

$V_E=40$ 

$V_G=10$

$H^2 = \frac{10}{10+40} = 0.2$

* If the inbred lines were crossed, what would be the predicted variance in days to maturation of the F<sub>1</sub> generation?

Add 1/2 parental genotypic variance to environmental. There is no V_G in F_1 because of total heterozygositity (I looked this up I am not sure why)

$V_{F1} = \frac{V_G}{2} + V_E = \frac{10}{2}+40 = 45$ days 


## 6. 
Q: In comparing a quantitative trait in the F<sub>1</sub> and F<sub>2</sub> generations obtained by crossing two highly inbred strains: 
* Which set of progeny provides an estimate of the environmental variance?

F_1 will provide environmental variance because all indv will be genetically identical. Any variation observed is soley due to environmental factors

* What determins the variance of the other set of progeny?

F_2 variance is determined by both genetic and environmental factors

## 7. 
Q: In a cross between two cultivated inbred varieties of tobacco, the variance in leaf number per plant in the F<sub>1</sub> generation is 1.46 and in the F<sub>2</sub> generation it is
5.97. What are the genotypic and environmental variances? What is the broad-sense heritability in leaf number?

$V_E = 1.46$ because F_1 is heterogeneous pop

$V_G = V_P - V_E = 5.97-1.46 = 4.51$

$H^2 = \frac{V_G}{V_P}=\frac{4.51}{5.97}=0.75$















   


 


