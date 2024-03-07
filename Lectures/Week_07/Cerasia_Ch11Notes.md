## Cassandra Cerasia - Scribe
## Chapter 11 Quantitative Genetics 
### Polygenic
* Quantitative traits typically involve many genes
* Environment also has an effect on this
* Chapter goes over:
    * Genetic variation in quantitative traits 
    * Phenotypic variation 
    * How we can use these in models to explore natural population 
### Heritability 
* Quantitative traits include phenotypes that consist of continuous distributions 
* Although a lot of qualitative traitsa are polygenic, we don't know how many genes are involved from distribution of phenotypes 

Equation 11.1 and 11.2

$V_a$ = Additive effects

$V_d$ = Dominance efftects 

$V_I$ = epistatic effects - interaction across multiple loci from chapter 10. Could be no interaciton or a lot of interaciton 
Above is a cocneptual and quantitative framework
* Phenotype is an expression of environment and genetics - nature and nurture 
* This can be broken down more with equation 11.2
* Once you get to a bunch of loci there is a more normal distribution and it is difficult to tell what is affecting a trait 
### Broad Sense Heritability 
* The proportion of phenotypic variaility that results from genetic difference among individuals 

Equation 11.3
 ### Narrow Sense Heritability 
 * Predicts the response of a trait to selection 
 * More commonly used than broad-sense - in broad-sense, the prediction is not always great
 $H_N$ is the proportion of total phenotypic variation that is due only to additive genetic variation among 
 individuals. 

Equation 11.4

 * Predicts the response of a trait to selection 
 * If H=1, completely heritable. Offspring look like parents 
 * If H=0, no heritability. Offspring go to mean of distribution

Figure 11.2

* S is difference between mean and quantitative trait you want to breed for 
* If all genetic variation is additive, then broad sense and narrow sense would be equal. 
* Papers typically discuss Narrow Sense. It is difficult to to Broad Sense. 
### Estimating Heritability 
* Can be used to estimate narrow sense 


* In figure 11.3, when slope was multiplied by two, this was used to estimate heritability 

* Progeny testing estimated breeding value of parents with phenotypic similarities between hald or full offsprings 
* Example: Collect plans from outcrossing species. Seeds will have same mother but different father (1/2 sibs sharign 1/4 of genes from mother). $V_F$ Would be a quartre of additive variation as shown in equation. 
* Equation can be bias as it assumes half sibs. Could be not genetic aspects influencing phenotypic traits. 
### Genotype by environment interactions 
* We know the environment plays a role in the fitness of an organism
### Selection and Quantitative Traits 
* Narrow sense heritability can be estimated by an organism's response to selection 


* S = selction 
* R = response 
* It s 1/3 beacuse it is the realized heritability already, it is fixed (In this example)
* The distance from the population mean can be changed
* Heritability = $\frac{R}{S}$
* Typically, you don't know $H_N$
* If $H_N$ = 0, you cannot select for that

* If there is no response to directional selection, heritability would be 0.

### Heritabilities and Allele Frequencies 
* Allele frequences can change even if the encironment is the same 
* In a single locus model, we can calculate heritability 

Equation 11.11 -11.14

* w is for fitness
* p and q are allele frequencies 

### Genetic Correlations 
* Pliotrophy - a bunch of genes impact one effect 
* Where alleles at different loci are not random
* Figure 11.1
    * Good indicator for progeny phenotypes for pectoral rays 
* It is like you are inheriting one gene but it is affecting two traits 
    * Figure 11.11 shows two traits genetically correlated. Increased fitness for one trait cna increase fitness for another trait 
        * c and b has an antagonistic response 
        * Increase in fitness for one trait that causes a decrease in fitness for another trait 
        * More sporadically shown in c but look for the error
### Finding Genes Underlying Quantitative Traits 
* High throughput sequencing 
* Allows us to indentify genes, chromosomal regions, SNPs
* QTL Mapping is a way to look for genes associated with traits, but doesn't look for gene associated woth carrying variation. Does not look at whole genome. Looks for the neighboorhood of the genes associated with the phenotypic trait
    * QTL looks at phenotype in order to search for responsible genes
