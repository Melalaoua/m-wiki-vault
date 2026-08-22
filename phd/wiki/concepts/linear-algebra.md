---
type: concept
title: Linear Algebra
aliases: []
tags:
  - concept
  - phd
updated: 2026-08-22
status: developing
---

# What is linear algebra for machine learning ?

Linear algebra involves the use of mathematical operations to represent and manipulate data, parameters and computations inside [[machine-learning|ML]] models. It provides the language and tools to express how data flows through models and how models "learn".

> powerful modern ML algos and genAI are powered by linear algebra.


- Data is rarely a simple, single number. Instead data often comes in the form of datasets : collections of messy data points.
- Linear algebra provides the tools to organize, manipulate and analyze this data efficiently.
- Manipulates objects like vectors, matrices, tensors to represent structured (often tabular data) and unstructured data like images or videos. 

> - An image can be represented as a matrix of pixel values. 
> - A collection of features describing a house (such as neigborhood, age, square footage) can be represented as a vector in a linear regression model.

#### Key concepts.
*The tools to represent and work with data in a structured forms.*

- **==Scalar==** : simplest building block, a single numerical value (i.e 5 or 2.3). => *often represent parameters, scaling factors, or single measurements*.
- **==Vector==** : Ordered array of numbers (column or row). => *Can represent anything from a list of features to the coordinates in space.*
- **==Matrix**== : Two-dimensional array of numbers (row and columns).Dataset where each row is a data point and each column is a feature naturally forms a matrix. => *Central to linear algebra because allow efficient storage of data + operations like ==scalar multiplication== (multiplying every element of a matrix by a constant number) and ==matrix multiplication (combining two matrix to apply transformation or compute relationship== are pervasive in algos.* 
- **==Tensor==** : Generalization of scalars, vectors and matrices to higher dimensions. => *an image might be stored as a 3D tensor where height, width and color channels form three separate axes.*

![[Pasted image 20260822133456.png]]

> Most ML workflows start by organizing data into numerical formats, and each structure (scalar, vector, matrix & tensor) serves a different purpose

#### Understanding algorithms.
ML are built upon a system of linear equations. [[linear-regression]] is a simple yet powerful algorithm used for predicting continous values i.e *the process of f*