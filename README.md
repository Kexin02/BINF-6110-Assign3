# BINF-6110-Assign3

## Introduction

## Methods

Shotgun metagenomic sequencing data were obtained from publicly available datasets derived from studies investigating the relationship between diet and gut microbiome composition (Filippis et al., 2019). These datasets include samples from individuals with different habitual diets, including omnivores and vegans, allowing for comparative microbiome analysis.

Raw sequencing reads were downloaded using SRA Toolkit (v3.0.9) (SRA Toolkit Development Team, n.d.) with prefetch, followed by conversion to FASTQ format using fasterq-dump. Paired-end reads were retained for downstream analysis.

Taxonomic classification was performed using Kraken2 (v2.1.6) (Wood et al., 2019) with a standard reference database (Standard-8). Reads were processed in paired-end mode with default parameters using four computational threads. Kraken2 assigns reads based on exact k-mer matches, enabling fast classification; however, its performance depends on database completeness, and unclassified reads may represent novel or underrepresented taxa (Wood et al., 2019).

Kraken2 report files were imported into R (v4.5.1) for downstream analysis. Data processing and visualization were performed using the tidyverse package collection, including ggplot2, dplyr, and tidyr (Wickham et al., 2019). Taxa were aggregated at the genus level, and relative abundances were calculated by normalizing read counts within each sample. Low-abundance taxa were grouped into an “Other” category to improve visualization clarity.

Alpha diversity was calculated using the Shannon index with the vegan package (Oksanen et al., 2001), which accounts for both richness and evenness. Differences between dietary groups were assessed using a Wilcoxon rank-sum test. Beta diversity was evaluated using Bray-Curtis dissimilarity and visualized using principal coordinates analysis (PCoA). Differential abundance was assessed by calculating log2 fold changes in mean relative abundance between groups. Due to limited sample size, differential abundance results were interpreted as exploratory rather than statistically conclusive.

## 
