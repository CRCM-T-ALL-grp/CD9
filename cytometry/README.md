# Flow Cytometry Analysis

## Overview

This directory contains the code used for flow cytometry analyses performed in this project.

The analysis workflow is provided in:

| Script                     | Description                                            |
| -------------------------- | ------------------------------------------------------ |
| `migration_versus_CD9.Rmd` | Analysis and visualization of flow cytometry datasets. |

# Data Requirements

## Flow Cytometry Datasets

Files required by `migration_versus_CD9.Rmd`:

| File                     |
| ------------------------ |
| `PDX11_top.csv`          |
| `PDX11_bottom.csv`       |
| `PDX65_top.csv`          |
| `PDX65_bottom.csv`       |
| `PDX65_top_noC12.csv`    |
| `PDX65_bottom_noC12.csv` |

### Download links

Zenodo: https://doi.org/10.5281/zenodo.18493456

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

| Image       | Purpose                 |
| ----------- | ----------------------- |
| `seurat500` | Flow cytometry analyses |

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

### Flow Cytometry Analysis

http://localhost:9292