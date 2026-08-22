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
ML are built upon a system of linear equations. [[linear-regression]] is a simple yet powerful algorithm used for predicting continous values i.e *the process of finding the 'best fit' line or a plane that minimizes the error between predicted and actual values often boils down to solving a system of linear equations.*


##### Simple Example.
Predicting the house prices based on square footage, number of bedrooms. We use coefficients (weights) that need to be found to satisfy equations like :
$$price = w_1 \cdot square\ footage +w_2 \cdot number\ of\ bedrooms + b$$
where $w_1\ w_2 \ and \ b$ are the unknown coefficients to solve for.

this can be represented and solved using matrices. Techniques like "least squares" are used to find the approximate solutions to these systems when an exact solution doesn't exist, which is often the case with real-word noisy data.

> In other words, approximating a loss function is represented as a collection of linear equations that solved for with calculus.

More complex algorithms , such as those found in [[deep-learning]] and [[neural-networks]] heavily rely on operatoins like massive matrix multiplication for processing information through different layers. Each layer in a neural-network performs a linear transformation on its input data, which is essentially a matrix transformation where the input vector is multiplied by a weight matrix. This allows the network to learn complex patterns and relationships within the data.


#### Dimensionality reduction
real-world datasets contain large numer of features/variables for each data-point => *high-dimensional data*.

> Intuition says this makes everything more precise, but it makes learning harder. **High-dimensional data can be computationally expensive to process, memory-intensive to store and prone to [[overfitting]].

##### Curse of dimensionality
As dimensions grows, data points become increasingly sparse in the feature space, and the notion of "closeness" between points becomes less meaningful.

Dimensionality reduction is the process of transforming data from a high-dimensional space into a lower-dimensional one while preserving as much of the original structure and important information as possible.

Linear algebra is at the core of many dimensionality reduction techniques. [[principal-component-analysis]] uses concepts like **eigenvalues or eigeinvectors** to find new axes (principal components) that capture the maximum variance in the data, representing a meaningful attribute in the high dimensional dataset.

##### Example.
If we try describing thousands of customers with 100 different features each (age, income, spending in various product categories, etc...). Analyzing all 100 features at once would be slow and complex, and many of them may be redundant (interest in sport gear often overlaps with outdoor equipment). PCA can reduce the dataset to just 2 or 3 components that summarize most of the variation in customer behavior.

==**In short, dimensionality reduction is a way to distill complex data into its most informative parts, and linear algebra provides the mathematical machinery to make it possible.**==

Another powerful technique, [[singular-value-decomposition]] (SVD) is also related to eigendecomposition, SVD can be applied to any matrix (not just square matrices) and offers a more general way to decmopose a matrix into its constituent parts, revealing underlying structures and reducing dimensions effectively.



#### Optimization.
Linear Algebra is essential in optimization like [[gradient-descent]] used in [[neural-networks]] relying on linear algebra to calculate gradients (vector pointing in the direction of the steepest ascent of a function) and update model parameters iteratively.


The **determinant** of a square matrix is a single number that provides crucial information about the matrix. For example :
- a non-zero determinant indicates that the matrix is invertible (it has a corresponding matrix inversion operation), which is critical for solving systems of linear equations uniquely.
- If the determinant is zero, the system might have no unique solution or infinitely many, indicating issues like linear independence (where one vector in a set can be expressed as a linear combination of the others). 