## Cassandra Cerasia
#### Week 5 Homework Problem Set 
#### February 29, 2024
## 1. 
Equation for the probability of the allele having no copies in the next generation: $(1-p)^{2N}$ where p = frequency of the allele

1 - this probability (as described in the hint): $(1-(1-p)^{2N})$

This equation in limit form:  $\lim\limits_{N \to \infty}(1-(1-p)^{2N})$

Original limit given in question:  $\lim\limits_{\varepsilon \to \infty}(1+\varepsilon*x)^\frac{1}{\varepsilon} = e^x$)

For similarities between the two limits, $\varepsilon = \frac{1}{2N}$ for the exponent to be eual to 2N

In the limit, would then have $\lim\limits_{N \to \infty}(1+\frac{1}{2N}*x)^{2N} = e^x$

Here is where I am begining to have trouble. To get the limit close to $(1-(1-p)^{2N})$ (the original equation/goal), I  could set x = -2Np. This will give $\lim\limits_{N \to \infty}(1+\frac{1}{2N}*-2Np)^{2N} = e^{-2Np}$, and after simplification $\lim\limits_{N \to \infty}(1-p)^{2N}$, which is close to the original but is missing a -1. 

After trying multiple other substitutions for x that were worse than what I tried above, I settled on this and x would then equal -2NP. 

With  $\lim\limits_{N \to \infty}(1-p)^{2N} = e^{-2Np}$, as N approaches infinity, the probability that a particular allele as at least one copy in the next generation becomes $e^{-2Np}$. 
## 2. 
Equation for the average effective population size over generations (harmonic mean):
$N_e = \frac{1}{t}(\frac{1}{N_1}+\frac{1}{N_2}+\frac{1}{N_3}+...+\frac{1}{N_t})$

This can be simplified with some algebra as: 

$N_e = \frac{t}{\sum \frac{1}{N_i}}$

$N_e = \frac{12}{\frac{1}{4100}+\frac{1}{2250}+\frac{1}{6000}+\frac{1}{8000}+\frac{1}{11000}+\frac{1}{2000}+\frac{1}{11000}+\frac{1}{16000}+\frac{1}{15000}+\frac{1}{7000}+\frac{1}{2500}+\frac{1}{1400}}$

$N_e = \frac{12}{0.0030}$

$N_e = 3936.8$
## 3. 
Equation for the effective population size with unequal sex ratio: 

$\frac{1}{N_e} = \frac{1}{4N_f}+\frac{1}{4N_m}$

Which is more commonly represented as solving for effective population size as: 
$N_e = \frac{4 \cdot N_f \cdot N_m}{N_f+N_m}$

$N_e$ = Effective population size 

$N_f$ = Number of Females (200 cows)

$N_m$ = Number of Males (2 bulls)

$N_e = \frac{4 \cdot 200 \cdot 2}{200+2}$

$N_e = \frac{1600}{202}$

$N_e = 8$
## 4. 
Equation for the average effective population size over generations (harmonic mean):
$N_e = \frac{1}{t}(\frac{1}{N_1}+\frac{1}{N_2}+\frac{1}{N_3}+...+\frac{1}{N_t})$

This can be simplified with some algebra as: 

$N_e = \frac{t}{\sum \frac{1}{N_i}}$

$N_e = \frac{5}{\frac{1}{2}+\frac{1}{3}+\frac{1}{25}+\frac{1}{32}+\frac{1}{89}}$

$N_e = \frac{5}{0.9}$

$N_e = 5.56$

Census Population Size Over 5 Years=  
$\frac{2+3+25+32+86}{5}$ 

$\frac{148}{5}$ = 29

The biological principle of effective population size and its relation to census population size is illustrated in this example. This example supported the common finding that $N_e$ is typically less than $N_c$. $N_e$ can often decline without a decline in $N_c$, due to events such as a sudden increase in the variance of family size, in which case only a few families would contribute towards the next generation. This example would then reduce $N_e$ with no reduction in $N_c$.

## 5. 
#### Allele Frequencies: 
Allele Frequency = $\frac{(2 \cdot Number of Individuals Homozygotes) + Number of Heterozygotes}{2 \cdot Total Individuals}$
### Munich: 
#### A1: 
Allele Frequency A1 Munich = $\frac{(2 \cdot 6) + 33}{2 \cdot 120}$

Allele Frequency A1 Munich = $\frac{(12) + 33}{240}$

Allele Frequency A1 Munich = $\frac{45}{240}$

Allele Frequency A1 Munich = $0.2$
#### A2:
Allele Frequency A2 Munich = $\frac{(2 \cdot 81) + 33}{2 \cdot 120}$

Allele Frequency A2 Munich= $\frac{(162) + 33}{240}$

Allele Frequency A2 Munich = $\frac{195}{240}$

Allele Frequency A2 Munich = $0.81$
### Innsbruck: 
#### A1: 
Allele Frequency A1 Innsbruck= $\frac{(2 \cdot 20) + 59}{2 \cdot 122}$

Allele Frequency A1 Innsbruck= $\frac{(40) + 59}{244}$

Allele Frequency A1 Innsbruck= $\frac{99}{244}$

Allele Frequency A1 Innsbruck= $0.4$
#### A2:
Allele Frequency A2 Innsbruck= $\frac{(2 \cdot 43) + 59}{2 \cdot 122}$

Allele Frequency A2 Innsbruck= $\frac{(86) + 59}{244}$

Allele Frequency A2 Innsbruck= $\frac{145}{244}$

