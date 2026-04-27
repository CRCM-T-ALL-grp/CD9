# Flow Cytometry analysis

## Overview

This repository contains the code used to analyze flow cytometry data.

## Prerequisites

To run the flow cytometry script analysis, you need to:
- Download the datasets hosted on [Zenodo](https://doi.org/10.5281/zenodo.18493456)
- Download the Docker image (`seurat500.tar`) hosted on [Zenodo](https://doi.org/10.5281/zenodo.18493456)
- Load the Docker image on your system

## Working Directory

```bash
# set your working directory
export WORKING_DIR=/workspace/CD9
```

## Download datas

The datas can be downloaded using the following commands:
```bash
wget -P $WORKING_DIR/Data/ https://zenodo.org/records/18493456/files/Dataset2.rds
wget -P $WORKING_DIR/Data/ https://zenodo.org/records/18493456/files/PDX11_top.csv
wget -P $WORKING_DIR/Data/ https://zenodo.org/records/18493456/files/PDX11_bottom.csv
wget -P $WORKING_DIR/Data/ https://zenodo.org/records/18493456/files/PDX65_top.csv
wget -P $WORKING_DIR/Data/ https://zenodo.org/records/18493456/files/PDX65_bottom.csv
wget -P $WORKING_DIR/Data/ https://zenodo.org/records/18493456/files/PDX65_top_noC12.csv
wget -P $WORKING_DIR/Data/ https://zenodo.org/records/18493456/files/PDX65_bottom_noC12.csv
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

