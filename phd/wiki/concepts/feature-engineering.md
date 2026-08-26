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
Extraction is creating new dimensional space for a model by **combining variables into new, surrogate variables** or in order to reduce dimensions of the model's feature space.

Selection is **selecting a subset of the most relevant features** to represent a model.

Both are a form of [[linear-algebra#Dimensionality reduction|dimensionality reduction]] and suitable for regression problems with a large number of features and limited available data samples.

- [[principal-component-analysis]] (PCA) is a common feature extraction method that combines and transforms a dataset's original features to produce new features called *principal components.* PCA selects a subset of variables from a model that together comprise the majority or all of the variance present in the model's original set of variables. PCA then projects data onto a new space defined by this subset of variables.
- **Linear discriminant analysis**  (LDA) : ostensibly similar to PCA in that it projects model data onto a new, lower, dimensional space. As in PCA, this model's space dimensions (or features) are derived from the initial model's features. LDA differs in its concern for retaining classification labels in the original dataset. PCA produces new component variables, LDA produces component variables primarily intended to maximize class difference in the data.

##### Feature scaling.
*Also called **feature normalization***

Rescale features and limit the impact of large scales on models, it transforms data in terms of range and distribution.

- **Min-max scaling** : rescales all values for a given feature so that they fall between specified minimum and maximum values (often 0 and 1). Each data point’s value for the selected feature (represented by _x_) is computed against the decided minimum and maximum feature values, _min(x)_ and _max(x)_ respectively, which produces the new feature value for that data point (represented by _x̃_ ). Min-max scaling is calculated using the formula:
	$$x̃ = \frac{x-min(x)}{max(x)-min(x)}$$

- **Z-core scaling** : Literature also refers to this as **standardization and variance scaling**. Whereas min-max scaling scales feature values to fit within the designated minimum and maximum values, z-score scaling rescale feature so that they have a shared standard deviation of 1 with a mean of 0. Z-score scaling si represented by the formula : 
	$$x̃=\frac{x-mean(x)}{sqrt(var(x))}$$