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



#### Convolutional neural networks (CNNS).
In mathematics, a convolution is an operation where one function modifies (or convolves) the shape of another. In CNNs, the convlutional layers are used to extract imporant features from data by applying weighted "filters".  CNNs are primarily associated with computer vision models and image data.


#### Recurrent Neural Networks (RNNs).
Work on sequential data, whereas conventional feedforward networks map a single input to a single ouptut, RNNs map a sequence of inputs to an output by operating in a recurrent loop in which the output for a given step in the input sequence servers as input to the computation for the following step. In effect, this creates an inernal "memory", called the hidden state, that allows RNNs to understand context and order.


#### Transfomers.
First introduced in 2017, they are largely responsible for the advent of [[wiki/concepts/large-language-models]] and other pillars of generative AI. 
Like RNNs, transformers are ostensibly designed for sequential data, but clever workarounds have enabled most data modalities to be processed by transformers. The unique strength of a transformer model comes from their innovative attention mechanism, which enables the models to selectively focus on the parts of the input data most relevant at a specific moment in a sequence.


### Architectures vs. algorithms.

In the context of deep learning, specific model types are often referred to by their “architectures,” a concept related to but distinct from algorithms.

a **neural network architecture** refers to its layout : the number and size of layers, the use of specialized layers, the choice of activation functions. A same architecture can be trained to perform multiple kinds of tasks.

A deep learning algorithm comprises not only the NN architectures but also the task its being trained to perform and the steps taken to optimize it for that task.

Consider autoencoders: architecture-wise, an autoencoder is an _encoder-decoder_ model—its encoder network features progressively smaller layers, while its decoder network features progressively larger layers. But an autoencoder is only one of many encoder-decoder models: for instance, [image segmentation](https://www.ibm.com/topics/image-segmentation) models have a very similar architecture, in which progressive smaller [convolutional](https://www.ibm.com/think/topics/convolutional-neural-networks) layers downsample data to isolate and segment key features, followed by progressively larger layers that upsample the (segmented) data back to its original size.

What makes an autoencoder an autoencoder is not (just) its architecture, but the algorithm used to train it: an autoencoder is _tasked with reconstructing the original input,_ and optimized through model training to _minimize a function that measures reconstruction loss_ (often modified by additional [regularization](https://www.ibm.com/think/topics/regularization) terms)_._ A model that has an identical architecture but is trained to perform a different task and optimized for a different objective is not an autoencoder.