# Short Summaries

## 01 - Astro UMAP: Detecting Outliers and Learning Complex Structures with Large Spectroscopic Surveys

This project explores dimensionality-reduction techniques (PCA, t-SNE, UMAP, and variational autoencoders) to uncover clusters and outliers hidden in high-dimensional astronomical data, such as spectra and galaxy images, with a stretch goal of rediscovering rare "green pea galaxies" from GalaxyZoo images. Required careful interpretation of unsupervised embeddings to avoid drawing misleading conclusions from projections that don't preserve true data structure. Useful skills include Python (scikit-learn, UMAP, PyTorch/TensorFlow for VAEs), familiarity with unsupervised learning and dimensionality reduction, and basic astrophysics/spectroscopy background.

## 02 - Photometric Redshift Estimation

This project focuses on estimating photometric redshifts of galaxies using data from the Sloan Digital Sky Survey, comparing empirical machine learning approaches (kNN, SVM, random forest, CNNs) with theoretically motivated template-fitting methods. Iinvolving both astrophysical domain knowledge (magnitudes, K-corrections, spectral templates) and hands-on data acquisition and preprocessing from a real astronomical database. Useful skills include Python and `scikit-learn` for machine learning, SQL for querying the SDSS SkyServer database, and some familiarity with deep learning frameworks (e.g. CNNs) and basic astrophysics/spectroscopy concepts.

## 03 - Lightning Hotspots on Earth

This project reanalyzes 16+ years of satellite lightning-flash data (TRMM/ISS Lightning Imaging Sensor) to reproduce and update the lightning-hotspot statistics of Albrecht et al. (2016), checking whether geographic patterns have shifted due to climate change. Handling large HDF/NetCDF satellite datasets and correctly reconstructing the event-group-flash-area hierarchy before computing statistics. Useful skills include Python (netCDF4, Basemap/cartopy), data format conversion, and geospatial statistical analysis.

## 04 - Mesoscale Ocean Eddies along the U.S. West Coast

This project tests whether a reported correlation between eddy radius and lifetime (found in the Western Mediterranean by Escudier et al. 2016) also holds for mesoscale ocean eddies off the U.S. West Coast, using a geostrophic flow-field dataset derived from satellite altimetry. It requires implementing and comparing multiple eddy detection/tracking algorithms and critically judging their disagreements. Useful skills include Python (NetCDF4, Basemap/cartopy, image/contour analysis), numerical algorithm implementation, and basic physical oceanography.

## 05 - Predicting Flowering Dates Based on Meteorological Information

This project predicts the year-to-year flowering dates of 329 perennial plant species from decades of historical daily weather data (temperature, soil moisture, radiation, etc.), using sparse regression methods such as orthogonal matching pursuit to cope with far more explanatory variables than observations. The problem is strongly under-determined and requires careful handling of missing data, correlated predictors, and train/test splitting for validation. Useful skills include Python and `scikit-learn` (sparse regression, feature selection), time-series data wrangling, and basic climatology/biology background.

## 06 - CMB Power Spectrum

This project reconstructs the Cosmic Microwave Background (CMB) angular power spectrum from Planck sky maps, and optionally generates synthetic CMB maps from theoretical power spectra using the CAMB tool. The difficulty is moderate, requiring an understanding of cosmological theory and following established (but non-trivial) analysis pipelines and notebooks rather than building methods from scratch. Useful skills include Python-based cosmology tools (CAMB, healpy), familiarity with Jupyter-based scientific workflows, and background in cosmology/physics.

## 07 - Signatures of Mutational Processes in Human Cancer

