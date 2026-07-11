---
type: source
title: "LeWorldModel: Stable End-to-End Joint-Embedding Predictive Architecture from Pixels"
citekey: phd2026leworldmodel
source_type: pdf
captured: 2026-07-11
site: phd
url: 
aliases: []
tags: [source, phd]
updated: 2026-07-11
status: developing
---

# LeWorldModel: Stable End-to-End Joint-Embedding Predictive Architecture from Pixels

Original: [[phd/raw/phd/2603.19312v3.pdf]]

This paper introduces [[LeWorldModel]] (LeWM), an end-to-end [[Joint-Embedding Predictive Architecture]] (JEPA) capable of stable training from raw pixels. It streamlines the learning of [[World Models]] for continuous control by reducing the optimization objective to just two terms: a standard next-embedding prediction loss, and the [[Sketched-Isotropic-Gaussian Regularizer]] (SIGReg). The latter explicitly enforces Gaussian-distributed latent embeddings to prevent representation collapse, bypassing the need for heuristics like stop-gradients, exponential moving averages, or frozen pre-trained encoders.

LeWM demonstrates strong efficiency and performance on downstream 2D and 3D control tasks (e.g., PushT, OGBench-Cube). It plans up to 48x faster than foundation-model-based approaches like [[DINO-WM]] and relies on only 15M parameters. Furthermore, without explicit temporal smoothing, LeWM exhibits emergent temporal latent path straightening. Through a [[Violation of Expectation]] evaluation, the authors show the model robustly detects physical impossibilities (like teleporting objects), indicating a learned internal representation of physical dynamics. Added as part of [[PhD]] literature review.

## Key claims

- LeWM trains stably from raw pixels using only a two-term loss, avoiding heuristics. ([[phd/raw/phd/2603.19312v3.pdf#page=1]]) — "trains stably end-to-end from raw pixels using only two loss terms: a next-embedding prediction loss and a regularizer enforcing Gaussian-distributed latent embeddings."
- LeWM enables planning speeds significantly faster than foundation-model alternatives. ([[phd/raw/phd/2603.19312v3.pdf#page=1]]) — "LeWM plans up to 48× faster than foundation-model-based world models while remaining competitive across diverse 2D and 3D control tasks."
- Using SIGReg simplifies hyperparameter tuning to a single scalable coefficient. ([[phd/raw/phd/2603.19312v3.pdf#page=5]]) — "making λ the only effective hyperparameter to tune. This greatly simplifies hyperparameter selection, as λ can be efficiently optimized using a simple bisection search with logarithmic complexity."
- LeWM detects physical anomalies without explicit physical supervision. ([[phd/raw/phd/2603.19312v3.pdf#page=9]]) — "LeWM consistently assigns higher surprise to frames containing physical violations compared to their unperturbed counterparts."
