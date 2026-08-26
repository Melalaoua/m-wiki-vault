---
type: concept
title: Vector embedding
aliases: []
tags:
  - concept
  - phd
updated: 2026-08-26
status: developing
---

# What is vector embedding?
*Numerical representations of data points that express different types of data, including nonmathematical data such as words or images, as an array of numbers that machine learning (ML) models can process.*

Any data that an AI model operates on, including unstructured data such as text, audio or images, must be expressed numerically. Vector embedding is a way to convert an unstructured data point into an array of numbers that still expresses that data's original meaning.

> Intuitively, the more similar two real-world data points, the more similar their respective vector embeddings should be. Dissimilar data points should have dissimilar vector embeddings.

Vector embeddings can be used as inputs to models that perform useful real-world tasks through mathematical operations that compare, transform, combine, sort or otherwise manipulate those numerical representations.

Vector embeddings thus underpin nearly all modern [[machine-learning]], powering models used in the fields of NLP and computer vision, and serving as the fundamental building blocks of genAI.

### What is a vector ?
[[linear-algebra#Key concepts.|vectors]] belong to the larger category of tensors. In ML, "tensor" is used as a generic form term for an array of numbers (or an array of arrays of numbers) in $n$-dimensional space, functioning like a mathematical bookkepeing device for data.

**Certain words are used differently in an ML context than in everyday language or mathematical settings**. "Vector" itself, for example, has a more specific connotation in physics-where it usually refers to a quantity with both magnitude and direction-- than it does in ML.

Likewise, **dimension** has different implications in ML, depend on the context. 
- For a tensor it refers to how many arrays that tensor contains.
- For a vector, it refers to how many components (indiv. numbers) it contains.

- a *scalar* is a zero-dimensional tensor, containing a single number.
- a *vector* is a *one-dimensional* (or first-degree or first-order) tensor, containing multiple scalars of the same type of data. (i.e (25, 30, 33) in weather r)