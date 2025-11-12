# Cell-Size-Dependent Transcriptomic Regulation in *Saccharomyces cerevisiae*

**Author:** Hans B. Liu  
**Supervision:** Matthew Swaffer, Center for Cell Biology, University of Edinburgh 
**Languages:** R (≥ 4.3) 
**Core packages:** tidyverse, DESeq2, mitch, ggplot2, pheatmap, VennDiagram  

---

## Project Overview
This repository contains a curated subset of the code used in my MSc Bioinformatics dissertation titled *“Examination of transcription factor-regulated gene expression changes with cell size in yeast.”*  
The analysis integrates transcriptomic slopes derived from four RNA-seq datasets with transcription-factor (TF) binding and regulation information to uncover how gene expression scales with cell size before and after removing growth rate effects.

---

## Data Sources
The data analysed in this project are dreived from the following published studies:
1. **Swaffer, M.P. et al. (2023).** RNA polymerase II dynamics and mRNA stability feedback scale mRNA amounts with cell size.  
  *Cell* **186**(24): 5254–5268.e26. (PMID: 37944513)  
2. **Lanz, M.C. et al. (2024).** Genome dilution by cell growth drives starvation-like proteome remodeling in mammalian and yeast cells.  
  *Nature Structural & Molecular Biology* **31**(12): 1859–1871. (PMID: 39048803)  
3. **Mahendrawada, L. et al. (2025).** Low overlap of transcription factor DNA binding and regulatory targets.  
  *Nature* **642**(8068): 796–804. (PMID: 40240607)  
4. **Huber, A. et al. (2011).** Sch9 regulates ribosome biogenesis via Stb3, Dot6 and Tod6 and the histone deacetylase complex RPD3L.  
  *EMBO Journal* **30**(15): 3052–3064. (PMID: 21730963)

---

## Analytical Pipeline
Main computational steps implemented as RMarkdown workflows:

1. **mRNA slope import & combination** – integrates slopes from four datasets.  
2. **Growth Rate Signature Removal** – uses linear regression and growth rate annotations to obtain slope residuals.  
3. **Wilcoxon Tests (VP script)** – compares slope distributions between TF-associated genes and the remaining genes, producing cumulative frequency distribution plots and volcano plots.  
4. **2D Annotation Enrichment (EA script)** – uses `mitch` to calculate S-scores and adjusted p-values, producing enrichment scatter plots and heatmaps.  
5. **Integration & Visualization** – generates Venn diagrams and summary tables highlighting TF gene groups which exhibit a biased scaling behaviour.

All scripts are organised to use relative paths and deposit outputs in `results/figures` and `results/tables`.

---

