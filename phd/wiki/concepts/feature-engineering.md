---
type: concept
title: Feature enginering
aliases: []
tags:
  - concept
  - phd
updated: 2026-08-25
status: developing
---

# What is feature engineering?
*Preprocess raw data into a machine-readable format.*

Feature engineering is the process of creating predictive model features. A feature, also called a dimension, is an input variable used to generate model predictions.

> Model performance largely rests on the quality of data used during training, feature engineering is a crucial preprocessing technique that require selecting the most relevant aspects of raw training data for both the predictive task and model type under consideration.

Data scientists spend a large portion of time on data preparation and feature creation in order to create high-quality models. It can require much trial and error.

Feature engineering is not a linear process, it is an **iterative process**.


##### Feature transformation.
*Converting one feature type into another, more readable form for a particular model.*

- **Binning** : Transform continous, numerical values into categorical fetures. It sorts data points into a number of bins (i.e age demographics with 18-25, 25-30, ...). Once values binned, one can futher smooth the bins by means, medians, or boundaries.
  
- **One-hot encoding** . Inverse of binning, creates numerical features from categorical variables. First map the categorical features to binary representations, then mapping the feature in a matrix or vector space.
	An example of one-hot encoding is spam filtering classifcation in which the categories spam and not spam are converted to 1 and 0 respectively.


##### Feature extraction and selection.
Extraction is **combining variables into new, surrogate variables** or in order to reduce dimensions of the model's feature space.

