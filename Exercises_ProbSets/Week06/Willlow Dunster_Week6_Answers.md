# Willlow Dunster
#### Week 6 Problem Set
#### Bio 594
#### 28 February 2024

## 1. 
Q: The fly *Eurosta solidaginis* forms galls (enlarged areas) on goldenrod plants within which the fly larvae feed and develop.  A studoy of allozyme frequencies in 21 subpopulations of *E. solidaginis* on two different speices of goldenrod distributed from Minnesota to Maine (Waring et al. 1990) produced the following estimates of *F<sub>ST</sub>*:

|Locus | *F<sub>ST</sub>* |
|------|------------------|
| *GAP-1*| 0.10|
| *TPI-1*| 0.11|
| *IDH-1*| 0.02|
| *HBDH-1*| 0.62|
| *GPD-1*| 0.11|
| *PGM-1*| 0.14|

Calculate the expected number of migrants per generation for each locus.  What is your interpretation of these data?  Do you think the differentiation at these loci is caused soley by a balance between migration and drift?  Why or why not?

Island Model of migration for finite number of sub populations 

$a = (\frac{n}{n-1})^2$

$F_{ST} = (\frac{1}{4mNa+1})$

where mN = number of migrants 

Solve for a with n subpops

$a = (\frac{12}{12-1})^2$
= 1.19

Solve for mN

$F_{ST} = (\frac{1}{4mNa+1})$

$mN = \frac{1-F_{ST}}{4F_{ST}a}$


|Locus | *F<sub>ST</sub>* | nM |
|------|------------------|----| 
| *GAP-1*| 0.10| 1.89 |
| *TPI-1*| 0.11| 1.70 |
| *IDH-1*| 0.02| 10.29 |
| *HBDH-1*| 0.62| 0.13 |
| *GPD-1*| 0.11| 1.70 |
| *PGM-1*| 0.14| 1.29 |

I do not know how to interpret this data with regards to differentation 


* Most of the differentiation at *HBDH-1* show in the data occurs btween the two species of host plants; nine of the subpopulations occured on *Solidago altissima* and the other 12 subpops were on *S. gigantean*.  The frequency of one of the two *HBDH* alleles is 0.84 on *S. altissima* and 0.13 on *S. gigantea*.  How does this affect your interpretation of the results?

