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

Essential to supervised learning is the use of a [[loss-function]] that measures the divergence (loss) between the model's output and the ground truth across a batch of training inputs. Various optimization algorithms (most involve calculating the [[backpropagation|derivative]]) are used to identify parameter adjustements that will reduce loss.

> Supervised learning aims to __minimize__ the loss function. 

Usually SL requires a [[human-in-the-loop]] to provide a ground-truth in the form of data annotations, thus the "supervised". But on the most fundamental level, the hallmark of **==SL is the existence of some ground truth and the training objective of minimizing the output of loss function.==**


#### Self-supervised learning.
Since labelling data can be costly and time-consuming, **==SSL==** entails training on tasks in which a supervisory signal is obtained directly from unlabeled data. hence the "self"-supervised.

[[phd/wiki/concepts/variational-autoencoder|variational-autoencoder]]