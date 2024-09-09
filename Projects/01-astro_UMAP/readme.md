# Detecting outliers and learning complex structures with large spectroscopic surveys

### Introduction
Many of scientific data is in form of high dimesional data vectors. These are hard to handle by humans and there are several methods, PCA, t-SNE, UMAP, ... that are used to create lower dimensional projections. These projections can be used in the data exploration phase and when presenting and viuslizing results, but one should be very careful to use them for reliabla data analysis. The goal of the project is to explore these methods to find clusters and outliers in astronomical spectra (and images).

### Task

We would like to reconstruct the results of [this paper](https://arxiv.org/pdf/1711.00022.pdf) , and if time allows do similar data analysis on other type of data, e.g. images. An interseting challenge would be, to use this approach to re-discover the [green pea galaxies](https://en.wikipedia.org/wiki/Pea_galaxy) in [GalaxyZoo images](https://data.galaxyzoo.org/)

- [1] Boucaud, A., Heneka, C., Ishida, E.E., Sedaghat, N., de Souza, R.S., Moews, B., Dole, H., Castellano, M., Merlin, E., Roscani, V. and Tramacere, A., 2020. Photometry of high-redshift blended galaxies using deep learning. Monthly Notices of the Royal Astronomical Society, 491(2), pp.2481-2495. [link](https://arxiv.org/pdf/1711.00022.pdf) 

Another interesting new approach for the dimension reduction problem is using Variational Autoencoder neural nets. This paper introduces the idea through a similar astronomical spectral exploration example:

- Sedaghat, N., Romaniello, M., Carrick, J.E. and Pineau, F.X., 2021. Machines learn to infer stellar parameters just by looking at a large number of spectra. Monthly Notices of the Royal Astronomical Society, 501(4), pp.6026-6041. [link](https://arxiv.org/pdf/2009.12872.pdf)

### Background materials
- UMAP paper: https://arxiv.org/abs/1802.03426
- UMAP short intro: https://pair-code.github.io/understanding-umap/
- https://umap-learn.readthedocs.io/en/latest/
- [Embedding projector](https://towardsdatascience.com/visualizing-bias-in-data-using-embedding-projector-649bc65e7487)  visualization tool, [online version](http://projector.tensorflow.org/) 
- Intro to [Varriational Autoencoders](https://towardsdatascience.com/understanding-variational-autoencoders-vaes-f70510919f73)
- GPU accelerated version of UMAP and other data exploration methods: [RAPIDS cuML](https://github.com/rapidsai/cuml)
