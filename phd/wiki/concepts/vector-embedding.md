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
- a *vector* is a *one-dimensional* (or first-degree or first-order) tensor, containing multiple scalars of the same type of data. For example, the weather model might represent the low, mean and high temperatures of that single day vector form as (25,30, 33). Each scalar component is a [[feature-engineering#What are features ?|feature]], a dimension, of the vector corresponding to a feature of that day's weather.
- a *tuple* is a first-order tensor containing scalars of more than one type of data. For example, a person's name, age and height might be represented in tuple form as (Jane, Smith, 31, 65).
- a *matrix* is a two-dimensional tensor, containing multiple vectors of the same type of data. It can be intuitively visualized as two-dimensional grid of scalars in which each row or column is a vector. For example, that weather model might represent the netire mont of june as a 3x30 matrix, in which each row is a feature vector describing an individual day's low, mean and high tempartures.
- *Tensors* with three or more dimensions, like the 3-dimensional tensors used to represent color images in computer visoin algorithms, are referred as *multidimensional arrays or N-dimensional tenors*

### Vectors versus embeddings.
Not necessarily the same thing.

an *embedding* is any numerical representation of data that captures its relevant qualities in a way that ML algorithms can process. **Data is embedding in $n$-dimensional space.** Data doesn't have to be embedded as a vector, but it's predominately is in modern ML.

### How does vector embedding work?
*embeddings transforms a data point (word, sentence, image) into a n-dimensional array of numbers, representing its features.*

Embeddings are obtained by training an embedding model on a large data set relevant to the task at hand or by using a pretrained model.

- **how vector embeddings represent data** : embeddings typically deal with high-dimensional data (commonly most nonnumerical information is high-dimensional). For instance a smiple 28x28 pixel B&W image can be represented as a 784-dimensional vector. 
	Efficient vector embedding
 
- **how vector embeddings can be compared :**
- **how models can be used to generate vector embeddings :**