Allele Frequency A2 Innsbruck= $0.59$
### Verona
#### A1 :
Allele Frequency A1 Verona= $\frac{(2 \cdot 65) + 39}{2 \cdot 118}$

Allele Frequency A1 Verona= $\frac{(130) + 39}{236}$

Allele Frequency A1 Verona= $\frac{169}{236}$

Allele Frequency A1 Verona= $0.72$
#### A2:
Allele Frequency A2 Verona= $\frac{(2 \cdot 14) + 39}{2 \cdot 118}$

Allele Frequency A2 Verona= $\frac{(28) + 39}{236}$

Allele Frequency A2 Verona= $\frac{67}{236}$

Allele Frequency A2 Verona= $0.28$

### Munich Expected Heterozygosity

p = Frequency of $A_1$ = 0.2

q = Frequency of $A_2$ = 0.81


Expected Genotypic Frequency $A_1A_2$ = ${2pq}{\cdot Number of Individuals}$

Expected Genotypic Frequency $A_1A_2$ = ${2(0.2 \cdot0.81)}{\cdot 120}$

Expected Genotypic Frequency $A_1A_2$ = ${2(0.15)}{\cdot 120}$

Expected Genotypic Frequency $A_1A_2$ = ${0.30}{\cdot 120}$

Expected Genotypic Frequency $A_1A_2$ = $37$
### Innsbruck Expected Heterozygosity
p = Frequency of $A_1$ = 0.4

1 = Frequency of $A_2$ = 0.59

Expected Genotypic Frequency $A_1A_2$ = ${2pq}{\cdot Number of Individuals}$

Expected Genotypic Frequency $A_1A_2$ = ${2(0.4 \cdot0.59)}{\cdot 122}$

Expected Genotypic Frequency $A_1A_2$ = ${2(0.2)}{\cdot 122}$

Expected Genotypic Frequency $A_1A_2$ = ${0.5}{\cdot 122}$

Expected Genotypic Frequency $A_1A_2$ = $59$
### Verona Expected Heterozygosity
p = Frequency of $A_1$ = 0.72

1 = Frequency of $A_2$ = 0.28

Expected Genotypic Frequency $A_1A_2$ = ${2pq}{\cdot Number of Individuals}$

Expected Genotypic Frequency $A_1A_2$ = ${2(0.72 \cdot0.28)}{\cdot 118}$

Expected Genotypic Frequency $A_1A_2$ = ${2(0.20)}{\cdot 118}$

Expected Genotypic Frequency $A_1A_2$ = ${0.41}{\cdot 118}$

Expected Genotypic Frequency $A_1A_2$ = $48$

### Average Expected Heterozygosity:
Average Expected Heterozygosity $A_1A_2$ = $\frac {37+59+48}{3}$

Average Expected Heterozygosity $A_1A_2$ = $\frac {143}{3}$

Average Expected Heterozygosity $A_1A_2$ = $48$ = $H_s$

### Average Observed Heterozygosities 
Average Observed Heterozygosity = $\frac{Number Heterozygotes}{Number Populations}$

Average Observed Heterozygosity = $\frac{33+59+39}{3}$

Average Observed Heterozygosity = $\frac{131}{3}$

Average Observed Heterozygosity = $44$
### $F_{IS}$ for the whole population 
$F_{IS} = \frac{H_S - H_I}{H_S}$

$H_S$ = Average expected heterozygosity = 48 

$H_I$ = Average Observed Heterozygosity = 44

$F_{IS} = \frac{48 - 44}{48}$

$F_{IS} = \frac{4}{48}$

$F_{IS} = 0.083$
### $F_{IS}$ for Munich
$F_{IS} = \frac{H_S - H_I}{H_S}$

$H_S$ = Expected heterozygosity = 37

$H_I$ = Observed Heterozygosity = 33

$F_{IS} = \frac{37 - 33}{37}$

$F_{IS} = \frac{-4}{37}$

$F_{IS} = -0.11$ = excess of heterozygotes
### $F_{IS}$ for Innsbruck
$F_{IS} = \frac{H_S - H_I}{H_S}$

$H_S$ = Expected heterozygosity = 59

$H_I$ = Observed Heterozygosity = 59

$F_{IS} = \frac{59 - 59}{59}$

$F_{IS} = \frac{0}{59}$

$F_{IS} = 0$ = No excess or deficit of heterozygotes or homozygotes 
### $F_{IS}$ for Verona
$F_{IS} = \frac{H_S - H_I}{H_S}$

$H_S$ = Expected heterozygosity = 48

$H_I$ = Observed Heterozygosity = 39

$F_{IS} = \frac{48 - 39}{48}$

$F_{IS} = \frac{9}{48}$

$F_{IS} = 0.19$ = Excess of homozygoes

The Munich population has excess heterozygotes. The Verona population has a deficit of homozygotes. $F_{IS}$ relates to question B and C as it is the way to calculate what populations have an excess or deficit of homozygotes or heterozygotes. $F_{IS}<0$ indicates an excess of heterozygotes, and $F_{IS}>0$ indicates and excess of homozygotes. $F_{IS}$ is calculated by the equation $F_{IS} = \frac{H_S - H_I}{H_S}$ where $H_S$ represents expected heterozygosity and $H_I$ represnts observed heterozygosity. If you were to calculate $F_{IS}$ across different subpopulations, the only change would be that $H_S$ would represent the average expected heterozygosity across the subpopulations and $H_I$ would represnt the average observed heterozygosity across the subpopulations.

