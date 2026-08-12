---
type: concept
title: Supervised Learning
aliases: []
tags:
  - concept
  - personal
updated: 2026-08-12
status: developing
---

# Supervised learning

Trains the model for the best accuracy, such as classification or regression.
- **regression** : models predict continous values (price, duration, temperature, ...).
- **classification** : models predict discrete values (category, class, ...).

In order to train the model, it must be measured & optimized against a "ground truth" which is the most ideal or correct output for any given input. Hence it requires **labeled data**.

Essential to supervised learning is the use of a [[loss-function]] that measures the divergence (loss) between the model's output and the ground truth across a batch of training inputs. 

> Supervised learning aims to __reduce__  