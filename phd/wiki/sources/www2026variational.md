---
type: source
title: "Variational autoencoder"
citekey: www2026variational
source_type: article
captured: 2026-07-24
site: www.ibm.com
url: https://www.ibm.com/think/topics/variational-autoencoder
aliases: []
tags: [source, personal]
updated: 2026-07-24
status: developing
---

# Variational autoencoder

Original: [[phd/raw/www.ibm.com/variational-autoencoder]]

The [[Variational Autoencoder]] (VAE) is a foundational deep generative model archetype introduced by Diederik P. Kingma and Max Welling in their seminal 2013 paper, "Auto-Encoding Variational Bayes". Unlike deterministic autoencoders that compress input data into fixed discrete codes, a VAE maps inputs to a continuous and probabilistic [[Latent Space]]. This enables VAEs to act as powerful generative systems capable of synthesizing novel variations of their training data, with wide-ranging applications spanning from image synthesis and anomaly detection to the molecular generation of drug compounds.

### Core Architecture
Like vanilla autoencoders, a VAE is composed of:
*   An **Encoder**: A neural network that compresses high-dimensional inputs into a representation of latent variables.
*   A **Bottleneck**: The lower-dimensional [[Embedding Space]] containing the compressed latent representation.
*   A **Decoder**: A neural network that reconstructs the original input data using vectors sampled from the bottleneck.

However, VAEs model the bottleneck probabilistically. For each latent attribute, the encoder outputs a vector of means ($\mu$) and a vector of standard deviations ($\sigma$), defining a posterior probability distribution $p(z|x)$ over the latent space.

### Optimization and Mathematical Framework
VAEs are optimized using a joint loss function that maximizes the Evidence Lower Bound (ELBO). This combines two principal objectives:
1.  **Reconstruction Loss**: Measures the difference between the original input and the decoder's output (typically via mean-squared error or cross-entropy loss).
2.  **Kullback-Leibler (KL) Divergence**: A regularization term that measures how much the encoded distribution diverges from a target prior distribution (usually a standard normal Gaussian distribution). Minimizing KL divergence ensures that the [[Latent Space]] possesses two critical properties: **continuity** (nearby points decode to similar content) and **completeness** (any sampled point in the space yields a meaningful reconstruction).

### The Reparameterization Trick
Because sampling a latent vector $z$ directly from the distribution $(\mu, \sigma)$ is a stochastic process, it lacks a derivative. This makes backpropagation impossible. To circumvent this, the **reparameterization trick** reformulates the sampling by introducing an auxiliary noise variable $\epsilon \sim \mathcal{N}(0, I)$. The latent variable is computed as:
$$z = \mu + \epsilon \odot \sigma$$
Since the randomness is isolated within $\epsilon$, gradients can flow directly through $\mu$ and $\sigma$, allowing standard gradient descent algorithms (such as Adam) to optimize the network's parameters.

### Variations and Competitors
*   **Conditional VAEs (CVAEs)**: Introduce supervised or semi-supervised labels during training, allowing users to direct the generative output of the decoder (e.g., generating a specific handwritten digit).
*   **Generative Adversarial Networks (GANs)**: Train a generator against an adversarial discriminator. While GANs yield sharper visual outputs than the typically blurry reconstructions of VAEs, they are notoriously unstable to train compared to the robust, ELBO-optimized framework of VAEs.
*   **VAE-GANs**: A hybrid model substituting the reconstruction loss of a standard VAE with a discriminator network to reduce blurriness while preserving training stability.

## Key claims

- VAEs represent the latent space as a continuous, probabilistic distribution rather than a fixed discrete vector. ([[phd/raw/www.ibm.com/variational-autoencoder#Variational autoencoder]]) — "However, whereas most autoencoder architectures encode a discrete, fixed representation of latent variables, VAEs encode a continuous, probabilistic representation of that latent space."
- The reparameterization trick allows stochastic models to remain differentiable for backpropagation. ([[phd/raw/www.ibm.com/variational-autoencoder#The reparameterization trick]]) — "This paper also popularized what they called the reparameterization trick, an important machine‑learning technique that enables the use of randomness as a model input without compromising the model’s differentiability."
- KL divergence regularizes latent space to enforce continuity and completeness. ([[phd/raw/www.ibm.com/variational-autoencoder#Kullback-Leibler divergence]]) — "Minimizing the KL divergence between the learned distribution of latent variables and a Gaussian distribution whose values range from 0–1 forces the learned encoding of latent variables to follow a normal distribution."
