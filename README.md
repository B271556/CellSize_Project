# Cell-Size-Dependent Transcriptomic Regulation in *Saccharomyces cerevisiae*

# Cell-Size-Dependent Transcriptomic Regulation in *Saccharomyces cerevisiae*

| Field | Details |
|-------|----------|
| **Author** | Hans B. Liu |
| **Languages** | R 4.3.2  (RStudio 2025.05) |
| **Core packages** | tidyverse, mitch, ggplot2, pheatmap, VennDiagram |

**Author:** Hans B. Liu  
**Languages:** R (4.3.2) (RStudio 2025.05)  
**Core packages:** tidyverse, mitch, ggplot2, pheatmap, VennDiagram  

---

## Project Overview
This repository contains a curated subset of the code used in my MSc Bioinformatics dissertation titled *Examination of transcription factor-regulated gene expression changes with cell size in yeast.*  
There are approximately 150 known transcription factors (TFs) in the budding yeast *Saccharomyces cerevisiae*. Each TF binds to and/or regulates various genes. This project integrates mRNA expression derived from four RNA-seq datasets with TF binding and regulation information to uncover how the expression of genes associated with TFs scales with cell size. The analysis was done twice (before and after removing growth rate effects) in order to distinguish between expression changes associated with cell size from those associated with cellular growth rate. 

---

## Data Sources
The data analysed in this project were obtained from the following studies:
1. **Huber, A. et al. (2011).** Sch9 regulates ribosome biogenesis via Stb3, Dot6 and Tod6 and the histone deacetylase complex RPD3L.  
  *EMBO Journal* 30(15): 3052–3064. https://doi.org/10.1038/emboj.2011.221 (PMID: 21730963)
2. **Swaffer, M.P. et al. (2023).** RNA polymerase II dynamics and mRNA stability feedback scale mRNA amounts with cell size.  
  *Cell* 186(24): 5254–5268.e26. https://doi.org/10.1016/j.cell.2023.10.012 (PMID: 37944513)  
3. **Lanz, M.C. et al. (2024).** Genome dilution by cell growth drives starvation-like proteome remodeling in mammalian and yeast cells.  
  *Nature Structural & Molecular Biology* **31**(12): 1859–1871. https://doi.org/10.1038/s41594-024-01353-z (PMID: 39048803)  
4. **Mahendrawada, L. et al. (2025).** Low overlap of transcription factor DNA binding and regulatory targets.  
  *Nature* 642(8068): 796–804. https://doi.org/10.1038/s41586-025-08916-0 (PMID: 40240607)  

---

## Analytical Pipeline
Main computational steps implemented as RMarkdown workflows:

1. **mRNA slope import & combination**: integrates slopes from four RNA-seq datasets with TF-associated information.  
2. **growth rate signature removal**: uses linear regression and growth rate annotations to obtain slope residuals.  
3. **Wilcoxon tests (VP script)**: compares slope (or residual) distributions between TF-associated genes and the remaining genes, producing cumulative frequency distribution plots and volcano plots.  
4. **2D annotation enrichment analysis (EA script)**: uses `mitch` to calculate S-scores and adjusted p-values, producing enrichment scatter plots and heatmaps.  
5. **integration & visualisation**: generates Venn diagrams and summary tables highlighting TF gene groups which exhibit a biased scaling behaviour.

All scripts are organised to use relative paths and deposit outputs in `results/figures` and `results/tables`.

---

