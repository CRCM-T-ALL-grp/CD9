**This repository contains the instructions to reproduce the analysis reported in the article :**

# Dynamic expression of CD9 protein in T-cell acute lymphoblastic leukemia

Authors : Quessada Julie<sup>1,2</sup>, Nozais Mathis<sup>1</sup>, Savey Charlotte<sup>1</sup>, Rey Julien<sup>1</sup>, Potier Delphine<sup>1</sup>, Loosveld Marie<sup>1,2</sup> & Payet Bornet Dominique<sup>1</sup>

<sup>1</sup> Aix Marseille Univ, CNRS, INSERM, Institut Paoli-Calmettes, CRCM, Marseille, France <br>
<sup>2</sup> APHM, Hôpital La Timone, Laboratoire d'Hématologie, Marseille, France

<!--
PMID:

Link to article : [DOI: xx.xxxx/???.xxxxxxx ](https://???)
-->

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18493456.svg)](https://doi.org/10.5281/zenodo.18493456)

[![Generic badge](https://img.shields.io/badge/GEO-GSE319183-blue.svg)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE319183)

---
### Overview

The bio-informatic analysis are divided in 2 part : 
- scRNAseq of thymocytes and splenocytes from wildtype and Pten knockout mice
- bulkRNAseq of Patient-Derived Xenograft of primary human T-ALL samples in immunodeficient NSG mice and Jurkat cells

All the code are available in this github repository.
Required data and builded Docker images are available in GEO and Zenodo.
Instructions to reproduce the analysis are provided in the different subdirectories:

- scRNAseq
	- Seurat preprocessing and analysis of the mice is described in the [scRNAseq](scRNAseq/) folder
- bulkRNAseq
	- Preprocesing and analysis of the PDX and Jurkat cells are described in the [bulkRNAseq](bulkRNAseq/) folder

---

### Data Availability

#### Mice scRNAseq

The raw and normalized count matrices for the scRNA-seq experiment are available on Zenodo, along with the final Seurat R object.
Raw sequencing data (FASTQ files) are not available. Some mice used to generate the dataset were not included in this publication and therefore remain confidential.

#### PDX and Jurkat bulkRNAseq

The raw counts and log-CPM–normalized counts for the bulk RNA-seq experiments are available via GEO, and the intermediate fitted edgeR objects can be downloaded from Zenodo.
Raw sequencing data (FASTQ files) are available for the Jurkat samples on GEO, but are not provided for the patient-derived xenograft (PDX) samples due to patient privacy concerns.
