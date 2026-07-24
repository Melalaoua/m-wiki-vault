---
type: concept
title: "Principal Component Analysis"
aliases: []
tags: [concept, personal]
updated: 2026-07-24
status: developing
---

# Principal Component Analysis

### Overview
**Principal Component Analysis (PCA)** is an unsupervised linear technique used for dimensionality reduction and feature extraction. Originating with Karl Pearson in 1901, it projects a high-dimensional dataset onto a lower-dimensional [[Latent Space]] of orthogonal axes, known as principal components, designed to capture maximum variance.

### Mathematical Formulation
Given a data matrix, the execution pipeline consists of:
1. **Standardization**: Scaling features to zero mean and unit variance.
2. **Covariance Matrix Construction**: Summarizing bivariate relationships across dimensions.
3. **Spectral Decomposition**: Extracting eigenvectors (the directions of maximum variance) and eigenvalues (the magnitude of variance) from the covariance matrix.
4. **Projection**: Mapping the original data points onto the chosen eigenvectors to yield low-dimensional [[Embedding Space]] representations.

### Limitations
Because PCA is fundamentally a linear transformation, it struggles with complex, non-linear manifolds. In such scenarios, researchers typically turn to non-linear alternatives like t-SNE, UMAP, or deep architectures like [[Variational Autoencoder]]s.

Source: [[phd/wiki/sources/www2026pca|PCA]]
