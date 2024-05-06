###BIO 594- Using genomic techniques to examine the evolution of populations ###

#### Exercise 3 - Map.Ex

Mapping Cut off at 5

	bwa mem reference.fasta JC_1119.R1.fq.gz JC_1119.R2.fq.gz -I 200,40 -t 8 2>/dev/null | samtools view -@8 -q 5 -SbT reference.fasta - | samtools flagstat -

```
#Output

2286501 + 0 in total (QC-passed reads + QC-failed reads)
2282816 + 0 primary
0 + 0 secondary
3685 + 0 supplementary
0 + 0 duplicates
0 + 0 primary duplicates
2286501 + 0 mapped (100.00% : N/A)
2282816 + 0 primary mapped (100.00% : N/A)
2282816 + 0 paired in sequencing
1159294 + 0 read1
1123522 + 0 read2
2141898 + 0 properly paired (93.83% : N/A)
2226598 + 0 with itself and mate mapped
56218 + 0 singletons (2.46% : N/A)
84387 + 0 with mate mapped to a different chr
84387 + 0 with mate mapped to a different chr (mapQ>=5)
```

	bwa mem reference.fasta JC_1119.R1.fq.gz JC_1119.R2.fq.gz -I 200,40 -t 8 -L 20,5 -B 3 -O 5 2>/dev/null | samtools view -@8 -q 5 -SbT reference.fasta - | samtools flagstat -

```
#Output
# Paired reads increased and singletons decreased as a result by relaxing the mismatch and gap opening penalties.

2283635 + 0 in total (QC-passed reads + QC-failed reads)
2281323 + 0 primary
0 + 0 secondary
2312 + 0 supplementary
0 + 0 duplicates
0 + 0 primary duplicates
2283635 + 0 mapped (100.00% : N/A)
2281323 + 0 primary mapped (100.00% : N/A)
2281323 + 0 paired in sequencing
1160621 + 0 read1
1120702 + 0 read2
2146130 + 0 properly paired (94.07% : N/A)
2226364 + 0 with itself and mate mapped
54959 + 0 singletons (2.41% : N/A)
79929 + 0 with mate mapped to a different chr
79929 + 0 with mate mapped to a different chr (mapQ>=5)
```

	bwa mem reference.fasta JC_1119.R1.fq.gz JC_1119.R2.fq.gz -I 200,40 -t 3 -B 3 -O 5 -L 20,5 2>/dev/null | mawk '!/\t[2-9].[SH].*/' | mawk '!/[2-9].[SH]\t/'| samtools view -@16 -q 5 -SbT reference.fasta - | samtools flagstat - > relaxed.stats
	bwa mem reference.fasta JC_1119.R1.fq.gz JC_1119.R2.fq.gz -I 200,40 -t 3 -L 20,5 2>/dev/null | mawk '!/\t[2-9].[SH].*/' | mawk '!/[2-9].[SH]\t/'| samtools view -@16 -q 5 -SbT reference.fasta - | samtools flagstat - > normal.stats
	paste <(cut -f1 -d + relaxed.stats) <(cut -f1 -d + normal.stats) <(cut -f4-10 -d " " relaxed.stats)

```
#Comparing the relaxed and unrelaxed results

2217934         2206471         in total (QC-passed reads + QC-failed reads)
2217934         2206471         primary
0       0       secondary
0       0       supplementary
0       0       duplicates
0       0       primary duplicates
2217934         2206471         mapped (100.00% : N/A)
2217934         2206471         primary mapped (100.00% : N/A)
2217934         2206471         paired in sequencing
1131358         1123539         read1
1086576         1082932         read2
2103108         2092133         properly paired (94.82% : N/A)
2169304         2157042         with itself and mate mapped
48630   49429   singletons (2.19% : N/A)
66004   64712   with mate mapped to a different chr
66004   64712   with mate mapped to a different chr
```
Mapping Cut off at 10

	bwa mem reference.fasta JC_1119.R1.fq.gz JC_1119.R2.fq.gz -I 200,40 -t 8 2>/dev/null | samtools view -@8 -q 10 -SbT reference.fasta - | samtools flagstat -

```
#Output
2269871 + 0 in total (QC-passed reads + QC-failed reads)
2266588 + 0 primary
0 + 0 secondary
3283 + 0 supplementary
0 + 0 duplicates
0 + 0 primary duplicates
2269871 + 0 mapped (100.00% : N/A)
2266588 + 0 primary mapped (100.00% : N/A)
2266588 + 0 paired in sequencing
1152390 + 0 read1
1114198 + 0 read2
2138505 + 0 properly paired (94.35% : N/A)
2213940 + 0 with itself and mate mapped
52648 + 0 singletons (2.32% : N/A)
75149 + 0 with mate mapped to a different chr
75149 + 0 with mate mapped to a different chr (mapQ>=5)
```

bwa mem reference.fasta JC_1119.R1.fq.gz JC_1119.R2.fq.gz -I 200,40 -t 8 -L 20,5 -B 3 -O 5 2>/dev/null | samtools view -@8 -q 10 -SbT reference.fasta - | samtools flagstat -

```
#Output
# Paired reads increased and singletons decreased as a result by relaxing the mismatch and gap opening penalties.

2263009 + 0 in total (QC-passed reads + QC-failed reads)
2261330 + 0 primary
0 + 0 secondary
1679 + 0 supplementary
0 + 0 duplicates
0 + 0 primary duplicates
2263009 + 0 mapped (100.00% : N/A)
2261330 + 0 primary mapped (100.00% : N/A)
2261330 + 0 paired in sequencing
1146393 + 0 read1
1114937 + 0 read2
2143521 + 0 properly paired (94.79% : N/A)
2212681 + 0 with itself and mate mapped
48649 + 0 singletons (2.15% : N/A)
68883 + 0 with mate mapped to a different chr
68883 + 0 with mate mapped to a different chr (mapQ>=5)
```

	bwa mem reference.fasta JC_1119.R1.fq.gz JC_1119.R2.fq.gz -I 200,40 -t 3 -B 3 -O 5 -L 20,5 2>/dev/null | mawk '!/\t[2-9].[SH].*/' | mawk '!/[2-9].[SH]\t/'| samtools view -@16 -q 10 -SbT reference.fasta - | samtools flagstat - > relaxed.stats
	bwa mem reference.fasta JC_1119.R1.fq.gz JC_1119.R2.fq.gz -I 200,40 -t 3 -L 20,5 2>/dev/null | mawk '!/\t[2-9].[SH].*/' | mawk '!/[2-9].[SH]\t/'| samtools view -@16 -q 10 -SbT reference.fasta - | samtools flagstat - > normal.stats
	paste <(cut -f1 -d + relaxed.stats) <(cut -f1 -d + normal.stats) <(cut -f4-10 -d " " relaxed.stats)

```
#Comparing the relaxed and unrelaxed results

2201764         2192629         in total (QC-passed reads + QC-failed reads)
2201764         2192629         primary
0       0       secondary
0       0       supplementary
0       0       duplicates
0       0       primary duplicates
2201764         2192629         mapped (100.00% : N/A)
2201764         2192629         primary mapped (100.00% : N/A)
2201764         2192629         paired in sequencing
1119342         1117075         read1
1082422         1075554         read2
2100814         2089604         properly paired (95.42% : N/A)
2157734         2147053         with itself and mate mapped
44030   45576   singletons (2.00% : N/A)
56754   57277   with mate mapped to a different chr
56754   57277   with mate mapped to a different chr
```

Mapping quality pattern holds true
