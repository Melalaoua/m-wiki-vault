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

A "feature" refers to an individual measurable property or characteristic of a data point: a specific attriute of the data that helps describe the phenomenon being observed.

Feature engineering is the process of creating predictive model features. A feature, also called a dimension, is an input variable used to generate model predictions.

> Model performance largely rests on the quality of data used during training, feature engineering is a crucial preprocessing technique that require selecting the most relevant aspects of raw training data for both the predictive task and model type under consideration.

Data scientists spend a large portion of time on data preparation and feature creation in order to create high-quality models. It can require much trial and error.

Feature engineering is not a linear process, it is an **iterative process**.

### What are features ? 

A definable quality of the items in a dataset, also known as variables because their values can change from one data point to the next, and attributes because they characterize the data points in the dataset.

Features can be independant variables, dependent variables that derive their value from independent variables or combined attributes that are compiled from multiple other features.

Features can be broadly categorized into numerical or categorical variables : 
- **Numerical variables** : length, size, age, duration, ...
- **Categorical variables** : name, job title, location, ...

### Feature transformation.
*Converting one feature type into another, more readable form for a particular model.*

- **Binning** : Transform continous, numerical values into categorical fetures. It sorts data points into a number of bins (i.e age demographics with 18-25, 25-30, ...). Once values binned, one can futher smooth the bins by means, medians, or boundaries.
  
- **One-hot encoding** . Inverse of binning, creates numerical features from categorical variables. First map the categorical features to binary representations, then mapping the feature in a matrix or vector space.
	An example of one-hot encoding is spam filtering classifcation in which the categories spam and not spam are converted to 1 and 0 respectively.


### Feature extraction and selection.
Extraction is creating new dimensional space for a model by **combining variables into new, surrogate variables** or in order to reduce dimensions of the model's feature space.

Selection is **selecting a subset of the most relevant features** to represent a model.

