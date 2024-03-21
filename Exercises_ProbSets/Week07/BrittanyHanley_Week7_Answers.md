## Week 7 problem set
Brittany Hanley

# 1. Cross and Birley (1986) studied restriction site vvariation in the region of alccohol dehydrogenase (*Adh*)gene of *D. melanogaster* ina  population descended from flies trapped at a Dutch fruit market in Groningen.  The following data was collected:

| *Adh* Allele | *Eco*RI Allele| Individuals|
|-------------|----------------|------------|
|*Adh<sup>F</sup>*| *Eco*RI<sup>+</sup> | 22|
|*Adh<sup>S</sup>*| *Eco*RI<sup>+</sup> | 4|
|*Adh<sup>F</sup>*| *Eco*RI<sup>-</sup> | 3|
|*Adh<sup>S</sup>*| *Eco*RI<sup>-</sup> | 5|


Where *Adh<sup>F</sup>* and *Adh<sup>S</sup>* are the allozyme alleles of *Adh* and *Eco*RI<sup>+</sup> and *Eco*RI<sup>-</sup> indicate the presence or absence of an *Eco*RI restriction site 3.5 kb downstream
   * Test for the presence of linkage disequilibrium
   * If significant, express *D* relative to its theoretical maximum or minimum.
   
Allele Frequency = $\frac{individuals}{total}$

|Allele|Equation|Frequency|
|-----|-----|----|
|AdhF|$\frac{25}{34}$|0.74|
|AdhS|$\frac{9}{34}$|0.26|
|EcoRI+|$\frac{26}{34}$|0.76|
|EcoRI-|$\frac{8}{34}$|0.24|

|Adh Allele|EcoRI Allele|Individuals|Frequency|
|AdhF|EcoRI+|22|$G_{1}$ = (p1)(p2) --> G1 = (0.74)(0.76) --> G1 = 0.56|
|AdhS|EcoRI+|4|$G_{2}$ = (q1)(p2) --> G2 = (0.26)(0.76) --> G2 = 0.2|
|AdhF|EcoRI-|3|$G_{3}$ = (p1)(q2) --> G3 = (0.74)(0.24) --> G3 = 0.18|
|AdhS|EcoRI-|5|$G_{4}$ = (q1)(q2) --> G4 = (0.26)(0.24) --> G4 = 0.06|

D = ((G1)(G4)) - ((G2)(G3)) --> D = ((0.56)(0.06)) - ((0.2)(0.18)) --> D = 0

D = 0, linkage is in equilibrium

$D_{max}$ = smallest of heterozygote frequency

$D_{max}$ = 0.18

$D^{prime}$ = $\frac{D}{$D_{max}$}$ --> $D^{prime}$ = 0/0.18 --> $D^{prime}$ = 0
   

# 2. Three linked loci in a random mating population have the gametic frequencies shown in the table below. Calculate the linkage disequilibrium *D*/*D<sub>max</sub>* between each pair of genes. Explain why the results seem paradoxical.

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

D = ((G1)(G4)) - ((G2)(G3))
$D^{prime}$ = $\frac{D}{$D_{max}$}$


for AB:
G1 = AB
G2 = Ab
G3 = aB
G4 = ab

D = ((0.25)(0.25)) - ((0.25)(0.25))
D = 0
$D_{max}$ = 0.25
$D^{prime}$ = $\frac{0}{0.25}$ --> $D^{prime}$ = 0


for BC:
G1 = BC
G2 = Bc
G3 = bC
G4 = bc

D = ((0.25)(0.25)) - ((0.25)(0.25))
D = 0
$D_{max}$ = 0.25
$D^{prime}$ = $\frac{0}{0.25}$ --> $D^{prime}$ = 0


for AC:
G1 = AC
G2 = Ac
G3 = aC
G4 = ac

D = ((0.5)(0.5)) - ((0)(0))
D = 0.25
$D_{max}$ = 0.25
$D^{prime}$ = $\frac{0.25}{0.25}$ --> $D^{prime}$ = 1


the results are paradoxical because while AB and BC are in linkage equilibrium, AC isn't, where it would make more sense if either all of them them are in linkage equilibrium or all of them aren't.

# 3. Two populations are examined for the same pair of loci with the following results in terms of two-locus gamete numbers:

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
   
|Population|Gamete| Count|Frequency|
|----------|------|-------|
| Pop 1| AB | 720| $\frac{720}{1000}$ = 0.72|
| Pop 1| Ab | 180| $\frac{180}{1000}$ = 0.18|
| Pop 1| aB | 80| $\frac{80}{1000}$ = 0.08|
| Pop 1| ab | 20| $\frac{20}{1000}$ = 0.02|

D = ((AB)(ab)) - ((Ab)(aB)) --> D = ((0.72)(0.02)) - ((0.18)(0.08))
D = 0, population 1 is in linkage equilibrium