* Candidate gene approaches look for the specific house affecting the gene involved 
    * Starts with genes involved in phenotypic trait. Candidate genes are sequenced to indentify SNPs which are then genotyped to associate with enivronmental factors. This is associated as association mapping. 
* Genome-Wide Association Mapping (GWAS or "G-WAS")
    * Requires no knowledge of individual gene function 
    * Does require computational power and genomic resources 
### Loss of Quantitative Genetic Variation 
* Equation 11.16
    * Doesn't matter how this is derived 
    * For neutral loci, it is related to effective population size 
    * In the equation, we only estimate the addititive variance 
    * Only thing that plays into this is differences among phenotypes and whehter or not there is dominance
    * Jon says don't worry about this equation :) Rarely have all of the variables to work with this
    * If variance, is additive, d goes to 0 and equation gets shorter 
    * If there is dominance, equation gets a little more complicated 
    * There is no effective population size term in the equation 
* Figure 11.16
    * Reviews the limits of adaptive potential in small populations and estimated heritability 
    * Low levels of inbreeding and larger effective population size
    * Heritability is higher than the outbred control which suggests variation is being expressed 
### Effects of Selection 
* Alleles associated with increased fitness will increase until fixation 
* Figure 11. 17
    * Long term experiment that selects separate lines for high and low oil and protien content 
    * SHows a persistance of additive genetic variation 
### Divergence among populations
* Equation 11.17
    * $Q_{ST}$ is expected to be th esame as $F_{ST}$ if in HW proportions 
    * $F_{ST}$ came from fixation index 
    * $Q_{ST}$ is more difficult to estimate. Then we turn to $P_{ST}$ (Equation 11.18)
* Equation 11.18
    *Used to estimate proportion of phenotypica variation caused by adaptive differences in a population 
* Similar consruct of Fst
* Instead of heterozygosities, it looks at variances 
* Partitions variance of a subgroup over total population you see
* These used to be used a lot, but not os much these days 
### Quantitiative Genetics and Conservation 
* Allows for study of traits associated with fitness 
* Used to look at effects of anthropogenic climate change 
* A bit controversial with difficult to estimate parameters and error rates
* Equation 11.19 
* Equation 11.20
    * Often expressed as a percentage 
* Figure 11.21
    * Fisher's Fundamental theorem of natural selection 
### Response To Selection in the Wild 
* Example is the the pink salmon caught off North American Coast. Size had declined due to size selectiveness 
* Selection pressures fluctuate overtime and there are other genetic correlations possibly with the traits under selection 
### Can molecular genetic variation within populations estimate quantitative variation? 
* Yes with caution 
* Examples and predictions in book
    * Endangered bird - molecular variation supported their result but another study disproved it 
    * Bottlenecks have shown to increase heritibility and decrese in genetic adaptation 
### Does population divergence for molcular markers estimate divergence for quantitative traits?
* In the absense of quantitative genetic information the amount of molecular genetic variation between populations should be used carefully to make predictions about quantitative genetic variation 
* Different local populations almost always have different optimal phenotypic values. 
### Discussion 
* How would a bottleneck change heritability? 
    * Allele frequencies! 
* How do researchers determine what traits to study? Do they look at multiple populations and try to find visual differences or look at local adaptations? 
    * Maybe if you say a decrease in fitness because of a specific trait 
    * Lots of constriants over what is phenotyped for lots of organisms 
    * For plants its easy - they don't move, easy to measure, etc. 
    * Many organisms are not as cooperative 
    * Ability to assess phenotype matters - limited by technology and what you can measure 
    * People design studies with the hope they can find an effect - will look at things they hope will have an effect. You wouldn't look at traits you do not think will have an effect. 
    * You wouldn't bother phenotyping something you don't think is adaptive. 


