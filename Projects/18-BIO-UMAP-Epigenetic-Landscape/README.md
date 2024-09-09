## Epigenetic Landscape and Allelic Imbalance Analysis in Colorectal Carcinoma Using Single-Cell Data

### Introduction
Colorectal cancer (CRC) is the third most common cancer and the second leading cause of cancer-related deaths worldwide. Emerging research highlights that the non-coding regions of the genome and epigenetic regulatory mechanisms significantly contribute to CRC development. An in-depth understanding of these epigenetic alterations is crucial for elucidating the mechanisms underlying CRC progression.
Single-cell multi-omics techniques, such as single-cell RNA sequencing (scRNA-seq) and single-cell ATAC sequencing (scATAC-seq), offer unprecedented resolution to investigate these epigenetic mechanisms at the level of individual cells. These methods enable the exploration of both gene expression and chromatin accessibility dynamics, providing comprehensive insights into the functional non-coding genome's role in regulating gene expression. By integrating scRNA-seq and scATAC-seq data, researchers can unravel the specific epigenetic alterations that drive gene expression changes in CRC.

###Objective
This challenge aims to provide participants with hands-on experience in analyzing single-cell data to decipher the epigenetic landscape of CRC. Participants will learn how to process and integrate scRNA-seq and scATAC-seq data, identify cell-type-specific epigenetic regulatory mechanisms, and explore allelic imbalance (AI) in the context of CRC risk loci.

### Tasks
#### Main Task: Single-Cell Data Processing and Epigenetic Analysis
    1. Data Preparation and Quality Control (QC):
        ◦ Start with publicly available single-cell data from the GEO database (GSE201349), which includes 5 CRC and 5 normal samples. Preprocessed data (FASTQ, BAM, barcode.tsv, feature.tsv, matrix.mtx files) will be provided.
        ◦ Perform essential QC steps to filter out low-quality cells, doublets, and other artifacts in both scRNA-seq and scATAC-seq datasets.
    2. Dimensionality Reduction and Clustering:
        ◦ Create UMAP representations of the data to visualize cell populations.
        ◦ Perform clustering to identify distinct cell groups and annotate these clusters to identify different cell types.
    3. Cell-Type-Specific Regulatory Mechanism Identification:
        ◦ Integrate scRNA-seq and scATAC-seq data to map open chromatin regions to their corresponding gene expression.
        ◦ Identify cell-type-specific regulatory regions that may alter gene expression.
        ◦ Provide examples of potential regulatory elements and their corresponding genes in CRC.
    4. Data Visualization:
        ◦ Generate visualizations to show cell clusters, gene expression profiles, and chromatin accessibility patterns.
        ◦ Use tools like UMAP plots, heatmaps, and gene regulatory network diagrams to present your findings.
#### Extra Task: Allelic Imbalance (AI) Analysis
    1. Understanding Allelic Imbalance (AI):
        ◦ Allelic imbalance refers to the unequal expression of two alleles of a gene in a diploid organism, which could result from genetic variants affecting transcription factor binding and gene regulation.
    2. Example workflow (you can choose a completely different approach)
        ◦ BAM Slicing and AI Investigation:
            1. Choose a specific genomic region from identified CRC risk loci for AI analysis. The region can be chosen from identified CRC risk loci. Paper
            2. Annotate cell clusters based on UMAP results and extract cell IDs for different cell types.
            3. Create cell-type-specific BAM slice files for the selected region using the extracted cell IDs.
            4. Investigate AI in the chosen region using visual tools like Integrative Genomics Viewer (IGV).
        ◦ Integration of scRNA-seq and scATAC-seq for AI Analysis:
            1. Use scATAC-seq data to identify risk loci with potential allelic effects.
            2. Combine this with scRNA-seq data to analyze gene expression differences associated with these risk loci.

### Tools and Resources
    • R Tools: Seurat, Signac, etc.
    • Python Tools: Scanpy, AnnData, pyGenomeTracks, etc.
    • Visualization Tools: UMAP, IGV, heatmaps, gene regulatory network tools.

### Background materials
    • UMAP paper: https://arxiv.org/abs/1802.03426
    • UMAP short intro: https://pair-code.github.io/understanding-umap/
    • https://umap-learn.readthedocs.io/en/latest/
    • Single cell technology
    • CRC paper 
    • Seurat
    • Scanpy