|Population|Gamete| Count|Frequency|
|----------|------|-------|----|
| Pop 2| AB | 300| $\frac{300}{10,000}$ = 0.03|
| Pop 2| Ab | 2700|$\frac{2700}{10,000}$ = 0.27|
| Pop 2| aB | 700|$\frac{700}{10,000}$ = 0.07|
| Pop 2| ab | 6300|$\frac{6300}{10,000}$ = 0.63|

D = ((0.03)(0.63)) - ((0.27)(0.07))
D = 0, population 2 is in linkage equilibrium


|Population|Gamete| Count|Frequency|
|----------|------|-------|----|
| Pop 3| AB | 1020|$\frac{1020}{11,000}$ = 0.09|
| Pop 3| Ab | 2880|$\frac{2880}{11,000}$ = 0.26|
| Pop 3| aB | 780|$\frac{780}{11,000}$ = 0.07|
| Pop 3| ab | 6320|$\frac{6320}{11,000}$ = 0.57|

D =((0.09)(0.57)) - ((0.26)(0.07))
D = 0.03, population 3 is in linkage disequilibrium


   * What is the effect of pooling of the two populations on linkage equilibrium?
   
      Pooling the two populations resulted in the combined population (pop 3) being in linkage disequilibrium


   * Suppose that the recombination rate between loci A/a and B/b is 0.1. What is the expected disequibrium in the offspring of population 3 (the parental gene pool), assuming random mating? In the second generation?
   
      $D^{prime}$ = D(1 - r), r = 0.1
      Gen 1 
      D = 0.03
      
      Gen 2
      $D^{prime}$ = 0.03(1 - 0.1) --> $D^{prime}$ = 0.27
      
      Gen 3
      $D^{prime}$ = 0.27(1 - 0.1) --> $D^{prime}$ = 0.24
      

   * Can this single episode of admixture be detected in the population established from population 3 after two generations of random mating? Can it be detected in the genotype frequencies at the A/a locus after two generations of random mating? Can it be detected in the genotype frequencies at the B/b locus after two generations of random mating?

  not sure how to answer this. 

# 4. A continuous trait is distributed approximately according to a normal distribution with mean 100 and standard deviation of 15.  What proportion of the population is expected to have a phenotypic value above 130?  Below 85?  Above 85?
  
  z = x - $\frac{mean}{stdev}$
  
  z = 130 - $\frac{100}{15}$ --> z = 2
  above 130 = 2.3% of pop 
  
  z = 85 - $\frac{100}{15}$ --> z = -1
  below 85 = 15.9% of pop
  
  above 85 = 84.13% of pop
  

# 5. A genetically heterogeneous population of wheat has a variance in the number A days to maturation of 40, whereas two inbred populations derived from it have a variance in the number of days to maturation of 10.  
   * What is the genotypic variance (V<sub>G</sub> or $\sigma_{g}^2$), the environmental variance (V<sub>E</sub> or $\sigma_{e}^2$), and the broad sense heritablilty *H*<sup>2</sup>, of days to maturation in this population?
   
   $V_{p}$ = $V_{g}$ + $V_{e}$
   $V_{e}$ = 10
   $V_{p}$ = 40
  
  40 = $V_{g}$ + 10 --> $V_{g}$ = 30
  
  genotypic varience ($V_{g}$) = 30 days
  environmental varience ($V_{e}$) = 10 days
  
  $H_{b}$ = $\frac{$V_{g}$}{$V_{p}$}$
  $H_{b}$ = $\frac{30}{40}$ --> $H_{b}$ = 0.75
  
  broad sense heritability ($H_{b}$) = 0.75 days
   
   
   * If the inbred lines were crossed, what would be the predicted variance in days to maturation of the F<sub>1</sub> generation?

  not sure? 


# 6. In comparing a quantitative trait in the F<sub>1</sub> and F<sub>2</sub> generations obtained by crossing two highly inbred strains: 
   * Which set of progeny provides an estimate of the environmental variance?
   
   F1, because it's the first generation and there is no genetic variation being added
   
   
   * What determins the variance of the other set of progeny?
   
   F2 would be determined by both genetic variation (from the first generation) and environmental variation
   
   

# 7. In a cross between two cultivated inbred varieties of tobacco, the variance in leaf number per plant in the F<sub>1</sub> generation is 1.46 and in the F<sub>2</sub> generation it is 5.97. What are the genotypic and environmental variances? What is the broad-sense heritability in leaf number?

$V_{p}$ = $V_{g}$ + $V_{e}$
F1: $V_{e}$ = 1.46 (first gen has no genetic varience)

F2: $V_{p}$ = 5.97 (due to having both $V_{e}$ and $V_{g}$)
5.97 = $V_{g}$ + 1.46
$V_{g}$ = 5.97 - 1.46 --> $V_{g}$ = 4.51

broad sense: $H_{b}$ = $\frac{$V_{g}$}{$V_{p}$}$
$H_{b}$ = 4.51/5.97 --> $H_{b}$ = 0.75













