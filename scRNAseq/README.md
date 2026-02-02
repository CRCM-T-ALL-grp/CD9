> [!WARNING]
> 🚧🚧🚧 **WORK IN PROGRESS** 🚧🚧🚧  
> This folder is still under construction.

# Single-cell RNA-seq analysis

## Overview

This repository contains the code and resources used to analyze scRNA-seq datasets.

The analysis is divided into two main steps:
1. Generation of a curated Seurat object from raw scRNA-seq data and firts analysis.
2. Downstream analysis and visualization based on this curated object

## Analysis workflow

### Step 1 – Data integration and subsetting (Seurat v4)

The first step of the analysis was performed using Seurat v4 and consists of:
- Merging multiple scRNA-seq datasets
- Subsetting cells and genes of interest
- Applying quality control and filtering criteria

This step produces a curated Seurat R object that serves as the input for all subsequent analyses.

> [!WARNING]
> The original Docker container used for this step is not available. As a result, exact reproduction of the UMAP coordinates is not guaranteed.

However, the biological results remain identical:
- the same cells and genes are selected
- the same filtering thresholds are applied
- downstream conclusions are unchanged

For reproducibility and transparency, the resulting Seurat object is therefore shared
directly and should be used as the starting point for downstream analyses.

Note: No Docker image is provided for `scRNAseq_part1.Rmd`.

### Step 2 – Downstream analysis (Seurat v4.4.0)

The second step of the analysis is based on the Seurat object generated in Step 1
and includes downstream analyses and visualizations.

This step is fully reproducible using the provided Docker image based on Seurat v4.4.0.

The analysis code for this step is contained in `scRNAseq_part2.Rmd`.

## Prerequisites

To run the downstream scRNA-seq analysis (Step 2), you need to:
- Clone this GitHub repository
- Download the Docker image (`seurat4.4.0.v2.tar`) hosted on Zenodo
- Load the Docker image on your system

## GitHub repository

# Set your working directory
```bash
export WORKING_DIR=/workspace/CD9
```
```bash
git clone https://github.com/JulienRey1/CD9.git
```

## Docker image (Step 2 only)

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
