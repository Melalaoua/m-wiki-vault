---
type: concept
title: "Energy-Based Models (EBM)"
aliases: []
tags: [concept, phd]
updated: 2026-08-21
status: developing
---

# Energy-Based Models (EBM)

# Energy-Based Models (EBM)

## Overview

Energy-Based Models constitute the mathematical framework this document uses to unify and analyze [[phd/wiki/concepts/self-supervised-learning|self-supervised learning]] methods, providing the theoretical substrate for training [[phd/wiki/concepts/joint-embedding-predictive-architecture|JEPA]] and its hierarchical variant. Rather than being a narrow architecture, an EBM in this paper's sense "designates a much broader category of models that treat the energy function as fundamental, and directly manipulate its landscape through learning." The framework is explicitly broad enough that "all traditional optimization-based learning methods can be interpreted as energy-based methods," including discriminative training methods for structure prediction problems.

The core formulation: an EBM is a scalar-valued function F(x, y) that produces low energy values when x and y are compatible, and higher values when they are not. This single formalism is used throughout the document to explain self-supervised learning, generative modeling, auto-encoders, and joint embedding methods as special cases distinguished mainly by how they avoid a shared pathology: energy collapse.

## Why EBMs over explicit prediction

The document motivates EBMs as a solution to a fundamental limitation of self-supervised learning: given an observed x, there may be an infinite number of compatible y values, so "it seems less inconvenient to merely ask the system to tell us if a proposed y is compatible with a given x" rather than requiring explicit prediction. This implicit-function formulation "enables the system to represent multi-modal dependencies in which multiple values of y are compatible with a given x," where the compatible set may be a single point, multiple discrete points, a manifold, or a collection thereof.

Crucially, "although many EBMs can easily be turned into probabilistic models, e.g. through a Gibbs distribution, this is not at all a necessity" — the framework does not require a probabilistic interpretation, giving it more flexibility than maximum-likelihood approaches.

## Latent-variable EBMs

To parameterize the set of possible relationships between x and compatible y values, the document introduces latent variables z, which "represent information about y that cannot be extracted from x." Inference then consists of finding the latent value that minimizes energy: ž = argmin_z E_w(x, y, z). After inference, z can be eliminated to yield a simplified energy Fw(x, y) = min_z E_w(x, y, z).

This latent-variable machinery underlies the document's treatment of uncertainty throughout — including how [[phd/wiki/concepts/world-model|world models]] represent multiple plausible future states and how the [[phd/wiki/concepts/actor-module|actor module]] handles [[phd/wiki/concepts/aleatoric-uncertainty|aleatoric]] and [[phd/wiki/concepts/epistemic-uncertainty|epistemic uncertainty]] during Mode-2 planning.

## Energy collapse: the central training problem

The document frames EBM training as fundamentally about avoiding **energy collapse**: "without a specific provision to ensure that Fw(x, y′) > Fw(x, y) whenever ŷ ≠ y, the energy landscape may suffer a collapse... the energy landscape could become 'flat', giving essentially the same energy to all values of y." Training an EBM requires devising a loss functional such that minimizing it makes the energy of true training pairs lower than the energy of non-matching alternatives.

The document analyzes collapse susceptibility across four architecture types:
- **Deterministic predictive/generative architectures** cannot collapse, since a single ỹ is produced for any x.
- **Generative latent-variable architectures** can collapse when the latent variable has excessive information capacity relative to the compatible-output set.
- **Auto-encoder architectures** can collapse when the representation sy has enough capacity to learn the identity function.
- **[[phd/wiki/concepts/joint-embedding-predictive-architecture|Joint Embedding Architectures]] (JEA)** can collapse when encoders ignore their inputs and produce constant, equal codes, giving the entire space zero energy.

## Two families of anti-collapse methods

The document's key organizing contribution is dividing EBM training into two approaches:

**Contrastive methods** push down energy on training samples while pulling up energy on "suitably-placed contrastive samples." Examples cataloged include Siamese networks, [[phd/wiki/concepts/denoising-auto-encoders|Denoising Auto-Encoders]] and Masked Auto-Encoders (contrastive samples via corruption), [[phd/wiki/concepts/generative-adversarial-networks|GANs]] (contrastive samples from a trainable generator), and modern instance-discrimination methods (PIRL, MoCo, SimCLR, CPT, DrLIM). The document formalizes a taxonomy of contrastive losses: Maximum Conditional Likelihood, [[phd/wiki/concepts/contrastive-divergence|Contrastive Divergence]] (MCMC sampling with detailed balance), pairwise hinge/triplet loss, min-hinge, square-hinge, square-exp, and distance-dependent hinge loss (which forces energy to grow at least quadratically with distance from the data manifold). The fundamental weakness identified: "the number of contrastive samples necessary to make an energy surface adopt a good shape may grow exponentially with the dimension of y space" — the curse of dimensionality.

