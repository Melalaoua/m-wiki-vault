---
type: concept
title: Deep Learning
aliases: []
tags:
  - concept
  - personal
updated: 2026-08-12
status: developing
---

# Deep learning

Employs artificial [[neural-networks]] with many layers (hence "deep"). Was vastly democratized in 2010 due to the emergence of [[graphic-processing-unit]] (GPUs)

Inspired by the human brain, NN are interconnected layrs of neurons (nodes) each performing a mathematical operation (activation function). The ouput of each nodes serves as input for the following nodes until the final layer.

Each activation function performed at each node are nonlinear, enabling NN to model complex patterns and dependencies.

Each connection between two neurons is assigned a uniqued **weight** : a multiplier that increases or decreases one neuron's contribution to a neuron in the following layer. Each of which are the parameters to be optimized through [[machine-learning]]

The [[backpropagation]] algorithm is the computation of =="**how each individual node contributes to the overal output of the loss function"**== allowing millions, billions of model wieghts to be individually optimized through [[gradient-descent]] algorithms.


> Neural networks are _universal approximators_: it has been theoretically proven that for any function, there exists a neural network arrangement that can reproduce it.

