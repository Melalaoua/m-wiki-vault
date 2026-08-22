---
type: concept
title: Principal Component Analysis
aliases: []
tags:
  - concept
  - phd
updated: 2026-07-24
status: developing
---

# Principal Component Analysis

### Overview
**Principal Component Analysis (PCA)** is an [[unsupervised-learning|unsupervised]] linear technique used for [[linear-algebra|dimensionality reduction]] and feature extraction. Originating with [[karl-pearson]] in 1901, it projects a high-dimensional dataset onto a lower-dimensional [[latent-space]] of orthogonal axes, known as principal components, designed to capture maximum variance.

- **==Eigenvector==** : Imagine a linear transformation (like stretching or rotating a vector space). An eigeinvector of a square matrix is a non-zero vector that, when that transformation is applied to it, only changes by a sclar factor. It doesn't change its direction. Its a special direction in the data that remins stable under the transformation. => *Represented by the equation $A\mathbf{v} = \lambda\mathbf{v}$, where A is a square matrix, $\mathbf{v}$ is the eigenvector, and λ is the eigenvalue.*

### Mathematical Formulation
Given a data matrix, the execution pipeline consists of:
1. **Standardization**: Scaling features to zero mean and unit variance.
2. **Covariance Matrix Construction**: Summarizing bivariate relationships across dimensions.
3. **Spectral Decomposition**: Extracting eigenvectors (the directions of maximum variance) and eigenvalues (the magnitude of variance) from the covariance matrix.
4. **Projection**: Mapping the original data points onto the chosen eigenvectors to yield low-dimensional [[embedding-space]] representations.

### Limitations
Because PCA is fundamentally a linear transformation, it struggles with complex, non-linear manifolds. In such scenarios, researchers typically turn to non-linear alternatives like t-SNE, UMAP, or deep architectures like [[phd/wiki/concepts/variational-autoencoder|variational-autoencoder]]s.

Source: [[phd/wiki/sources/www2026pca|PCA]]
