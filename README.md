**This repository contains the instructions to reproduce the analysis reported in the article :**

# Dynamic expression of CD9 protein in T-cell acute lymphoblastic leukemia

Authors : Quessada Julie<sup>1,2</sup>, Nozais Mathis<sup>1</sup>, Savey Charlotte<sup>1</sup>, Rey Julien<sup>1</sup>, Potier Delphine<sup>1</sup>, Loosveld Marie<sup>1,2</sup> & Payet Bornet Dominique<sup>1</sup>

<sup>1</sup> Aix Marseille Univ, CNRS, INSERM, Institut Paoli-Calmettes, CRCM, Marseille, France <br>
<sup>2</sup> APHM, Hôpital La Timone, Laboratoire d'Hématologie, Marseille, France

<!--
PMID:

Link to article : DOI: 10.1038/s41417-026-01066-z [DOI: xx.xxxx/???.xxxxxxx ](https://???)
-->

GEO dataset : [![Generic badge](https://img.shields.io/badge/GEO-GSE319183-blue.svg)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE319183)

Zenodo : [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18493456.svg)](https://doi.org/10.5281/zenodo.18493456)

---
### Overview
This repository contains the code used to perform bioinformatic analyses of single-cell, bulk RNA-seq datasets and flow cytometry, with a focus on downstream statistical analysis and visualization starting from count matrices.

The analyses are organized into three main parts:

- [scRNA-seq](scRNAseq/) : Analysis of thymocytes and splenocytes from wild-type and Pten knockout mice. This workflow includes Seurat-based preprocessing and downstream analyses starting from count matrices, as well as the reanalysis of publicly available datasets.
- [bulk RNA-seq](bulkRNAseq/) : Analysis of Patient-Derived Xenograft (PDX) models from primary human T-ALL samples in immunodeficient NSG mice, along with Jurkat cell lines. This workflow also includes the reanalysis of publicly available datasets, including TCGA RNA-seq data.
- [flow cytometry](cytometry/) : Basic analysis of flow cytometry data with generation of a single representative figure.

All code is available in this GitHub repository. Required datasets and pre-built Docker images are hosted on GEO and Zenodo. Detailed instructions for reproducing the analyses are provided in the corresponding subdirectories.

---  

### Data Availability

#### Mice scRNAseq

The raw and normalized count matrices for the scRNA-seq experiment are available on Zenodo, along with the final Seurat R object.

#### PDX and Jurkat bulkRNAseq

The raw counts and log-CPM–normalized counts for the bulk RNA-seq experiments are available via GEO, and the intermediate fitted edgeR objects can be downloaded from Zenodo.
Raw sequencing data (FASTQ files) are available for the Jurkat samples on GEO.
