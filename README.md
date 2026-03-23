# BINF-6110-Assign3

## Introduction

## Methods

Shotgun metagenomic sequencing data were obtained from publicly available datasets derived from studies investigating the relationship between diet and gut microbiome composition (Filippis et al., 2019). These datasets include samples from individuals with different habitual diets, including omnivores and vegans, allowing for comparative microbiome analysis.

Raw sequencing reads were downloaded using SRA Toolkit (v3.0.9) (SRA Toolkit Development Team, n.d.) with prefetch, followed by conversion to FASTQ format using fasterq-dump. Paired-end reads were retained for downstream analysis.

Taxonomic classification was performed using Kraken2 (v2.1.6) (Wood et al., 2019) with a standard reference database (Standard-8). Reads were processed in paired-end mode with default parameters using four computational threads. Kraken2 assigns reads based on exact k-mer matches, enabling fast classification; however, its performance depends on database completeness, and unclassified reads may represent novel or underrepresented taxa (Wood et al., 2019).

Kraken2 report files were imported into R (v4.5.1) for downstream analysis. Data processing and visualization were performed using the tidyverse package collection, including ggplot2, dplyr, and tidyr (Wickham et al., 2019). Taxa were aggregated at the genus level, and relative abundances were calculated by normalizing read counts within each sample. Low-abundance taxa were grouped into an “Other” category to improve visualization clarity.

Alpha diversity was calculated using the Shannon index with the vegan package (Oksanen et al., 2001), which accounts for both richness and evenness. Differences between dietary groups were assessed using a Wilcoxon rank-sum test. Beta diversity was evaluated using Bray-Curtis dissimilarity and visualized using principal coordinates analysis (PCoA). Differential abundance was assessed by calculating log2 fold changes in mean relative abundance between groups. Due to limited sample size, differential abundance results were interpreted as exploratory rather than statistically conclusive.

## Results

**Figure 1.** Genus-level taxonomic composition of gut microbiome samples from omnivore and vegan groups. Relative abundance of dominant genera is shown for each sample, illustrating substantial inter-individual variability within and between dietary groups.

Genus-level taxonomic composition revealed substantial inter-individual variability within both dietary groups (Figure 1). Dominant genera such as *Segatella*, *Faecalibacterium*, and *Bacteroides* were observed across samples; however, their relative abundances varied considerably. While certain taxa appeared more prominent in specific samples, no consistent genus-level pattern clearly distinguished omnivore from vegan groups, indicating that microbial composition is highly heterogeneous.


**Figure 2.** Alpha diversity (Shannon index) of gut microbiome samples in omnivore and vegan groups. Each point represents an individual sample, and boxplots summarize group distributions. No statistically significant difference was observed between groups.

Alpha diversity analysis showed a trend toward higher Shannon diversity in omnivore samples compared to vegan samples (Figure 2). Omnivore samples also exhibited greater variability in diversity values, whereas vegan samples appeared more tightly clustered. However, this difference was not statistically significant (Wilcoxon rank-sum test: W = 19, p = 0.2222), suggesting that the observed trend does not represent a consistent difference between dietary groups.


**Figure 3.** Beta diversity of gut microbiome samples visualized by principal coordinates analysis (PCoA) based on Bray–Curtis dissimilarity. Each point represents a sample colored by dietary group, showing substantial overlap between groups.

Beta diversity analysis using PCoA based on Bray-Curtis dissimilarity did not reveal clear separation between omnivore and vegan samples (Figure 3). Samples from both groups overlapped substantially in ordination space, indicating that overall community composition is not strongly structured by diet. Instead, variation between individuals appears to be the dominant driver of community differences.


**Figure 4.** Differential abundance of genera between omnivore and vegan groups, shown as log2 fold change. Positive values indicate higher abundance in omnivore samples, while negative values indicate higher abundance in vegan samples. Differences were modest and not consistently observed across samples.

Differential abundance analysis identified several genera with differences in relative abundance between dietary groups (Figure 4). Genera such as *Agathobacter*, *Faecalibacterium*, and *Bifidobacterium* showed relatively higher abundance in omnivore samples, whereas *Akkermansia* and *Blautia* were more abundant in vegan samples. However, these differences were modest in magnitude and not consistently observed across all samples, suggesting that diet-associated effects at the genus level are limited in this dataset.


