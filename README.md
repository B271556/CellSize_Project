# Cell-Size-Dependent Transcriptomic Regulation in *Saccharomyces cerevisiae*

Author: Hans Liu
---

## Project Overview
This repository contains the material used in my MSc Bioinformatics dissertation titled *Examination of transcription factor-regulated gene expression changes with cell size in yeast.*  There are approximately 150 known transcription factors (TFs) in the budding yeast *Saccharomyces cerevisiae*. Each TF binds to and/or regulates various genes. This project integrates mRNA expression derived from four RNA-seq datasets with TF binding and regulation information to uncover how the expression of genes associated with TFs scales with cell size. The analysis was done twice (before and after removing growth rate effects) in order to distinguish between expression changes associated with cell size from those associated with cellular growth rate. 

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
3. **Wilcoxon tests (VP script)**: compares slope (or residual) distributions between TF-associated genes and the remaining genes, producing cumulative frequency distribution plots, volcano plots, Venn diagrams, and tables to summarise the results.  
4. **2D annotation enrichment analysis (EA script)**: uses `mitch` to calculate S-scores and adjusted p-values, producing enrichment scatter plots, heatmaps, Venn diagrams, and tables to summarise the results. 

All scripts are organised to use relative paths and deposit outputs in `results/figures` and `results/tables`.

---

## Reproducibility

Each script starts by setting the working directory as the folder in which the script resides, so the scripts can be run without manually setting working directories. Certain scripts use the output generated from another script as input. However, to reproduce the results of this project, the scripts do not have to be run in any order, and each script can be run on its own. The reason is that all of the scripts have been run previously and all scripts use relative paths that are already set up in the _cell_size_project_ folder. This means that all required input files are already present. To ensure reproducibility, use Git clone below instead of downloading the ZIP as ZIP download only gets placeholders for large files such as .Rmd files.

To reproduce any portion, or the entirety of, the results generated from this project, follow the steps below. 

### 1. Install R and RStudio
  • Install R (version ≥ 4.3) from https://cran.r-project.org.  
  • Install RStudio (version ≥ 2023.12) from https://posit.co/download/rstudio-desktop/.  

### 2. Clone this repository by using Git  
  • Download Git from https://git-scm.com/downloads (Windows/macOS/Linux).  
  • Install Git LFS (via winget install GitHub.GitLFS on Windows; brew install git-lfs on macOS, or from https://git-lfs.com).  
  • In Terminal (if using Mac) or Command Prompt (if using Windows), run the following command:

```r
git clone https://github.com/B271556/CellSize_Project.git
cd CellSize_Project
git lfs pull         # downloads the full contents of large files (e.g., .Rmd files, .pdf files, tables)
```

### 3. Restore the R package environment used in this project
  • Double-click the project file _cellsize_project.Rproj_ to open it in RStudio (this sets the working directory automatically)  
  • Run the following command in the console:

```r
install.packages("renv")    # only needed if renv is not already installed
renv::restore()             # installs the exact package versions that were used in the project
```

  • If prompted, choose option 1 (activate project library).  

### 4. Open any .Rmd file in RStudio and run it 