## 2. 
Q: Levin (1978) studied allele frequencies at the 6-pgd allozyme locus in 73 sub-populations of the self-incompatible species Phlox drummondi. Of these 73 subpopulations,66 were fixed for the a allele, with allele frequencies and observed heterozygosities at the other loci given below (Levin's original subpopulation numbering altered for simplicity):

Calculate the three F-statistics for these data and check to make sure they have the correct mathematical relationship. Do these comparisons fit your expectations based on the mating systems of this species? Why or why not? If not, do you have a possible explanation for the lack of fit?

$H_I=\frac{\sum_{i=1}^n H_O}{n}$
$ = \frac{(66*0)+ 0.06 +  0.12 + 0.2 + 0.03 +0.09 + 0.15 + 0.06}{73}$
$ =0.01 $

$H_S = \frac{\sum_{i=1}^n 2p_iq_i}{n}$
$ = \frac{\sum_{i=1}^n 2p_i(1-p_i)}{n}$
$ = \frac{(66*0)+ 0.24 +  0.32+ 0.42 + 0.08 +0.08 + 0.4 + 0.16}{73}$
$ = 0.0232$

$H_T=2\overline{p}*\overline{q}$
$ = 2(0.985)(0.015)
$ = 0.03$

$F_{IS} = 1 - \frac{H_I}{H_S}$
$ = -0.58 $ 

$F_{ST} = 1 - \frac{H_S}{H_T}$
$ = 0.22$

$F_{IT} = 1 - \frac{H_I}{H_T}$
$ = 0.67$ 

I don't think I understand how to interpret these results 
$F_{IS}$ is close to -1 so it suggests inbreeding and increased homozygosity. $F{_ST}$ is not close to 1 so there should be a good amount of migration. 


Calculate Nem from these data. If the migration rate m was found to be 0.1, what would the estimate of Ne be?

$mN = \frac{1-F_{ST}}{4F_{ST}}$
$ = 0.91$

$ m = 0.1$ 
$ N_e = \frac{mN}{m}$
$ = 9.1

Now assume that Ne is very large, 6-pgd is neutral in these subpopulations, and the migration rate is still O.1. What would the frequencies of the a allele in subpopulations 68 and 69 after 10 generations be? After 25 gener-ations? What biological principle is illustrated by these results?

$p_{t} = \bar{p} + (p_{0} - \bar{p})(1 - m)^t$

68 

$p_{10} = 0.985 + (0.8 - 0.985)(1 - 0.1)^10$
$ = 0.92$

$p_{25} = 0.985 + (0.8 - 0.985)(1 - 0.1)^25$
$= 0.97$

69
$p_{10} = 0.985 + (0.7 - 0.985)(1 - 0.1)^10$
$ = 0.88$

$p_{25} = 0.985 + (0.7 - 0.985)(1 - 0.1)^25$
$ = 0.96$

I do not know what principles is illustrated. 
pwd

## 3.
Q: In *D. melanogaster*, curly wings is due to a dominant allele C<sub>*y*</sub> that is lethal when homozygous. A population is established with an initial frequency of C<sub>*y*</sub> equal to 0.168. Calculate the expected frequency in the next generation, assuming.
      * The relative fitness of +/+ : C<sub>*y*</sub>/+ is 1:1.
      * The relative fitness of +/+ : C<sub>*y*</sub>/+ is 1:0.5.

Allele freq for the next generation 

$p^p = \frac{p^2 w_{11} + pqw_{12}}{p^2w_{11}+2pqw_{12}+q^2w_{22}}$

if p = 0.168

   q = 1-0.168 
    = 0.832

A. The relative fitness of +/+ : C<sub>*y*</sub>/+ is 1:1.

$w_{11} = 0$ because lethal 

$w_{12} = w_{22}$ = 1

$p^p = \frac{0 + 0.14(1)}{0 + 0.28(1)+0.832^2(1)}$
$ = 0.144$

B. The relative fitness of +/+ : C<sub>*y*</sub>/+ is 1:0.5.

$w_{11} = 0$ because lethal 

$w_{12} = 0.5* w_{22}$ 

$w_{22} = 1$ 
$p^p = \frac{0 + 0.14(0.5)}{0 + 0.28(0.5)+0.832^2(1)}$
$ = 0.084$

## 4. 
Q: If the fitnesses of the genotypes A1A1, A1A2, and A2A2 are 1.5, 1.1, and 1.0, respectively, what are the values of the selection coefficient and the heterozygous effect?

$ s = 1-w $
where w is the relative fitness 

$S_{A_{1}A_{1}} = 1-(1.5/1.5) = 0.000 $

$S_{A_{1}A_{2}} = 1-(1.1/1.5) = 0.267 $

$S_{A_{2}A_{2}} = 1-(1/1.5) = 0.333 $

heterozygous effect = $w_{A1}w_{A2} = 1-hs$

$h = \frac{(1 - w_{A1}w_{A2})}{s}$

$h = \frac{1-0.733}{0.33}$
$ = 0.8 $

## 5 
Q: Industrial melanism refers to the dark pigmentation that evolved in some insects, giving them protective coloration on vegetation darkened by soot in heavily industrialized areas prior to the requirement for smokestack filtration. In one heavily polluted area near Birmingham, England in 1956, 87% of moths of the species Biston betularia had black bodies due to the presence of a dominant gene for melanism (Kettlewell 1956). Estimate the frequency of the dominant allele in this population and the frequency of melanics that are heterozygous.

melanism = $ p^2 $ and $2pq $

non melanism = $ q^2$

$p^2 + 2pq = 0.87$

$q^2 = 1-0.87 = 0.13$

$q = sqrt(0.13) = 0.361$ freq of recessive allele 

$p = 1 - q = 0.639$ freq of dominant allele 

heterozygotes $= 2pq = 2(0.361)(0.639) = 0.461$


In this species, the frequency of melanic moths increased from a value of 1% in 1848 to a value of 95% in 1898. The species has one generation per year.
Estimate the approximate value of the selection coeffecient s against non-melanics that would be necessary to account for the change in the frequency of the melanic forms.
How many generations would be required for the same change in frequency of melanic forms in a hypothetical case in which the allele for melanism is recessive, assuming the same value of s against nonmelanics

Want the s against non melanics so have to find q 

$q^2_{50} = 1-0.95$

$q_{50} = sqrt(0.05) = 0.224$

$q^2_{0} = 1 - 0.01$

$q_{0} = sqrt(0.99) = 0.995$

Change in freq for favored dominant allele 
$st = ln \frac{pt}{qt} + \frac{1}{qt} - ln \frac{po}{qo}-\frac{1}{qo}$

$st = ln \frac{0.776}{0.224} + \frac{1}{0.224} - ln \frac{0.005}{0.995} - \frac{1}{0.995}$

$st = 12.005 $

$s = \frac{12.005}{50} = 0.2401$ 

if the allele was recessive swap p and q 
$ p^2_{0}= 0.01$
$ p_{0} = 0.1

$ p_{50} = 0.9747$

favored recessive allele 

$st = ln \frac{pt}{qt} + \frac{1}{pt} - ln \frac{po}{qo}-\frac{1}{po}$

$st = 16.874$

$t = \frac{16.874}{0.2401} = 70.28 generations $

## 6. 
Q Experimental populations of Drosophila pseudoobscura were established and periodically treated with weak doses of the insecticide DDT (Anderson et al. 1968). One population was initially polymorphic for five different inversions in the third chromosome, in approximately equal frequencies. After 13 generations, three of the inversions had disappeared from the population. The two that remained were Standard (ST) and Arrowhead (AR). Changes in frequencv of each inversion were monitored, and from the values for the first nine generations the relative fitnesses of ST/ST, ST/AR, and AR/AR genotypes were estimated as 0.47, 1.0, and 0.62, respectively. Because the inversions yield almost no recombinant gametes, each type can be considered as an "allele " What equilibrium frequency of ST is predicted? What equilibrium value of 
 is predicted?

 s = 1-w

 $s_{1} = 1-0.47$
 $= 0.53

 $s_{2} = 1-0.62$
 $ = 0.38

 $p^* = \frac{s_{2}}{s_{1}+s_{2}}$
 $ = 00.42 $

 I don't know how to calculate wbar for an equilibrium? 





