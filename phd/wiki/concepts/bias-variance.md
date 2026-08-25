---
type: concept
title: Bias-Variance tradeoff
aliases: []
tags:
  - concept
  - phd
updated: 2026-08-25
status: developing
---
# Introduction to bias-variance tradeoff
Bias and variance represent two source of prediction error.

- **Bias : how far off predictions are from the true values due to overly simplistic assumptions.**
- **Variance : how much predictions fluctuate based on different training data.**

> Model with high bias are prone to underfitting, models with high variance are prone to overfitting.

#### Tradeoff illustrated
In predictive models such as linear regression or K-nearest neighbor (KNN), bias and variance are interdependent.

- High-bias models tend to make strong assumptions about the form of data and cause underfitting. **An overly simplistic model tends to have high bias and low variance**
- High-variance models are sensitive to noise in the training data and cause overfitting. **A model with complex architecture and more parameters tends to have high variance and low bias**

In [[linear-regression]], the evaluation metric is defined by mean square error (MSE): the average squared error from ground truth and predicted value. A large MSE indicate sa poorly fit model on the training data, a low MSE 