**Regularized methods** instead minimize the volume of low-energy space directly, causing low-energy regions to "wrap around data-dense areas" without needing negative samples. The document judges these "much more promising in the long run... because they can eschew the curse of dimensionality that plagues contrastive methods." Examples include sparse modeling, sparse auto-encoders, and [[phd/wiki/concepts/variational-autoencoder|VAE]]. Mechanistically, regularization works by restricting information capacity: in latent-variable generative models by limiting z's capacity, in auto-encoders by limiting sy's capacity, and in JEAs by *maximizing* the information sx and sy carry about x and y (the opposite direction, since here the failure mode is codes that carry too little information).

The document notes these approaches are not mutually exclusive: "contrastive and regularized methods are not incompatible with each other, and can be used simultaneously on the same model."

## JEPA as an EBM instance

[[phd/wiki/concepts/joint-embedding-predictive-architecture|JEPA]] is presented as "a combination of the Joint Embedding Architecture and the Latent-Variable Generative Architecture," with energy defined as prediction error in representation space: E_w(x, y, z) = D(sy, Pred(sx, z)). JEPA's non-contrastive training regime is built directly on the EBM anti-collapse principles: (1) sx maximally informative about x, (2) sy maximally informative about y, (3) sy easily predictable from sx (enforced by the energy term itself), and (4) z minimal in information content — the last preventing the predictor from trivially copying z to zero out the energy. Criteria 1–2 prevent informational collapse of the encoders; criterion 4 prevents a distinct collapse mode where the latent absorbs all predictive burden. Minimizing z's information content is achieved via discretization (VQ-VAE-style), dimensionality/rank minimization, sparsification (L1 regularization, LISTA), or fuzzification (noisy AE, VAE).

The document explicitly names [[phd/wiki/concepts/sketched-isotropic-gaussian-regularizer|VICReg]] and Barlow Twins as concrete non-contrastive, regularized EBM criteria used for JEPA training, with VICReg further analyzed as "dimension-contrastive" rather than sample-contrastive — contrasting over representation components across a batch rather than over sample vectors.

## Notation and formal apparatus

The paper's architectural diagrams encode the EBM framework visually: filled circles denote observed variables or deterministic outputs, hollow circles denote latent variables to be inferred/sampled, red rectangles denote energy terms contributing additively to total system energy, and rounded rectangles denote differentiable deterministic functions (typically neural nets). Level sets Z_h of a latent regularizer R(z) define permissible latent configurations below a threshold, and the Gibbs-Boltzmann formula can convert an energy term into a probability distribution when needed. Amortized inference — training an encoder to predict approximate solutions to the latent-inference optimization problem — reduces inference cost but requires careful regularization of z to prevent the encoder from "cheating" by smuggling all of y's information through it.

## Significance to the overall architecture

EBM theory is what allows the document to treat energy as the single quantity flowing through the entire cognitive architecture: the [[phd/wiki/concepts/cost-module|cost module]]'s output (intrinsic cost plus trainable critic) is itself an energy, differentiable and backpropagable "through the other modules, particularly the world model, the actor and the perception, for planning, reasoning, and learning." In this sense EBM is the connective mathematical tissue between [[phd/wiki/concepts/self-supervised-learning|SSL]] training of the world model and the [[phd/wiki/concepts/energy-minimization|energy minimization]]-as-reasoning paradigm used by the actor during Mode-2 planning.

## Relevance to active projects

**[[phd/wiki/maps/thesis-topic-shift-world-models-vs-llms|Thesis Topic Shift: World Models vs LLMs]]**: This page is directly relevant to evaluating the strengths of [[phd/wiki/concepts/world-models|World Models]] relative to LLMs. The document argues that generative/token-based models (including LLMs) simplify uncertainty representation by discretizing over finite vocabularies, whereas EBM-based JEPA handles continuous, high-dimensional uncertainty (as in video or, by extension, physiological/genomic signals) by eliminating irrelevant information through learned encoders rather than by exhaustive generative modeling. The contrastive-vs-regularized distinction and the collapse-avoidance machinery are the technical foundation any pitch invoking JEPA/world-model superiority over LLMs for clinical or molecular diagnosis would need to cite, since they explain *why* JEPA-style architectures might generalize with less data than reward- or token-based approaches.

Source: [[phd/wiki/sources/phd202610356apathtowardsautonomousmach|10356_a_path_towards_autonomous_mach]]
