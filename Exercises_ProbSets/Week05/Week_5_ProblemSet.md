# Week 5 problem set answers

1.  What is the probability that a particular allele has at least one copy in the next generation?  The surprising answer quickly becomes independent of population size as *N* becomes larger.  (Hint: Use one minus the probability that the allele has no copies in the next generation and this equation: $\lim\limits_{\varepsilon \to \infty}(1+\varepsilon*x)^\frac{1}{\varepsilon} = e^x$)

probability that allele doesn't get passed on for an individual: $(1 - $\frac{1}{2}$N)^2$ 

probability for entire population: 1 - $(1 - $\frac{1}{2}$N)^2$




2.  A highly isolation colony of the month *Panaxia dominula* near Oxford, England has been instenstively studied by Ford and collaborators over the period of 1928-1968 (Ford and Sheppard 1969).  This speices has one generation per year, and estimates of the population size were caried out yearly begnining in 1941.  For the years 1950-1961, inclusive, estimates of the population size were: 

|Year| Individuals|
|------|----------|
| 1950 | 4100 |  0.0002439
| 1951 | 2250 |  0.00044444
| 1952 | 6000 |  0.00016667
| 1953 | 8000 |  0.000125
| 1954 | 11000 |  0.00009091
| 1955 | 2000 |  0.0005
| 1956 | 11000 |  0.00009091
| 1957 | 16000 |  0.0000625
| 1958 | 15000 |  0.00006667
| 1959 | 7000 |  0.00014286
| 1960 | 2500 |  0.0004
| 1961 | 1400 |   0.00071429
   * Assuming that the actual size of the population in any year equals the effective population size in that year, estimate the average effective number over the entire 12-year period.
   
   $N_{e}$ = $\frac{t}{$Sigma$ $\frac{1}{$N_{i}$}$}$
   
   $N_{e}$ = $\frac{12}{0.00304}$
   
   $N_{e}$ = 3947.37
   

3.  A dairy farmer has a herd consisting of 200 cows and 2 bulls.  What is the effective population size?

  $N_{e}$ = $\frac{4$N_{f}$$N_{m}$}{$N_{f}$$N_{m}$}$
  $N_{e}$ = $\frac {1600} {202}$
  $N_{e}$ = 7.92
  
4.  A rare triggerplant from Australia (*Stylidium coroniforme*) has only five known populations (Coates 1992).  One of these populations has been monitored for several years, and over five years in the early 1980s: 2, 3, 25, 32, and 86 plants were recoreded.  Assuming *N<sub>e</sub>* = *N<sub>c</sub>* in that year, estimate *N<sub>e</sub>* as well as the average *N<sub>c</sub>* over this period.  What biological principle is illustrated by this example?

  This is example is illustrating the concept of harmonic mean.
  
  $N_{e}$ = $\frac{t}{sum$\frac{1}{$N_{i}$}$}$
  $N_{e}$ = $\frac{5}{0.916}$ --> 5.457
  Average $N_{c}$ over 5 years: $\frac{2+3+25+32+86}{5}$ --> 29.6

5.  You genotyep a species of grasshopper along a transect in the European Alsp.  Near Munich, Germany, you sample 120 individuals; near Inssbruck, Austria, you sample 122 individuals;  near Verona, Italy you sample 118 individuals.  You find the following genotypes:

| Locality| A<sub>1</sub>A<sub>1</sub> | A<sub>1</sub>A<sub>2</sub> | A<sub>2</sub>A<sub>2</sub>|
|---------|--------------|---------|---------|
|Munich| 6|33|81|
|Innsbruck| 20|59|43|
|Verona|65|39|14|

* Calculate the frequencies of the two alleles in each population
* Do any populations have excess heterozygotes?
* Do any populations have a deficit of heterozygotes?
* Calculate *F<sub>IS</sub>* for each of the populations and how does this related to B and C?
   * Hint: this the equation $F_{IS} = \frac{H_S - H_I}{H_S}$
   * I suggest looking it up, but you can likely figure it out from context
   
   