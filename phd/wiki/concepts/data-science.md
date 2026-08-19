---
type: concept
title: Data Science
aliases: []
tags:
  - concept
  - phd
updated: 2026-08-12
status: developing
---

# What is statistical machine learning ?

Machine learning is built upon statistical techniques and mathematical tools (bayesian methods, linear, algebra, validation strategies). Whenever you're training a model, you're estimating parameters from data. When you test it : is this pattern real, or just random noise? How can we quantify error by using evaluation metrics ? These are statistical questions.

This note unpacks the **statisticall pillars** behind modern [[machine-learning]].


#### What is statistics ?
==Science of extracting insight from data==, it provides the mathematical foundation for understanding data behavior, guiding model choices and evaluating outcomes. **It transforms messy, noisy datasets into actionable intelligence.**

ML is built on top of statistical methods :
- [[supervised-learning]] uses regression or classification.
- [[unsupervised-learning]] uses clustering.
- [[reinforcement-learning]] uses tools rooted in statistical inference.

> Statistics enables quantification of uncertainty, generalization from samples and drawing conclusion about broader populations, all essential toward building trustworthy AI systems.

###### Descriptive statistics : basics.
Applying **==exploratory data analysis==** (EDA), before training models, relies on descriptive statistics to summarze key characteristics of the data. 
- **Mean (average)** : arithmetic average of values. Common in measuring centrality in loss functions like mean squared error (MSE).
- **Median** : the middle value when data is sorted. More robust to outliers than the mean.
- **Mode** : The most frequently ocurring value.
- **Standard deviation (SD)** : How spread out the values are from the mean. A low SD implies that data points are clustered near the mean. Higher SD = greater variability.
- **Interquartile range** (IQR) : The range between the 75th and 25th percentiles (Q3 - Q1)  : captures the middle 50% of the data and is useful for detecting outliers.