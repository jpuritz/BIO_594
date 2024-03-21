# Problem Set 4


## Answers


1. Cross and Birley (1986) studied restriction site variation in the region of alccohol dehydrogenase (*Adh*)gene of *D. melanogaster* ina  population descended from flies trapped at a Dutch fruit market in Groningen.  The following data was collected:

| *Adh* Allele | *Eco*RI Allele| Individuals|
|-------------|----------------|------------|
|*Adh<sup>F</sup>*| *Eco*RI<sup>+</sup> | 22|
|*Adh<sup>S</sup>*| *Eco*RI<sup>+</sup> | 4|
|*Adh<sup>F</sup>*| *Eco*RI<sup>-</sup> | 3|
|*Adh<sup>S</sup>*| *Eco*RI<sup>-</sup> | 5|


Where *Adh<sup>F</sup>* and *Adh<sup>S</sup>* are the allozyme alleles of *Adh* and *Eco*RI<sup>+</sup> and *Eco*RI<sup>-</sup> indicate the presence or absence of an *Eco*RI restriction site 3.5 kb downstream
   * Test for the presence of linkage disequilibrium
   * If significant, express *D* relative to its theoretical maximum or minimum.

```
Total # of individuals = 22 + 4 + 3 + 5 = 34
$$ G_1 = \frac{22}{34} = 0.65
$$ G_2 = \frac{4}{34} = 0.12
$$ G_3 = \frac{3}{34} = 0.09
$$ G_4 = \frac{5}{34} = 0.14

D = G_1G_4 - G_2G_3

D = 0.65*0.14 - 0.12*0.09 = 0.091 - 0.0108 = 0.0802 This shows linkage disequilbrium

The theoretical maximum of D is 0.25 

$$ \frac{D}{D_max} = \frac{0.802}{0.25} = 0.3208
```

### 2. Three linked loci in a random mating population have the gametic frequencies shown in the table below. Calculate the linkage disequilibrium *D*/*D<sub>max</sub>* between each pair of genes. Explain why the results seem paradoxical.

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

```
AB
D = G1G4 - G2G3 = AB* ab - Ab * aB 
0.25* 0.25 - 0.25* 0.25 = 0
$$ \frac{D}{Dmax} = \frac{0}{0.25} = 0

BC 
D = G1G4 - G2G3 = BC* bc - Bc * bC 
0.25* 0.25 - 0.25* 0.25 = 0
$$ \frac{D}{Dmax} = \frac{0}{0.25} = 0

AC
D = G1G4 - G2G3 = AC* ac - Ac * aC 
0.5* 0.5 - 0* 0 = 0.25
$$ \frac{D}{Dmax} = \frac{0.25}{0.25} = 1

The results seem paradoxical because AC link link loci show they have linkage disequilibrium however AB and BC pairs are in equilibrum.
```

### 3. Two populations are examined for the same pair of loci with the following results in terms of two-locus gamete numbers:

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
```
#### Population 1
D=(G1G4)-(G2G3)
D=(0.72 * 0.02) - (0.18 * 0.08) = (0.0144) - (0.0144)D = 0
Linkage equilibrium is seen in population 1

#### Population 2
D=(G1G4)-(G2G3)
D=(0.03 * 0.63) - (0.27 * 0.07) = (0.0189) - (0.0189) = 0
Linkage equilibrium is seen in population 2

#### Population 3
D=(G1G4)-(G2G3)
D= (0.0927 * 0.575) - (0.262 * 0.071) = (0.0533) - (0.0186) = 0.0347
Linkage disequilibrium is seen in population 3
```
   * What is the effect of pooling of the two populations on linkage equilibrium?
By pooling the two populations the third became disequibrium
	
	r=0.1, D=0.0347
	F1
	D = D(1−r) = 0.0347(1-0.1) = 0.0312~
	F2
	D = D(1−r) = 0.0312(1-0.1) = 0.0281~
	
   * Suppose that the recombination rate between loci A/a and B/b is 0.1. What is the expected disequibrium in the offspring of population 3 (the parental gene pool), assuming random mating? In the second generation?

   * Can this single episode of admixture be detected in the population established from population 3 after two generations of random mating? Can it be detected in the genotype frequencies at the A/a locus after two generations of random mating? Can it be detected in the genotype frequencies at the B/b locus after two generations of random mating?

4. A continuous trait is distributed approximately according to a normal distribution with mean 100 and standard deviation of 15.  What proportion of the population is expected to have a phenotypic value above 130?  Below 85?  Above 85?

```
The proportion of the population expected to have a phenotypic value above 130 is 2.35%: 2 standard deviations from the mean
The proportion of the population expected to have a phenotypic value below 85 is 15.85% 1 standard deviations from the mean 
The proportion of the population expected to have a phenotypic value above 85 84.15% 
```

5. A genetically heterogeneous population of wheat has a variance in the number A days to maturation of 40, whereas two inbred populations derived from it have a variance in the number of days to maturation of 10.  
   * What is the genotypic variance (V<sub>G</sub> or $\sigma_{g}^2$), the environmental variance (V<sub>E</sub> or $\sigma_{e}^2$), and the broad sense heritablilty *H*<sup>2</sup>, of days to maturation in this population?
   * If the inbred lines were crossed, what would be the predicted variance in days to maturation of the F<sub>1</sub> generation?

```
V<sub>P</sub> (phenotypic variance): 40
V<sub>E</sub> environmental variance: 10

V<sub>P</sub> = V<sub>E</sub> + V<sub>G</sub>
V<sub>P</sub> - V<sub>E</sub> = V<sub>G</sub>
40- 10 = 30

$$ HB = \frac{V<sub>G</sub>}{V<sub>P</sub>}
$$ HB = \frac{30}{40} = 0.75
```
```
The predicted variance of the F<sub>1</sub> Generation would be 10 because genertic variance would be the same
```

6. In comparing a quantitative trait in the F<sub>1</sub> and F<sub>2</sub> generations obtained by crossing two highly inbred strains: 
   * Which set of progeny provides an estimate of the environmental variance?
   * What determins the variance of the other set of progeny?
```
The F<sub>1</sub> generation would provide an estimate of the environmental variance.
The F<sub>2</sub> generation variance would be determined by the genotypic variance and the environmental variance.
```

7. In a cross between two cultivated inbred varieties of tobacco, the variance in leaf number per plant in the F<sub>1</sub> generation is 1.46 and in the F<sub>2</sub> generation it is
5.97. What are the genotypic and environmental variances? What is the broad-sense heritability in leaf number?
Vp=VE + VG

```
F<sub>1</sub> = 1.46 = V<sub>E</sub>
F<sub>2</sub> = 5.97 = V<sub>P</sub>

V<sub>P</sub> = V<sub>E</sub> + V<sub>G</sub>
V<sub>G</sub> = V<sub>P</sub> - V<sub>E</sub>
V<sub>G</sub> = 5.97 - 1.46 = 4.51

$$ HB = \frac{V<sub>G</sub>}{V<sub>P</sub>}
$$ HB = \frac{4.51}{5.97} = 0.76~
```


