This project decomposes catalogs of somatic mutations from multiple cancer types into underlying "mutational signatures" using non-negative matrix factorization, followed by clustering signatures across cancers into a consensus set. Combining genomic data wrangling (FASTA reference genomes, mutation annotation files), numerical matrix factorization, and non-trivial clustering/validation of results. Useful skills include Python (pandas, NumPy, scikit-learn's NMF), bioinformatics/genomics data handling, and clustering/statistical evaluation.

## 09 - Twitter: Small World

This project explores the "small world" structure of a Twitter social network, analyzing connectivity and network topology among users (see the accompanying notebook for detailed tasks). It centers on applying established network-science measures to real, potentially noisy social media data. Useful skills include Python (`networkx`), graph/network analysis, and basic social media data handling.

## 11 - Wars on Wikipedia

This project identifies "edit wars" in Wikipedia articles and explores the social network of conflicting editors alongside the semantic network of the pages they fight over, based on the work of Yasseri et al. Large-scale data processing is required due to the scale of Wikipedia dump data and the need to define and detect edit wars in a principled way. Useful skills include Python, network analysis (`networkx`), and text/data mining of large structured dumps.

## 14 - Cell Motion

This project analyzes time-lapse phase-contrast microscopy images of a glioblastoma cell culture, segmenting individual cells, tracking their motion to estimate velocity distributions, and fitting an anomalous diffusion model to the trajectories. Requires reliable image segmentation of noisy microscopy data as well as physical modeling of cell trajectories. Useful skills include Python-based image processing (scikit-image/OpenCV), trajectory/statistical analysis, and basic diffusion-model physics.

## 15 - Neural Network-Aided Milk Somatic Cell Count Gain Prediction

This project investigates whether data from common milking machines can be used to predict subclinical mastitis in dairy cows via somatic cell count (SCC) trends, using neural network models. Involves working with real-world sensor/tabular data with practical noise and the need to design a suitable prediction target from continuous herd data. Useful skills include Python, deep learning frameworks (PyTorch/TensorFlow), and data preprocessing; familiarity with veterinary/dairy science is a plus.

## 16 - Bacterial Colony Size Growth Estimation by Deep Learning

This project estimates bacterial colony growth rates over time from Petri-dish images (against white/black backgrounds) using deep learning, relevant to food safety and pathogenicity studies. Mainly involving image-based colony detection/segmentation and converting size changes into growth-rate estimates. Useful skills include deep learning for image analysis (CNNs, object detection/segmentation), Python, and basic image processing.

## 17 - Impact Evaluation of Score Classes and Annotation Regions in Deep Learning-Based Dairy Cow Body Condition Prediction

This project evaluates how different scoring classes and annotated body regions affect the performance of deep learning models that predict dairy cow body condition from images, replacing time-consuming manual expert scoring. Requiring careful experimental comparison of model variants rather than developing an entirely new method. Useful skills include deep learning for image classification (CNNs), image annotation/data handling, and statistical model evaluation.

## 18 - Epigenetic Landscape and Allelic Imbalance Analysis in Colorectal Carcinoma Using Single-Cell Data

This project integrates single-cell RNA-seq and ATAC-seq data from colorectal cancer and normal samples to identify cell-type-specific epigenetic regulatory mechanisms and, optionally, allelic imbalance at cancer risk loci. It requires multi-omics integration, single-cell QC/clustering pipelines, and interpretation of chromatin accessibility alongside gene expression. Useful skills include R/Python single-cell tools (Seurat, Signac, Scanpy, AnnData), UMAP-based dimensionality reduction/clustering, and genomics/epigenetics background.

## 21 - Detecting Uracil in DNA from Nanopore Signals

This project investigates whether nanopore sequencing signals contain sufficient information to distinguish uracil (U) from thymine (T) in DNA sequences, a differentiation that standard basecalling software cannot make despite its biological importance in gene regulation and immune system function. It involves comparing normalized electrical current signals from two datasets (T-only DNA vs. U-substituted DNA), identifying subtle signal perturbations between the bases, and building an XGBoost classifier to predict whether a given position contains T or U. Useful skills include Python, signal processing and exploratory data analysis, gradient boosting methods (XGBoost), and basic molecular biology/sequencing background.
