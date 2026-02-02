**This repository contains the instructions and material to reproduce the analysis reported in the article :**

# Dynamic expression of CD9 protein in T-cell acute lymphoblastic leukemia

Authors : Quessada Julie<sup>1,2</sup>, Nozais Mathis<sup>1</sup>, Savey Charlotte<sup>1</sup>, Rey Julien<sup>1</sup>, Potier Delphine<sup>1</sup>, Loosveld Marie<sup>1,2</sup> & Payet Bornet Dominique<sup>1</sup>

<sup>1</sup> Aix Marseille Univ, CNRS, INSERM, Institut Paoli-Calmettes, CRCM, Marseille, France <br>
<sup>2</sup> APHM, Hôpital La Timone, Laboratoire d'Hématologie, Marseille, France

<!--
PMID:

Link to article : [DOI: xx.xxxx/???.xxxxxxx ](https://???)

[![DOI](https://zenodo.org/badge/DOI/xx.xxxx/zenodo.xxxxxxxx.svg)](https://doi.org/xx.xxxx/zenodo.xxxxxxxx)

[![Generic badge](https://img.shields.io/badge/GEO-GSExxxxxx-blue.svg)](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSExxxxxx)
-->

---
### Overview

The bio-informatic analysis are divided in 2 part : 
- scRNAseq on PTEN<sup>del</sup> mice
- bulkRNAseq on Patient-Derived Xenograft (PDX) and Jurkat cells

All the code are available in this github repository. Required data and builded Docker images are available respectively in GEO and Zenodo. Instructions to reproduce the analysis are provided in the different subdirectories:

- scRNAseq
	- Seurat preprocessing and analysis of the mice is described in the scRNAseq folder : [scRNAseq](scRNAseq/)
- bulkRNAseq
	- Preprocesing and analysis of the PDX and Jurkat cells are described in the bulkRNAseq folder : [bulkRNAseq](bulkRNAseq/)

---

### Data Availability

#### Mice scRNAseq

Raw counts matrix and metadata to assign each cell to a sample for the mice scRNAseq experiment are available via GEO. Final R Seurat object can be dowloaded via Zenodo.

#### PDX and Jurkat bulkRNAseq

Raw counts and CPM normalized counts for the bulkRNAseq are available via GEO. The intermediates fit object from edgeR can be downloaded via Zenodo.
