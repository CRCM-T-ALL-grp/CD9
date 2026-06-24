# Single-cell RNA-seq Analysis

## Overview

This directory contains the code used for single-cell RNA-seq analyses performed in this project.

Three analysis workflows are provided:

| Script                        | Description                                                                         |
| ----------------------------- | ----------------------------------------------------------------------------------- |
| `scRNAseq_part1.Rmd`          | Generation of a curated Seurat object from raw scRNA-seq data and initial analyses. |
| `scRNAseq_part2.Rmd`          | Downstream analyses and visualizations based on the curated Seurat object.          |
| `scRNAseq_public_dataset.Rmd` | Reanalysis of a publicly available scRNA-seq dataset.                               |

Raw FASTQ files were processed using Cell Ranger v3.0.1 for demultiplexing, barcode processing, gene counting, and aggregation.

For each experiment, antibody-derived tag (ADT) counts used for cell hashing were quantified using CITE-seq-Count v1.4.1.

# Data Requirements

## 1. In-house scRNA-seq Dataset

Files required by `scRNAseq_part2.Rmd`:

| File                |
| ------------------- |
| `sickphys_reg.Robj` |

This file contains the curated Seurat object generated in `scRNAseq_part1.Rmd` and allows users to directly reproduce downstream analyses and visualizations.

### Download links

Zenodo: https://doi.org/10.5281/zenodo.18493456

## 2. Public scRNA-seq Dataset

Files required by `scRNAseq_public_dataset.Rmd`:

| File           |
| -------------- |
| `Dataset2.rds` |

Source: https://doi.org/10.5281/zenodo.19002805

# Installation

## Clone the Repository

```bash
git clone https://github.com/JulienRey1/CD9
```

## Define the Working Directory

```bash
export WORKING_DIR=/workspace/CD9
```

# Docker Environment

The Docker image below is required to reproduce the analyses:

| Image       | Purpose                      |
| ----------- | ---------------------------- |
| `seurat500` | Single-cell RNA-seq analyses |

## Download Docker Image

```bash
wget -P $WORKING_DIR/Container/ https://zenodo.org/records/18493456/files/seurat500.tar
```

## Load Docker Image

```bash
docker load --input $WORKING_DIR/Container/seurat500.tar
```

## Start Container

```bash
docker run -d --name seurat500 -p 9292:8787 -v $WORKING_DIR:/workspace seurat500
```

# Access RStudio

Once the container is running, access the analysis environment through your browser:

### Single-cell RNA-seq analysis

http://localhost:9292