Both are a form of [[linear-algebra#Dimensionality reduction|dimensionality reduction]] and suitable for regression problems with a large number of features and limited available data samples.

- [[principal-component-analysis]] (PCA) is a common feature extraction method that combines and transforms a dataset's original features to produce new features called *principal components.* PCA selects a subset of variables from a model that together comprise the majority or all of the variance present in the model's original set of variables. PCA then projects data onto a new space defined by this subset of variables.
- **Linear discriminant analysis**  (LDA) : ostensibly similar to PCA in that it projects model data onto a new, lower, dimensional space. As in PCA, this model's space dimensions (or features) are derived from the initial model's features. LDA differs in its concern for retaining classification labels in the original dataset. PCA produces new component variables, LDA produces component variables primarily intended to maximize class difference in the data.

#### Feature extraction.
During the extraction process, unstructured data is converted into a more structured and usable format to enance the data quality and model interpretability.

Data is difficult to work with when the number of features or covariates, exceeds the number of independent data points. This type of data is considered high-dimensional data.[3](https://www.ibm.com/think/topics/feature-extraction#f03) Feature extraction can be considered a [dimensionality reduction](https://www.ibm.com/think/topics/dimensionality-reduction) technique.[4](https://www.ibm.com/think/topics/feature-extraction#f04)  
  
This is crucial when working with large datasets or datasets from multiple modalities. The more extracted features the model must manage, the less proficient and performant it is.[5](https://www.ibm.com/think/topics/feature-extraction#f05) Common tasks that rely on efficient feature extraction include image processing, natural language processing (NLP) and signal processing.

First, the model takes in input data, then the feature extractor transforms the data into a numerical representation that can be used to compute the dimensionality reduction methods for feature extraction. These representations are stored in feature vectors for the model to perform algorithms for data reduction.

> After extraction, it is sometimes necessary to standardize the data using feature normalization.

Most modern AI models perform automatic feature extraction, but it is still useful to understand the diverse ways of handling it. Here are a few common feature extractions methods used :
- **Principal component analysis (PCA)** : Reduces the number of features in large datasets to principal components. Popular because of its ability to create original data that is uncorrelated.
- 

#### Feature Selection.
*Choosing the features to use for the model.*

Identifying the most important, impactful and nonredundant features in the dataset. Reducing the number of features enhances model efficiency and boost performance.

Example, in a database of employees, input features can include age, location, salary, title, performance metrics and duration of employment. An employer can use these variables to generate a target combined attribute representing an employee's likelihood of leaving for a better offer.

> Before feature selection, feature extraction transforms raw data into numerical features that machine learning models can use.

##### Supervised feature selection methods.
[[supervised-learning]] feature selection uses the target variable to determine the most important features. Because the data features are already identified, the task is about indentifying which input variables most directly affect the target variable. Correlation is the primary criterion when assessing the most important features.

- **Filter Methods** : a group of feature selection techniques that are solely concrned with the data itself and do not directly consider model performance optimization. Input variables are assessed independently against the target variable to determine which has the highest correlation.
	- *Information gain* : measures how important the presence or absence of a feature is in determining the target variable by the degree of entropy reduction.
	- *Mutual information* : assesses the dependence between variables by measuring the information obtained about on through the other.
	- *Chi-square test* : assesses the relationship between two categorical variables by comparing observed to expected values.
	- *Fisher's score* : Uses derivatives to calculate the relative importance of each feature for classifying data. A higher score indicates greater influence.
	- *Pearson's correlation coefficient* : Quantifies the relationship between two continuous variables with a score ranging from -1 to 1.
	- *Variance threshold* : Removes all features that fall under a minimum degree of variance because features with more variances are likely to contain more useful information.
	- *Missing value ratio* : Calculates the percentages of instances in a dataset for which a certain feature is missing or has a null value. If too many instances are missing a feature, it is not likely to be useful.
	- *ANOVA (analysis of variance)* : Determines whether different feature values affect the value of the target variable.

- **Wrapper methods** : train the machine learning algorithm with various subsets of features, adding or removing features and testing the results at each iteration. The goal is to find the feature that leads to optimal model performance. **Test all the possible feature combination** known as greedy algorithms : 
	- *Forward selection* : Starts with an empty feature set and gradually adds new features until the optimal set is found.
	- *Backward selection* : remove features one-by-one.
	- *Exhaustive feature selection* : Tests every possible combination of features to find the overall best one by optimizing a specified performance metric.
	- *Recursive feature elimination (RFE)* : A type of backward selection that begins with an initial feature space and eliminates or adds features after each iteration based on their relative importance.
	- *Recursive feature elimination with cross-validation* : variation of RFE that uses cross-validation, which test model on unseen data, to select the best performing feature set. It's a common [[large-language-models]] evaluation technique.

- **Embedded methods** : As the model undergoes training, it uses various mechanisms to detect underperforming features and discard those from future iterations. Many embedded methods revolve around regularization, which penalize features based on a preset coefficient threshold : 
	- *[[bias-variance#L1 regularization (lasso)|LASSO regression (L1 regression)]]* : adds a penalty to the loss function for high value correlated coefficients, moving them toward a value of 0. The greater the penalization, the more features are removed from the feature space.
	- *Random forest importance* : builds hundreds of decision trees, each with a random selection of data points and features. Each tree is assessed by how well it divides the data points. The better the results, the more important the feature or features in that tree are considered to be.
	- *Gradient boosting* : Adds predictors in sequence to an ensemble with each iteration correcting the errors of the previous one.

##### Unsupervised feature selection methods.
With [[unsupervised-learning]], models figure out data features, patterns and relationship on their own.

One unsupervised feature selection method is [[principal-component-analysis]] which reduces the dimensionality of large datasets by transforming potentially correlated variables into a smaller set of variables.
Others techniques include independent component analysis (ICA) which separates multivariate data into individual components that are statistically independent, and[[phd/wiki/concepts/variational-autoencoder|autoencoders]].

Widely used with [[transformers]] architectures, an autoencoder is a type of neural network that learns to compress and then reconstruct data. In doing so, autoencoders discover [[latent-space|latent variables]]  (those which are not directly observable, but that strongly affect data distribution.)

##### Choosing a feature selection method.
- **Numerical input, numerical output** : When inputs and outputs are both numerical, this indicates a [[linear-regression|regression]] predictive problem. In theses cases, correlation coefficients, such as Pearson's correlation coefficient, are an ideal feature selection method.

- **Numerical input, categorical output** : [[logistic-regression]] models classify inputs into discrete categorial outputs. In this classifications problem, correlation-based feature selection methods that support categorical target variables can be used. These inlucde ANOVA for linear regression models and Kendall's coefficient of rank correlation for nonlinear tasks.

- **Categorical input, numerical output** : This rare type of challenge can also be solved with correlation methods that support categorical variables.

- **Categorical input, categorical output** : Classificaiton problems with categorical input and target variables lend themselves to the chi-square methods or information gain techniques.

Other factors to consider include the size of the dataset and feature space, feature complexity and model type. Filter methods can quickly eliminate a large portion of irrelevant features, but struggle with complex feature interactions. In these cases, wrapper and embedded methods might be more suitable.

### Feature scaling.
*Also called **feature normalization***

Rescale features and limit the impact of large scales on models, it transforms data in terms of range and distribution.

- **Min-max scaling** : rescales all values for a given feature so that they fall between specified minimum and maximum values (often 0 and 1). Each data point’s value for the selected feature (represented by _x_) is computed against the decided minimum and maximum feature values, _min(x)_ and _max(x)_ respectively, which produces the new feature value for that data point (represented by _x̃_ ). Min-max scaling is calculated using the formula:
	$$x̃ = \frac{x-min(x)}{max(x)-min(x)}$$

- **Z-core scaling** : Literature also refers to this as **standardization and variance scaling**. Whereas min-max scaling scales feature values to fit within the designated minimum and maximum values, z-score scaling rescale feature so that they have a shared standard deviation of 1 with a mean of 0. Z-score scaling si represented by the formula : 
	$$x̃=\frac{x-mean(x)}{sqrt(var(x))}$$
	Here, a given feature value (x) is computed against the rescaled feature's mean and divided by the standardized standard deviation. Z-score scaling can be useful when implementing feature extraction methods like PCA and LDA, as these two methods require features to share the same scale.


