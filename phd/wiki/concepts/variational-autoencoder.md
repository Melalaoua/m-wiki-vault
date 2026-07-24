---
type: concept
title: "Variational Autoencoder"
aliases: []
tags: [concept, personal]
updated: 2026-07-24
status: developing
---

# Variational Autoencoder

A [[Variational Autoencoder]] (VAE) is a probabilistic generative model first introduced by Diederik P. Kingma and Max Welling in 2013. Unlike deterministic autoencoders, VAEs map input data to a continuous [[Latent Space]] represented as probability distributions.

### Key Components
1.  **Encoder**: Maps high-dimensional inputs to distribution parameters (mean $\mu$ and standard deviation $\sigma$).
2.  **Bottleneck**: Represents the stochastic [[Latent Space]] using the parameterized distribution.
3.  **Decoder**: Reconstructs inputs from sampled latent points.

### Reparameterization Trick
To allow backpropagation through the stochastic bottleneck, VAEs formulate the latent variable $z$ as:
$$z = \mu + \epsilon \cdot \sigma$$
where $\epsilon \sim \mathcal{N}(0, I)$ is an external noise variable. This keeps the network's parameters differentiable.

### Contrast with Non-Generative Models
While VAEs minimize reconstruction loss to model data distributions, modern paradigms like the [[Joint-Embedding Predictive Architecture]] (JEPA) actively reject pixel-level reconstruction to avoid capturing irrelevant background details, focusing instead on abstract semantic predictability within [[World Models]].

Source: [[phd/wiki/sources/www2026variational|Variational autoencoder]]
