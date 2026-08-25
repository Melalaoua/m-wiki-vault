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

In [[linear-regression]], the evaluation metric is defined by mean square error (MSE): the average squared error from ground truth and predicted value. A large MSE indicate sa poorly fit model on the training data, a low MSE indicates a well-fitted model on the training data
$$ MSE = (y_{pred} - y_{actual})²$$
Or expressed as a residual sum of squares:
$$RSS = \sum_{i=1}^n{(y_i-ŷ_i)²}$$
Take x and y (input with corresponding output). The true relationship with X and Y is nonlinear, a smooth curved U-shape like a sin-wave. We don't know the underlying function.

![[Pasted image 20260825114145.png]]

We want to build a model to predict Y by using X by trying to fit 3 models of increasing complexity : a linear model, a moderately complex polynomial model, and a very complex polynomial model. 

This nois introduces rnadomness, mimicking real-world data. A polynomial is a mathematical expression involving a sum of powers of X multiplied by coefficients.
$$ŷ = \beta_0 + \beta_1x $$

![[Pasted image 20260825114406.png]]

This model is **very simple** and assume the relationship between X and Y is linear :
- **Bias is high** : the model cannot capture the nonlinear pattern in the data.
- **Variance is low** : it is stable and doesn't change much with different datasets.
- **MSE = 0.2929 (high)**

> This is an example of underfitting.

A degree 4 polynomial is :
$$ŷ = \beta_0 + \beta_1x + \beta_2x²+\beta_3x³+\beta_4x⁴
$$
![[Pasted image 20260825114648.png]]

This model is complex enough to capture the curve of the data without being too sensitive to noise:
- **Bias is moderate** : The model can represent the true function fairly well.
- **Variance is moderate** : It doesn't overreact to small fluctuations in the data.
- **MSE = 0.0714**

This is the best performing model in this example.

A degree 25 polynomial is :
$$\sum$$