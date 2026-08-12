---
type: concept
title: Unsupervised Learning
aliases: []
tags:
  - concept
  - personal
updated: 2026-08-12
status: developing
---

# Unsupervised learning

Models discern intrinsic patterns in unlabeled data : similarities, correlations or potential groupings. They are useful when patterns aren't apparent to the human eye. 

Unsupervised doesnt' assume the preexistence of a known "correct output".

- [[clustering]] : partition unlabeled data points into clusters (groupings), based on their proximity or similarity. (market segmentation, fraud detection). Prominent clustering algorithms include [[k-means]], [[gaussian-mixture-models]].
- [[association-algorithms]] : discern correlation for instance between action and certains conditions.
- [[dimensionality-reduction]] : reduce the complexity of data points by representing them with a smaller number of features while preserving their meaningful characteristics. Prominent dimensionality reduction algorithm include [[phd/wiki/concepts/variational-autoencoder|auto-encoder]], [[principal-component-analysis]] (PCA), [[t-distributed-stochastic-neighbor-embedding]] (t-SNE)

Unsupervised learning somewhat "optimizes" themsevles. The challenges lies in data-preprocessing and properly tuning hyperparameters 



### Unsupervised learning algorithms.
There are three fundamental subsets of unsupervised learning algorithms.

#### Clustering algorithms.
They partition unlabeled data points into "clusters" based on their proximity or similarity to one another.

- **==K-means clustering==** : partitions data in to k clusters in a given data point will be assigned to the cluster whose center (centroid) it's closes to. Each data point is assigned to the cluster of the nearest centroid. Each centroid is then relocated to the position representing the average (_mean_) of all the data points that were just assigned to it; Rinse & repeat.


#### Association algorithms.
Identify correlations between variables in large datasets, used prominently in task like market basket analysis or product recommendation engines.


#### Dimensionality reduction algorithm.
Take a data point and output a more efficient representation of that data point. They're designed to learn a mapping of high dimensional data points to a space where they can be accurately described using fewer features.

- [[principal-component-analysis]] : 