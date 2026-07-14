---
type: concept
title: "Joint-Embedding Predictive Architecture"
aliases: []
tags: [concept, phd]
updated: 2026-07-11
status: developing
---

# Joint-Embedding Predictive Architecture

A machine learning architecture, conceptualized by Yann LeCun, that learns representations by predicting the latent embedding of a future state from the latent embedding of a current state, avoiding the need to reconstruct high-dimensional raw observations. A major challenge in JEPAs is preventing representation collapse, historically addressed with stop-gradients or EMAs, but more recently through direct regularization like the [[sketched-isotropic-gaussian-regularizer]].

Source: [[phd/wiki/sources/phd2026leworldmodel|LeWorldModel: Stable End-to-End Joint-Embedding Predictive Architecture from Pixels]]
