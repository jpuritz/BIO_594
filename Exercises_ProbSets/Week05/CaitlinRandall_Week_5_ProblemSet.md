# Problem Set 2
## Due 2/29/2024

### Instructions

* Please answer all questions using a Mardown or RMarkdown, showing all work.
* Please place your files in this same directory in the format of `YourName_Week5_Answers.md`
* Problem sets can be worked on collaboratively, but please note who you worked with in your answer document



## Problems

1.  What is the probability that a particular allele has at least one copy in the next generation?  The surprising answer quickly becomes independent of population size as *N* becomes larger.  (Hint: Use one minus the probability that the allele has no copies in the next generation and this equation: $\lim\limits_{\varepsilon \to \infty}(1+\varepsilon*x)^\frac{1}{\varepsilon} = e^x$)

2.  A highly isolation colony of the month *Panaxia dominula* near Oxford, England has been instenstively studied by Ford and collaborators over the period of 1928-1968 (Ford and Sheppard 1969).  This speices has one generation per year, and estimates of the population size were caried out yearly begnining in 1941.  For the years 1950-1961, inclusive, estimates of the population size were: 

|Year| Individuals|
|------|----------|
| 1950 | 4100 |
| 1951 | 2250 |
| 1952 | 6000 |
| 1953 | 8000 |
| 1954 | 11000 |
| 1955 | 2000 |
| 1956 | 11000 |
| 1957 | 16000 |
| 1958 | 15000 |
| 1959 | 7000 |
| 1960 | 2500 |
| 1961 | 1400 | 
   * Assuming that the actual size of the population in any year equals the effective population size in that year, estimate the average effective number over the entire 12-year period.
   
   Ne = t/(summation (1/Ni))
   Ne = 12/ (1/4100 + 1/2250 + 1/6000 + 1/8000 + 1/11000 + 1/2000 + 1/11000 + 1/16000 + 1/15000 + 1/7000 + 1/2500 + 1/1400) = 3936.825

3.  A dairy farmer has a herd consisting of 200 cows and 2 bulls.  What is the effective population size?

Nm = 2 
Nf = 200 

Ne = 4(Nf)(Nm)/(Nf + Nm) 
   = 4 (200)(2)/(200+2)
   = 1600 / 202 
   = 7.9207
   
  


4.  A rare triggerplant from Australia (*Stylidium coroniforme*) has only five known populations (Coates 1992).  One of these populations has been monitored for several years, and over five years in the early 1980s: 2, 3, 25, 32, and 86 plants were recoreded.  Assuming *N<sub>e</sub>* = *N<sub>c</sub>* in that year, estimate *N<sub>e</sub>* as well as the average *N<sub>c</sub>* over this period.  What biological principle is illustrated by this example?

Ne = t/(summation(1/Ni))
Ne = 5/(1/2 + 1/3 + 1/25 + 1/32 + 1/86) 
Ne = 5.457 

average Nc = 2 + 3 + 25 + 32 + 86 / 5 = 29.6 

5.  You genotype a species of grasshopper along a transect in the European Alsp.  Near Munich, Germany, you sample 120 individuals; near Inssbruck, Austria, you sample 122 individuals;  near Verona, Italy you sample 118 individuals.  You find the following genotypes:

| Locality| A<sub>1</sub>A<sub>1</sub> | A<sub>1</sub>A<sub>2</sub> | A<sub>2</sub>A<sub>2</sub>|
|---------|--------------|---------|---------|
|Munich| 6|33|81|
|Innsbruck| 20|59|43|
|Verona|65|39|14|

* Calculate the frequencies of the two alleles in each population

Munich: 
A1 frequency = (2(6) + 33)/(2)(120)
= 45/240 = 0.1875
A2 frequency = 0.8125 

Innsbruck:
A1 frequency = (2(20) + 59)/(2)(122) 
= 99/244 = 0.4057 
A2 frequency = 0.5943 

Verona: 
A1 frequency = (2(65) + 39)/(2)(118) 
= 169/236 = 0.7161 
A2 frequency = 0.2839 

* Do any populations have excess heterozygotes?

Munich: 
expected heterozygosity: 2pq(N) = 2(0.1875)(0.8125)(120) = 36.5625 
observed heterozygotes: 33 

--> deficit in observed heterozygosity 

Innsbruck: 
expected heterozygotes: 2pqN = 2(0.4057)(0.5943)(122) = 58.83 
observed heterozygotes: 59 
--> due to rounding up to 59 whole individuals, there is not an excess or deficit of heterozygosity 

Verona: 
expected heterozygotes: 2pqN = 2(0.7161)(0.2839)(118) = 47.9789 
observed heterozygotes: 39 

--> deficit in observed heterozygosity  

* Do any populations have a deficit of heterozygotes?
see above 
* Calculate *F<sub>IS</sub>* for each of the populations and how does this related to B and C?
   * Hint: this the equation $F_{IS} = \frac{H_S - H_I}{H_S}$
   * I suggest looking it up, but you can likely figure it out from context