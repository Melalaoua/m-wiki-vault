---
type: concept
title: Uncertainty Quantification
aliases: []
tags:
  - concept
  - phd
updated: 2026-08-25
status: developing
---

# What is uncertainty quantification ?
*All models are wrong, but some are useful* - George Box


Multiple types of uncertainty affecting [[machine-learning|models]] : random process or stochastic characteristics (**aleatoric uncertainty**), incomplete knowledge (**epistemic uncertianty**) or computational limitations.

> Uncertainty quantification (UQ)

UQ methods are important showing how error and unknowns affect final results, preventing the model from becoming overconfident.
> Data-driven uncertainty and model-driven uncertainty.

#### Sampling-based methods
Most commonly used techniques for UQ as it can handle any kind of model complexity. Provide an intuitive comprehensive uncertainty characterization.
- Generate many possible scenarios & sampling to build up statistical picture of what outcome are likely.
- Uses statistical analysis of many sample outputs to characterize uncertainty distributions.

##### Monte Carlo
- Monte Carlo simulation (latin hypercube sampling) requires fewer runs while still covering the input space well.

- Monte Carlo dropout is another technique that keeps the dropout active during prediction, running multiple forward passes to get a distribution of outputs.
	