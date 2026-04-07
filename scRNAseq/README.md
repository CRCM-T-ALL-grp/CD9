# Single-cell RNA-seq analysis

## Overview

This repository contains the code used to analyze scRNA-seq datasets and focuses on downstream statistical analysis and visualization starting from count matrices.

Starting from FASTQ files, demultiplexing, barcode processing, gene counting, and aggregation were performed using Cell Ranger v3.0.1.  
For each experiment, antibody counts for cell hashing were quantified using CITE-seq-Count v1.4.1.

The analysis is divided into two main steps:
1. Generation of a curated Seurat object from raw scRNA-seq data and firts analysis : `scRNAseq_part1.Rmd`
2. Downstream analysis and visualization based on this curated object : `scRNAseq_part2.Rmd`

In addition to in-house datasets, this repository also includes the reanalysis of a publicly available scRNA-seq dataset. The dataset can be downloaded using :
```bash
wget -P $WORKDIR/ https://zenodo.org/records/XXXXXXXX/files/XXXXXXXXXX.rds
```
The script used for this reanalysis follows the same workflow as described below, starting from the Seurat object.

> [!WARNING]
> As described in the data availability section of [CD9 README](../README.md), the preprocessing step in `scRNAseq_part1.Rmd` cannot be reproduced.
> For transparency and reproducibility, the resulting Seurat object is therefore provided directly and should be used as the starting point for all downstream analyses.

## Prerequisites

To run the scRNA-seq analysis, you need to:
- Clone this GitHub repository
- Download the Seurat object generated in Step 1 (`sickphys_reg.Robj`) hosted on [Zenodo](https://doi.org/10.5281/zenodo.18493456)
- Download the Docker image (`seurat4.4.0.v2.tar`) hosted on [Zenodo](https://doi.org/10.5281/zenodo.18493456)
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
wget -P $WORKING_DIR/Container/ https://zenodo.org/records/18493456/files/seurat4.4.0.v2.tar
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
