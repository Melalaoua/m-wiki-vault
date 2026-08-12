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
- **regression** : predict ouput values by identifying linear relationships between real or continous values. (Linear regression, random forest, gradient boosting, ...).
- **classification** : models predict discrete values (category, class, ...).

In order to train the model, it must be measured & optimized against a "ground truth" which is the most ideal or correct output for any given input. Hence it requires **labeled data**.

Essential to supervised learning is the use of a [[loss-function]] that measures the divergence (loss) between the model's output and the ground truth across a batch of training inputs. Various optimization algorithms (most involve calculating the [[backpropagation|derivative]]) are used to identify parameter adjustements that will reduce loss.

> Supervised learning aims to __minimize__ the loss function. 

Usually SL requires a [[human-in-the-loop]] to provide a ground-truth in the form of data annotations, thus the "supervised". But on the most fundamental level, the hallmark of **==SL is the existence of some ground truth and the training objective of minimizing the output of loss function.==**


## Common classification algorithms.

#### Naïve Bayes.
Operate on the logic of [[bayes-theorem]] which is essentially a mathematical formulation of the idea that information from later events can be used to update understanding of earlier events (such as inputs).

The model learns the relative importance of a given input variable based on how strongly it correlates with specific outcomes. Its eponymous "naive" assumption is that all features contributing to a classification are independent of each other. This simplification makes the algorithm fast and effective for straightforward tasks like spam detection.


#### Logistic regression.
Adapts the linear regression algorithm to solve binary classification problems by feeding the weighted sum of input features into a sigmoid function, which squashes any input into a value between 0 and 1.  The resulting value can be interpreted as the probability of a given event—in this case, a specific classification—occurring.

#### K-nearest neighbor (KNN).
Classify data points based on their proximity in the [[embedding-space]] to other data points, with the assumption that similar data points can be found near each other. The k refers to how many neighboring data points are taken into consideration.

#### Support vector machines (SVMs).
Powerful models that ostensibly perform binary classification but can also be adapted to multi-classification.

Its goal is to learn the optimal decision boundary to separate two categories of labeled data points in order to classify new data based on which side of the boundary they fall. 

The boundary defined is a hyperplane that maximizes the margin (or gap) between data points of opposite classes.

Logically, the only data points that can support the computation of that hyperplane are the data points from each class that are closest to the boundary. The vector embeddings of those boundary-adjacent data points are therefore called _support vectors._



## Self-supervised learning.
Since labelling data can be costly and time-consuming, **==SSL==** entails training on tasks in which a supervisory signal is obtained directly from unlabeled data. hence the "self"-supervised.

#### Category One : Self-prediction
Train a model to predict one aspect of a data point when given other information about that data point. "Pretend there is a part of the input you don't know and predict that" - Yann Lecun.

- Predict _any part of the input_ from _any other part_
- Predict the _future_ from the _past_
- Predict the _masked_ from the _visible_
- Predict any _occluded part_ from all _available parts_

Prominent example of machine learning models trained used self-prediction algorithms include autoencoders and [[large-language-models]] (LLMs).

[[phd/wiki/concepts/variational-autoencoder|variational-autoencoder]] are trained to compress (encode) input data, then reconstruct (decode) the original input that using the compressed representation. The training objective is to **minimize reconstruction error**, using the original input sa ground-truth.

Autoregressive LLMs—the text generating models that rose to fame following the launch of ChatGPT—are tasked with iteratively predicting the next token in a sequence, given only the previous tokens in that sequence. For each prediction, the actual next token in the sequence serves as ground truth.


#### Category Two : Contrastive learning.
Provide a lot of data and task the model to predict how diffrent (or similar) they are.



> **semi-supervised learning** use both labeled and unlabeled data using techniques that use information from the available labeled data to make assumptions about the unlabeled data.


