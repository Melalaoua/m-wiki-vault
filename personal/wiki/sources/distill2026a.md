---
type: source
title: "A Gentle Introduction to Graph Neural Networks"
citekey: distill2026a
source_type: article
captured: 2026-07-20
site: distill.pub
url: https://distill.pub/2021/gnn-intro/
aliases: []
tags: [source, personal]
updated: 2026-07-20
status: developing
---

# A Gentle Introduction to Graph Neural Networks

Original: [[personal/raw/distill.pub/a-gentle-introduction-to-graph-neural-networks]]

This article from distill.pub introduces [[Graph Neural Network]] (GNN) architectures. Unlike images or text which have regular grid-like structures, graph data (like molecules, social networks, or citation networks) requires models that respect [[Permutation Invariance]]. The core operation in modern GNNs is message passing (formalized in the [[Message Passing Neural Network]] framework), where each node or edge gathers embeddings from its neighbors, aggregates them (e.g., via sum, mean, or max pooling), and updates its own embedding using a neural network. The article covers three main types of prediction tasks: graph-level, node-level, and edge-level. It also explores how graph connectivity is represented efficiently using adjacency lists rather than sparse adjacency matrices, and notes that a [[Transformer]] can be viewed as a GNN with an attention mechanism operating on a fully connected graph.

## Key claims

- A Graph Neural Network applies transformations to graph attributes while preserving permutation invariance. ([[personal/raw/distill.pub/a-gentle-introduction-to-graph-neural-networks#Graph Neural Networks]]) — "A GNN is an optimizable transformation on all attributes of the graph (nodes, edges, global-context) that preserves graph symmetries (permutation invariances)."
- Edge classification tasks can be transformed into node classification tasks using the graph's dual representation. ([[personal/raw/distill.pub/a-gentle-introduction-to-graph-neural-networks#Edges and the Graph Dual]]) — "an edge prediction task on a graph $G$ can be phrased as a node-level prediction on $G$’s dual."
- Matrix multiplication on an adjacency matrix functions as a summation-based message passing operation. ([[personal/raw/distill.pub/a-gentle-introduction-to-graph-neural-networks#Graph convolutions as matrix multiplications, and matrix multiplications as walks on a graph]]) — "the matrix multiplication of an adjacent matrix $A$ ... with a node feature matrix $X$ ... implements an simple message passing with a summation aggregation."
- Increasing the number of layers in a GNN can degrade performance by diluting node representations. ([[personal/raw/distill.pub/a-gentle-introduction-to-graph-neural-networks#Some empirical GNN design lessons]]) — "GNN with a higher number of layers will broadcast information at a higher distance and can risk having their node representations ‘diluted’ from many successive iterations"
