Final Project for BIO 594
================

# Let’s generate some data QC

Let’s start by making a directory on KITT

``` bash
mkdir -p /home/BIO594/Final_Project/QC
```

Second, I will create a conda environment

``` bash
mamba create -n QC ddocent fastqc multiqc
```

## Fastqc

Now, I will move into the directory and link the fastq files, activate
the environment and run `fastqc` in parallel

``` bash
cd /home/BIO594/Final_Project/QC
ln -s ../dDocent_working_dir/*.fq.gz .
mamba activate QC
ls *.fq.gz | parallel -j 16 "fastqc -t 4 {}"
```

Truncated output:

    Academic tradition requires you to cite works you base your article on.
    If you use programs that use GNU Parallel to process data for an article in a
    scientific publication, please cite:

      Tange, O. (2024, March 22). GNU Parallel 20240322 ('Sweden').
      Zenodo. https://doi.org/10.5281/zenodo.10901541

    This helps funding further development; AND IT WON'T COST YOU A CENT.
    If you pay 10000 EUR you should feel free to use GNU Parallel without citing.

    More about funding GNU Parallel and the citation notice:
    https://www.gnu.org/software/parallel/parallel_design.html#citation-notice

    To silence this citation notice: run 'parallel --citation' once.

    application/gzip
    Analysis complete for FBN_309.F.fq.gz
    Started analysis of FBN_309.F.fq.gz
    Approx 5% complete for FBN_309.F.fq.gz
    Approx 10% complete for FBN_309.F.fq.gz
    Approx 15% complete for FBN_309.F.fq.gz
    Approx 20% complete for FBN_309.F.fq.gz
    Approx 25% complete for FBN_309.F.fq.gz
    Approx 30% complete for FBN_309.F.fq.gz
    Approx 35% complete for FBN_309.F.fq.gz
    Approx 40% complete for FBN_309.F.fq.gz
    Approx 45% complete for FBN_309.F.fq.gz
    Approx 50% complete for FBN_309.F.fq.gz
    Approx 55% complete for FBN_309.F.fq.gz
    Approx 60% complete for FBN_309.F.fq.gz
    Approx 65% complete for FBN_309.F.fq.gz
    Approx 70% complete for FBN_309.F.fq.gz
    Approx 75% complete for FBN_309.F.fq.gz
    Approx 80% complete for FBN_309.F.fq.gz
    Approx 85% complete for FBN_309.F.fq.gz
    Approx 90% complete for FBN_309.F.fq.gz
    Approx 95% complete for FBN_309.F.fq.gz
    application/gzip
    Analysis complete for FBN_309.R1.fq.gz

## Multiqc

Next I will run [multiqc](https://multiqc.info/) to aggregate the qc
info.

``` bash
mamba activate QC
cd /home/BIO594/Final_Project/QC
multiqc .
```

      /// MultiQC 🔍 | v1.21

    |           multiqc | Search path : /home/BIO594/Final_Project/QC
    |         searching | ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 100% 4548/4548  
    |            fastqc | Found 1516 reports
    |           multiqc | Report      : multiqc_report.html
    |           multiqc | Data        : multiqc_data
    |           multiqc | MultiQC complete

Now, I will copy the multiqc report `multiqc.html` and the
`multiqc_data` directory to my BIO_594 Repository

``` bash
cp -r /home/BIO594/Final_Project/QC/multiqc* ~/repos/BIO_594/Final_Project
```

The mutliqc.json file is big, so we need to use [git
LFS](https://git-lfs.com/) to handle the file

``` bash
cd ~/repos/BIO_594/Final_Project
git pull
git lfs install
git lfs track "*.json"
git add .gitattributes
git commit -a -m "add LFS"
git push
```

Now, we can add the report and the data files

``` bash
git add multiqc_report.html
cd multiqc_data/
git add multiqc_data.json
git add *
git commit -m "add multiqc report"
git push
```

Now, the report and data files are accessible on github. To view the
full interactive report, download the `multiqc_report.html` file and the
whole `multiqc_data` directory and open the `multiqc_report.html` with a
web browser.

We can also export images of some of the data.

### Sequence Counts

![Sequence
Counts](./Collaborative_Final_Project_Part_1_RawData_QC_Jon_files/fastqc_sequence_counts_plot.png)
This shows a bar graph of the read counts per individual. This has raw
and trimmed reads in it. You can see that there is a large spread of
variance across samples. Also, for RADseq, don’t be alarmed by the
presenence of “duplicate reads” this is an approximation and has to do
with the fact that RADseq is only sampling at RAD loci. It is not a
random, shotgun sequencing approach.

### Sequence Quality

![Sequence
Quality](./Collaborative_Final_Project_Part_1_RawData_QC_Jon_files/fastqc_per_base_sequence_quality_plot.png)
This graph shows the mean quality at each position across the read. The
quality looks pretty good. Quality is lower at the front and end of the
sequence, but still within the green.

### Per Sequence Quality scores

![Sequence
Quality](./Collaborative_Final_Project_Part_1_RawData_QC_Jon_files/fastqc_per_sequence_quality_scores_plot.png)
This graph looks at the average quality scores per sequence. I ran this
on both raw and trimmed reads. They look good!

### Per Sequence GC Content

![Sequence
GC](./Collaborative_Final_Project_Part_1_RawData_QC_Jon_files/fastqc_per_sequence_gc_content_plot.png)
If all individuals are from the same species, then this graph will show
that the sequences are roughly normally distributed. It is possible that
there are individuals from another species mixed in. These individuals
(if any) will be identified using Principal Components Analysis (PCA).
