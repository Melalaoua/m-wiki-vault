---
type: concept
title: Latent Space
aliases: []
tags:
  - concept
  - phd
updated: 2026-07-24
status: stable
---

# Latent Space

*A compressed representation of data points that preserves only essential features that inform the input's data underlying structure.*

Mapping data points to latent space can express complex data in an efficient and meaningful way, enhancing the ability of machine learning models to understand and manipulate it while reducing computational requirements.

Encoding latent space representations typically entails some degree of [[linear-algebra#Dimensionality reduction|dimensionality reduction]] : the compression of high-dimensional data down to a lower-dimensional space that omits irrelevant or redundant information.

Examples : 
- [[phd/wiki/concepts/variational-autoencoder|variational-autoencoder]] and [[phd/wiki/concepts/generative-adversarial-networks|generative adversarial networks (GANs)]] compute the latent space of training data to then interpolate from it to generate new data samples.
- Computer vision models trained for classification tasks such as object detection or image segmentation map input data to latent space to isolate its qualities that are relevant to making accurate predictions.
- [[large-language-models]] (LLMs), from embedding models that enable semantic search to autoregressive models such as [[ChatGPT]] manipulate latent space to explore complex connections between different words in specific contexts.


#### What does "latent space" mean ?
*The word space takes on a more varied meaning in the context of machine learning that in general language*

Broadly speaking a *space* in ML refers to a specific mode of mapping, comparing or sampling data points : 
- The 'input space' is the range of possibilities included in the input data.
- The 'output space' is the range of possibilities for the model's output.
- 'pixel space' is the range of possibilities for numerical pixel values.
- In [[reinforcement-learning]], the 'action space' is the range of possible actions that could be taken next.

Mathematically speaking, a *space* is primarily defined by what its dimensions correspond to (i.e which features/variables are being used to describe data points in that space). 

> When data points are mapped to a specific space, data points with similar values for the variables that define the space will be similar to 

In machine learning, a **latent space** is an abstract, lower-dimensional space that captures the compressed representation of high-dimensional input data, filtering out noise to retain essential attributes [[phd/wiki/sources/www2026latent|Latent and Embedding Space]] [[phd/wiki/sources/www2026variational|Variational autoencoder]]. This concept is foundational to environment-simulating systems, such as [[world-models]] [[phd/wiki/sources/www2026latent|Latent and Embedding Space]].\n\nTo map raw data into these compressed representations, both linear and non-linear methods are utilized. Classical linear approaches, most notably [[principal-component-analysis]] (PCA) [[phd/wiki/sources/www2026pca|PCA]], transform raw features into orthogonal coordinate systems representing a linear latent space of maximum variance. In contrast, deep learning architectures model highly non-linear manifolds. Traditional [[Autoencoder]]s, for instance, map inputs to discrete, fixed vectors within this space [[phd/wiki/sources/www2026latent|Latent and Embedding Space]] [[phd/wiki/sources/www2026variational|Variational autoencoder]].

In contrast to discrete mappings, a [[phd/wiki/concepts/variational-autoencoder|variational-autoencoder]] structures a continuous, probabilistic [[latent-space]] by encoding inputs as the parameters of a probability distribution, typically a Gaussian distribution characterized by mean $\mu$ and variance $\sigma$ [[phd/wiki/sources/www2026variational|Variational autoencoder]]. This probabilistic formulation guarantees continuity—where nearby latent points decode to structurally similar outputs—and completeness, meaning any sampled point yields meaningful data [[phd/wiki/sources/www2026variational|Variational autoencoder]]. To organize the geometry of these spaces, prevent overfitting, and enable smooth interpolation, regularization methods like KL-divergence minimization or the [[sketched-isotropic-gaussian-regularizer]] are utilized [[phd/wiki/sources/www2026variational|Variational autoencoder]].
