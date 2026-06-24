# Bulk RNA-seq Analysis

## Overview

This directory contains the code used for bulk RNA-seq analyses performed in this project.

Two analysis workflows are provided:

| Script                          | Description                                            |
| ------------------------------- | ------------------------------------------------------ |
| `bulkRNAseq.Rmd`                | Analysis of the in-house bulk RNA-seq dataset.         |
| `bulkRNAseq_public_dataset.Rmd` | Analysis of publicly available T-ALL RNA-seq datasets. |

Raw FASTQ files from the in-house cohort were preprocessed using the nf-core/rnaseq pipeline (v3.21.0) with STAR-RSEM as the aligner and default parameters.

Public datasets were obtained from published studies and preprocessed expression matrices available through Zenodo or supplementary material repositories.

# Data Requirements

## 1. In-house Bulk RNA-seq Dataset

Files required by `bulkRNAseq.Rmd`:

| File                             | Source |
| -------------------------------- | ------ |
| `counts.txt`                     | GEO    |
| `edgeR_fit.rds` *(optional)*     | Zenodo |
| `data.filtered.rds` *(optional)* | Zenodo |

The optional RDS files contain preprocessed objects and allow users to skip the initial filtering and model fitting steps.

### Download links

Zenodo: https://doi.org/10.5281/zenodo.18493456

GEO: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE319183

## 2. TCGA T-ALL Dataset

Files required by `bulkRNAseq_public_dataset.Rmd`:

| File                                      |
| ----------------------------------------- |
| `RNA_matrix_TARGET_TALL_convert.rds`      |
| `Clinical_matrix_TARGET_TALL_convert.rds` |

Source: https://doi.org/10.5281/zenodo.14044880

## 3. TALL-X01 Dataset

Files required by `bulkRNAseq_public_dataset.Rmd`:

| File                                                |
| --------------------------------------------------- |
| `TALL_X01_FeatureMatrix_genomics_subtype.Rdata`     |
| `TALL_X01_vst.tsv`                                  |
| `TALL_X01_gene_annotations_unfiltered.tsv`          |
| `NIHMS2036708-supplement-Supplementary_Tables.xlsx` |

These files are derived from the supplementary material associated with the Nature publication :<br>
Pölönen P, Di Giacomo D, Seffernick AE, Elsayed A, Kimura S, Benini F *et al.*
**The genomic basis of childhood T-lineage acute lymphoblastic leukaemia.**
*Nature* (2024) 632:1082–1091.

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

Two Docker images are provided:

| Image          | Purpose                        |
| -------------- | ------------------------------ |
| `rna_analysis` | In-house bulk RNA-seq analysis |
| `rna431-2`     | Public dataset analyses        |

## Download Docker Images

```bash
wget -P $WORKING_DIR/Container/ https://zenodo.org/records/18493456/files/rna_analysis.tar
wget -P $WORKING_DIR/Container/ https://zenodo.org/records/14044880/files/rna431-2.tar
```

## Load Docker Images

```bash
docker load --input $WORKING_DIR/Container/rna_analysis.tar
docker load --input $WORKING_DIR/Container/rna431-2.tar
```

## Start Containers

```bash
docker run -d --name rna_analysis -p 9090:8787 -v $WORKING_DIR:/workspace rna_analysis
docker run -d --name rna431-2 -p 9191:8787 -v $WORKING_DIR:/workspace rna431-2
```
# Access RStudio

Once the containers are running, access the analysis environments through your browser:

### In-house RNA-seq analysis

http://localhost:9090

### Public dataset analysis

http://localhost:9191