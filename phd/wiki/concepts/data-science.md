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
- 