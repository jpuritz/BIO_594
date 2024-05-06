Final Project for BIO 594
================

## GitHub Documents

This is an R Markdown format used for publishing markdown documents to
GitHub. When you click the **Knit** button all R code chunks are run and
a markdown file (.md) suitable for publishing to GitHub is generated.

# Data setup

- Population: 12 populations from 5 different localities (10 near sewage
  effluent sources, 2 controls)

- The sequenced data files are located on KITT and can be accessed via

  PATH: `/home/BIO594/Final_Project`

- Size: 376 individuals (28-33 per population), 150bp sequences

- Sequences were previously demultiplexed with barcodes and individuals
  from a different species were removed (completed by Dr. Jon Puritz)

# Bioinformatics

## Initial Raw Data Assessment and Characterization (Jon)

- Count the RAW reads
- Examine quality of data (fastqc)

## Reference assembly (Cass)

- De Novo Reference Assembly
  - Include optimization
  - Assemble only a subset of individuals

## RADSeq Bioinformatics (Caitlin)

- Trimming adapters and low quality reads (fastp via dDocent)
- Read Mapping (BWA & SAMtools via dDocent)
  - Try using different mappaing parameters on a subset and pick the
    best ones
- SNP calling and filtering (FreeBayes via dDocent)

## SNP Filtering (VCFtools, vcflib, rad_haplotyper) (Willow)

# Population-level Analyses

## Detecting Selection Via Outlier Detection Programs (Flow and Michelle)

      * RDA 
      * Bayenv2
      * PCAadapt
      * Outflank

## Detecting Population Structure (Brittany and Angela)

      * Pairwise *F~ST~*
      * Genetic diversity (observed and expected heterozygosity)
      * EEMS (https://www.nature.com/articles/ng.3464)
