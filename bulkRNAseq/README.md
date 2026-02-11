# Bulk RNA-seq analysis

## Overview

This repository contains the code and ressources used to analyze bulk RNA-seq datasets.
It focuses on downstream statistical analysis and visualization starting from count matrices.

RNA-seq FASTQ files were preprocessed using the nf-core rnaseq pipeline (v3.21.0), with STAR–RSEM as the aligner and default parameters.

## Prerequisites

To run the analysis, you need to prepare the following environment:
- Clone this GitHub repository
- Download the Docker image (`rna_analysis.tar`) hosted on [Zenodo](https://doi.org/10.5281/zenodo.18493456)
- Load the Docker image on your system

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

## Docker image

> [!WARNING]
> To execute the analysis, you must load the provided Docker image.
> Docker must be installed on your system.
> See https://docs.docker.com/install/ for installation instructions.

### Download the Docker image
```bash
wget -P $WORKING_DIR/Container/ https://zenodo.org/records/18493456/files/rna_analysis.tar
```
### Load the Docker image
```bash
docker load --input $WORKING_DIR/Container/rna_analysis.tar
```
### Run the Docker container
```bash
docker run -d --name rna_analysis -p 9090:8787 -v $WORKING_DIR:/workspace rna_analysis
```
Once the container is running, the analysis environment can be accessed through a web browser:  
http://localhost:9090/
