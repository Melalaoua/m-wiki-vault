---
type: concept
title: "Joint-Embedding Predictive Architecture"
aliases: []
tags: [concept, phd]
updated: 2026-08-21
status: stable
contradiction: true
---

# Joint-Embedding Predictive Architecture

A **Joint-Embedding Predictive Architecture (JEPA)** is a machine learning architecture, conceptualized by Yann LeCun, that ==learns representations by predicting the latent embedding of a future (or otherwise related) state from the latent embedding of a current state==, **rather than reconstructing high-dimensional raw observations**.

LeCun's original proposal, in "A Path Towards Autonomous Machine Intelligence" ([[phd/wiki/sources/phd202610356apathtowardsautonomousmach|10356_a_path_towards_autonomous_mach]]), formalizes JEPA's energy function explicitly as a prediction error computed in representation space rather than input space: 
$$E_w(x, y, z) = D(s_y, Pred(s_x, z))$$where $s_x = Enc(x)$ and $s_y = Enc(y)$. 

The architecture is framed as a combination of a [[phd/wiki/concepts/joint-embedding-architecture|joint-embedding-architecture]] and a latent-variable generative architecture, and is explicitly non-generative — it predicts the representation of `y`, not `y` itself. This is what the paper argues makes it preferable to pixel-level generative models: in a video-prediction scenario it is "essentially impossible to predict every pixel value of every future frame," but abstract representations discard exactly the irrelevant, unpredictable detail.

A major challenge in JEPAs is preventing representation collapse. Historically this has been addressed with stop-gradients or EMAs, but more recently through direct regularization such as the [[sketched-isotropic-gaussian-regularizer]]. 

LeCun's paper spells out a non-contrastive training principle as four simultaneous criteria that motivate this family of fixes: 
1. $s_x$ should be maximally informative about $x$.
2. $s_y$ should be maximally informative about $y$. 
3. $s_y$ should be easily predictable from $s_x$.
4. The latent variable $z$ should carry minimal information content. 

(1) and (2) block collapse of the [[phd/wiki/concepts/joint-embedding-architecture|joint-embedding-architecture]] into constant, uninformative codes; 
(3) is enforced directly by the energy/distance term; 
(4) blocks a distinct collapse mode in which an overly expressive $z$ lets the predictor ignore $s_x$ entirely (e.g., if $z$ matches $s_y$ dimension, the predictor can simply copy $z$ onto its output, driving energy to zero for any input).

> Anti-collapse technique were found such as [[phd/wiki/concepts/sketched-isotropic-gaussian-regularizer|sketched-isotropic-gaussian-regularizer]] — the paper catalogs the general family of such fixes as discretization/quantization (VQ-VAE), dimensionality/rank minimization (Implicit Rank-Minimizing AE), sparsification (LISTA, sparse coding), and fuzzyfication (noisy AE, [[phd/wiki/concepts/variational-autoencoder|variational-autoencoder]]).


Multi-modality — representing several plausible futures for one input — is achieved either through encoder invariance (mapping multiple compatible `y` to the same `sy`) or through the latent `z` itself, sampled or optimized at inference/planning time.

[[phd/wiki/concepts/vicreg|vicreg]] and Barlow Twins are named as the concrete non-contrastive losses used to instantiate the four points state before in practice, with VICReg characterized as "dimension-contrastive" (decorrelating representation components over a batch) rather than sample-contrastive.

JEPA is positioned as the central technical proposal of LeCun's cognitive architecture because it underlies the Hierarchical [[phd/wiki/concepts/world-models|World Models]] (H-JEPA) needed for the full system: stacked JEPA levels with temporal pooling are proposed to support prediction at multiple time scales and abstraction levels (e.g., short-term detailed vehicle trajectory vs. long-term arrival-time estimates), feeding into the actor, cost, and configurator modules for hierarchical model-predictive-control-style planning under uncertainty.

Separately, [[phd/wiki/sources/phd2026leworldmodel|LeWorldModel: Stable End-to-End Joint-Embedding Predictive Architecture from Pixels]] treats JEPA as a concrete, trainable end-to-end architecture operating directly from pixels, with stability of training (i.e., avoiding collapse) as its central practical concern, addressed via the [[sketched-isotropic-gaussian-regularizer]] noted above.

## Contradictions

- ⚠️ contradicts [[phd/wiki/sources/phd202610356apathtowardsautonomousmach|10356_a_path_towards_autonomous_mach]] (captured 2026-08-21): "A major challenge in JEPAs is preventing representation collapse, historically addressed with stop-gradients or EMAs, but more recently through direct regularization like the sketched-isotropic-gaussian-regularizer." vs "JEPA can be trained with non-contrastive methods using four criteria: maximize information in sx, maximize information in sy, make sy predictable from sx, and minimize information in z; VICReg and Barlow Twins are examples of non-contrastive criteria for JEPA training." — Existing page frames collapse-prevention primarily via stop-gradient/EMA (contrastive-style asymmetric tricks) with newer sketched-isotropic-gaussian-regularizer; incoming source instead frames JEPA's collapse prevention as fundamentally regularized/non-contrastive (VICReg, Barlow Twins) rather than via stop-gradient/EMA methods, a differing account of the primary anti-collapse mechanism.
