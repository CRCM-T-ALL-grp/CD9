> [!WARNING]
> 🚧🚧🚧 **WORK IN PROGRESS** 🚧🚧🚧  
> This folder is still under construction.

# Single-cell RNA-seq analysis

## Overview

This repository contains the code used to analyze scRNA-seq datasets.
It focuses on downstream statistical analysis and visualization starting from count matrices.

The analysis is divided into two main steps:
1. Generation of a curated Seurat object from raw scRNA-seq data and firts analysis : `scRNAseq_part1.Rmd`
2. Downstream analysis and visualization based on this curated object : `scRNAseq_part2.Rmd`

<!--
## Analysis workflow

### Step 1 - `scRNAseq_part1.Rmd`

> [!WARNING]
> The original Docker container used for this step is not available. As a result, exact reproduction of the UMAP coordinates is not guaranteed.

However, the biological results remain identical:
- the same cells and genes are selected
- the same filtering thresholds are applied
- downstream conclusions are unchanged

For reproducibility and transparency, the resulting Seurat object is therefore shared
directly and should be used as the starting point for downstream analyses.

### Step 2 - `scRNAseq_part2.Rmd`

The second step of the analysis is based on the Seurat object generated in Step 1
and includes downstream analyses and visualizations.

This step is fully reproducible using the provided Docker image based on Seurat v4.4.0.
-->

## Prerequisites

To run the downstream scRNA-seq analysis (Step 2), you need to:
- Clone this GitHub repository
- Download the Seurat object generated in Step 1 (`sickphys_reg.Robj`) hosted on [Zenodo]<!--(https://doi.org/xx.xxxx/zenodo.xxxxxxxx)-->
- Download the Docker image (`seurat4.4.0.v2.tar`) hosted on [Zenodo]<!--(https://doi.org/xx.xxxx/zenodo.xxxxxxxx)-->
- Load the Docker image on your system

## GitHub repository

```bash
# set your working directory
export WORKING_DIR=/workspace/CD9
```
```bash
git clone https://github.com/JulienRey1/CD9.git
```

## Docker image

> [!WARNING]
> To execute the downstream analysis, you must load the provided Docker image.
> Docker must be installed on your system.
> See https://docs.docker.com/install/ for installation instructions.

### Download the Docker image
```bash
wget -P $WORKING_DIR/Container/ https://zenodo.org/records/xxxxxxxx/files/seurat4.4.0.v2.tar
```
### Load the Docker image
```bash
docker load --input $WORKING_DIR/Container/seurat4.4.0.v2.tar
```
### Run the Docker container
```bash
docker run -d --name seurat4.4.0.v2 -p 9191:8787 -v $WORKING_DIR:/workspace seurat4.4.0.v2
```
Once the container is running, the analysis environment can be accessed through a web browser:  
http://localhost:9191/
