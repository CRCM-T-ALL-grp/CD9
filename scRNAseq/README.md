# Single-cell RNA-seq analysis

## Overview

This repository contains the code used to analyze scRNA-seq datasets and focuses on downstream statistical analysis and visualization starting from count matrices.

Starting from FASTQ files, demultiplexing, barcode processing, gene counting, and aggregation were performed using Cell Ranger v3.0.1.  
For each experiment, antibody counts for cell hashing were quantified using CITE-seq-Count v1.4.1.

The analysis is divided into two main steps:
1. Generation of a curated Seurat object from raw scRNA-seq data and firts analysis : `scRNAseq_part1.Rmd`
2. Downstream analysis and visualization based on this curated object : `scRNAseq_part2.Rmd`

In addition to in-house datasets, this repository also includes the reanalysis of a publicly available scRNA-seq dataset : `scRNAseq_public_dataset.Rmd`

## Prerequisites

To run the scRNA-seq analysis, you need to:
- Download the Seurat object generated in `scRNAseq_part1.Rmd` (`sickphys_reg.Robj`) hosted on [Zenodo](https://doi.org/10.5281/zenodo.18493456)
- Download the Docker image (`seurat500.tar`) hosted on [Zenodo](https://doi.org/10.5281/zenodo.18493456)
- Load the Docker image on your system

## GitHub repository

```bash
# set your working directory
export WORKING_DIR=/workspace/CD9
```

## Download Public Dataset

The public dataset can be downloaded using the following commands:
```bash
wget -P $WORKING_DIR/Data/ https://zenodo.org/records/19002805/files/Dataset2.rds
```

## Docker image

> [!WARNING]
> To reproduce the downstream analysis, you must load the provided Docker image.
> Docker must be installed on your system.
> See https://docs.docker.com/install/ for installation instructions.

### Download the Docker image
```bash
wget -P $WORKING_DIR/Container/ https://zenodo.org/records/18493456/files/seurat500.tar
```
### Load the Docker image
```bash
docker load --input $WORKING_DIR/Container/seurat500.tar
```
### Run the Docker container
```bash
docker run -d --name seurat500 -p 9292:8787 -v $WORKING_DIR:/workspace seurat500
```
Once the container is running, the analysis environment can be accessed through a web browser:  
http://localhost:9292/
