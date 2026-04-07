# Bulk RNA-seq analysis

## Overview

This repository contains the code and resources used to analyze bulk RNA-seq datasets.
It focuses on downstream statistical analysis and visualization starting from count matrices.

RNA-seq FASTQ files were preprocessed using the nf-core rnaseq pipeline (v3.21.0), with STAR–RSEM as the aligner and default parameters.

In addition to in-house datasets, this repository includes the analysis of publicly available RNA-seq datasets derived from TCGA, which provides expression matrices and associated clinical annotations.

## Prerequisites

To run the analysis, you need to prepare the following environment:
- Clone this GitHub repository
- Download the Docker image (`rna_analysis.tar`) hosted on [Zenodo](https://doi.org/10.5281/zenodo.18493456)
- Load the Docker image on your system
- Download the count matrix on [GEO](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE319183)

Pre-processed data files are also available on Zenodo. These files allow you to skip
the initial data preparation steps and directly start the differential expression analysis:
- `edgeR_fit.rds`: R object containing the fitted edgeR model (design matrix and dispersions)
- `data.filtered.rds`: filtered count matrix with sample and gene annotations

## Github repository

```bash
# set your working directory
export WORKING_DIR=/workspace/CD9
```

```bash
git clone https://github.com/JulienRey1/CD9.git
 ```
## Download Public Dataset

The TCGA dataset can be downloaded using the following commands:
```bash
wget -P $WORKING_DIR/Data/ https://zenodo.org/records/14044880/files/RNA_matrix_TARGET_TALL_convert.rds
wget -P $WORKING_DIR/Data/ https://zenodo.org/records/14044880/files/Clinical_matrix_TARGET_TALL_convert.rds
```
## Docker image

> [!WARNING]
> To execute the analysis, you must load the provided Docker image.
> Docker must be installed on your system.
> See https://docs.docker.com/install/ for installation instructions.

### Download the Docker image
```bash
wget -P $WORKING_DIR/Container/ https://zenodo.org/records/18493456/files/rna_analysis.tar
wget -P $WORKING_DIR/Container/ https://zenodo.org/records/14044880/files/rna431-2.tar
```
### Load the Docker image
```bash
docker load --input $WORKING_DIR/Container/rna_analysis.tar
docker load --input $WORKING_DIR/Container/rna431-2.tar
```
### Run the Docker container
```bash
docker run -d --name rna_analysis -p 9090:8787 -v $WORKING_DIR:/workspace rna_analysis
docker run -d --name rna431-2 -p 9191:8787 -v $WORKING_DIR:/workspace rna431-2
```
Once the container is running, the analysis environment can be accessed through a web browser:  
http://localhost:9090/  
http://localhost:9191/
