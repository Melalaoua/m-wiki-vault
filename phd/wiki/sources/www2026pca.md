---
type: source
title: "PCA"
citekey: www2026pca
source_type: article
captured: 2026-07-24
site: www.ibm.com
url: https://www.ibm.com/think/topics/principal-component-analysis
aliases: []
tags: [source, personal]
updated: 2026-07-24
status: developing
---

# PCA

Original: [[phd/raw/www.ibm.com/pca]]

The article provides a comprehensive overview of **Principal Component Analysis (PCA)**, a fundamental multivariate statistical technique credited to Karl Pearson in 1901. PCA serves as a cornerstone for dimensionality reduction, helping combat the "curse of dimensionality" in high-dimensional datasets while minimizing information loss.

### Key Mechanisms and Concepts
PCA transforms correlated variables into a smaller set of linearly independent variables called **principal components**. 
*   **First Principal Component (PC1):** The spatial direction along which data points exhibit the highest variance.
*   **Second Principal Component (PC2):** Perpendicular (orthogonal) to PC1, accounting for the next highest level of variance under the constraint of zero correlation with PC1.

Mathematically, the technique utilizes linear algebra and matrix operations on a standardized dataset:
1.  **Standardization:** Normalizing continuous variables to have a mean of zero and standard deviation of one, preventing scale-based bias.
2.  **Covariance Matrix:** Quantifying how the variables vary together. 
3.  **Eigenvalue/Eigenvector Decomposition:** Identifying eigenvectors (which represent the directions of variance, hence the principal components) and eigenvalues (representing the magnitude of variance along those directions).
4.  **Dimensionality Selection:** Utilizing scree plots (identifying the "elbow") or cumulative explained variance to determine how many principal components to retain.
5.  **Projection:** Transforming the original dataset into a new coordinate system, creating a simplified [[latent-space]] or [[embedding-space]].

### Comparisons with Other Techniques
*   **vs. LDA:** Unlike Linear Discriminant Analysis, PCA is an unsupervised technique and does not require class labels.
*   **vs. Factor Analysis:** While both minimize dimensionality, Factor Analysis targets latent structures and unmeasured underlying factors, whereas PCA focuses strictly on capturing maximum variance.
*   **vs. K-Means Clustering:** K-means groups data points by similarity, whereas PCA reduces feature dimensions.
*   **vs. t-SNE & UMAP:** PCA is linear and computationally inexpensive. Non-linear techniques (t-SNE/UMAP) focus on local structure visualization, whereas PCA preserves global variance and acts as a true feature extraction mechanism.

## Key claims

- PCA projects high-dimensional data onto a smaller feature space to minimize overfitting and multicollinearity. ([[phd/raw/www.ibm.com/pca#PCA is commonly used for data preprocessing for use with machine learning algorithms.]]) — "By projecting a high-dimensional dataset into a smaller feature space, PCA also minimizes, or altogether eliminates, common issues such as multicollinearity and overfitting."
- The first principal component captures the highest degree of variability, representing the maximum retained information. ([[phd/raw/www.ibm.com/pca#First principal component]]) — "The first principal component (PC1) is the direction in space along which the data points have the highest or most variance. It is the line that best represents the shape of the projected points."
- PCA is a linear technique, contrasting with non-linear dimensionality reduction algorithms like t-SNE and UMAP. ([[phd/raw/www.ibm.com/pca#There are many other dimensionality reduction techniques available]]) — "PCA is a linear technique, while other techniques such as t-SNE and UMAP are non-linear. This means that PCA is better suited for datasets with linear relationships between variables."
