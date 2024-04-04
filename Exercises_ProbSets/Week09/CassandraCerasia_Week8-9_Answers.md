## Cassandra Cerasia
### Week 8/9 Homework Tutorial Set 
### April 4, 2024
## 1. 
Congratulations you have finished this exercise!!!!
 I highly recommend that you take the time to learn more about AWK!
 Please take a look at these websites as references:
 http://www.thegeekstuff.com/2010/01/awk-introduction-tutorial-7-awk-print-examples/
 http://www.grymoire.com/Unix/Awk.html
 ## 2. 
 * Oh me! Oh life! of the questions of these recurring,
Of the endless trains of the faithless, of cities fill’d with the foolish,
Of myself forever reproaching myself, (for who more foolish than I, and who more faithless?)
Of eyes that vainly crave the light, of the objects mean, of the struggle ever renew’d,
Of the poor results of all, of the plodding and sordid crowds I see around me,
Of the empty and useless years of the rest, with the rest me intertwined,
The question, O me! so sad, recurring—What good amid these, O me, O life?

                                       Answer.
That you are here—that life exists and identity,
That the powerful play goes on, and you may contribute a verse.

I did this with the line: cat BIO594/Exercises/sneaky/file.txt
* [ccerasia@KITT ~]$ awk '{print $3}' /home/BIO594/Exercises/Week_2/out.idepth | head -n 5

MEAN_DEPTH

19.7475

19.8769

20.2284

19.4391
* [ccerasia@KITT ~]$ awk 'NR==19 {print $2}' /home/BIO594/Exercises/Week_2/out.idepth

8428
*[ccerasia@KITT ~]$ awk '$3 > 20.1' /home/BIO594/Exercises/Week_2/out.idepth

INDV    N_SITES MEAN_DEPTH

PopA_03 8453    20.2284

PopA_05 8448    20.4425

PopA_08 8454    20.1047

PopA_09 8341    20.2223

PopA_13 8408    20.6407

PopA_20 8342    20.1082

PopB_07 8392    20.2092

PopB_08 8382    20.2733

PopB_09 8262    20.2642

PopB_14 8370    20.2419 
* [ccerasia@KITT ~]$ awk '$3 > 20.1 && $3 < 20.25 {print}' /home/BIO594/Exercises/Week_2/out.idepth | wc -l

6
* [ccerasia@KITT ~]$  awk '{sum=sum+$3} END {print sum/NR}' /home/BIO594/Exercises/Week_2/out.idepth

19.3738
* [ccerasia@KITT realdata]$ bwa mem reference.fasta JC_1119.R1.fq.gz JC_1119.R2.fq.gz -I 200,40 -t 3 -B 3 -O 5 -L 20,5 2>/dev/null | mawk '!/\t[2-9].[SH].*/' | mawk '!/[2-9].[SH]\t/'| samtools view -@16 -q 5 -SbT reference.fasta - | samtools flagstat - > relaxed.stats

[ccerasia@KITT realdata]$ bwa mem reference.fasta JC_1119.R1.fq.gz JC_1119.R2.fq.gz -I 200,40 -t 3 -L 20,5 2>/dev/null | mawk '!/\t[2-9].[SH].*/' | mawk '!/[2-9].[SH]\t/'| samtools view -@16 -q 5 -SbT reference.fasta - | samtools flagstat - > normal.stats

[ccerasia@KITT realdata]$ paste <(cut -f1 -d + relaxed.stats) <(cut -f1 -d + normal.stats) <(cut -f4-10 -d " " relaxed.stats)

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

* [ccerasia@KITT realdata]$ realdata]$ bwa mem reference.fasta JC_1119.R1.fq.gz JC_1119.R2.fq.gz -I 200,40 -t 3 -B 3 -O 5 -L 20,5 2>/dev/null | mawk '!/\t[2-9].[SH].*/' | mawk '!/[2-9].[SH]\t/'| samtools view -@16 -q 10 -SbT reference.fasta - | samtools flagstat - > relaxed.stats

[ccerasia@KITT realdata]$ bwa mem reference.fasta JC_1119.R1.fq.gz JC_1119.R2.fq.gz -I 200,40 -t 3 -L 20,5 2>/dev/null | mawk '!/\t[2-9].[SH].*/' | mawk '!/[2-9].[SH]\t/'| samtools view -@16 -q 10 -SbT reference.fasta - | samtools flagstat - > normal.stats

[ccerasia@KITT realdata]$ paste <(cut -f1 -d + relaxed.stats) <(cut -f1 -d + normal.stats) <(cut -f4-10 -d " " relaxed.stats)

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
