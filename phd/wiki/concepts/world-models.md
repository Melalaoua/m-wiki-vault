---
type: concept
title: "World Models"
aliases: []
tags: [concept, phd, personal]
updated: 2026-08-02
status: developing
---

# World Models

Predictive models of environment dynamics that allow agents to simulate future states internally (in 'imagination'). Used extensively in reinforcement learning and planning, where an agent evaluates potential action sequences using a latent space without interacting with the real environment.

Source: [[phd/wiki/sources/phd2026leworldmodel|LeWorldModel: Stable End-to-End Joint-Embedding Predictive Architecture from Pixels]]

## From [[phd/wiki/sources/phd2026integrated|Integrated Architectures for Learning, Planning, and Reacting Based on Approximating Dynamic Programming]] (2026-08-01)

A **World Model** is an internal agent representation that mimics the transitions, rewards, and dynamics of the real world. Historically popularized by Richard Sutton's [[Integrated Architectures for Learning, Planning, and Reacting Based on Approximating Dynamic Programming]] in 1990, world models allow an agent to generate hypothetical experiences to plan actions offline or in real-time execution loops.

Modern incarnations include [[Joint-Embedding Predictive Architecture]] (JEPA) and [[Biological World Models via JEPA]]. Unlike model-free architectures, world models permit *relaxation planning*, drastically improving sample efficiency by allowing the agent to 'think' and simulate outcomes before acting.

## From [[phd/wiki/sources/phd2026world|World Models]] (2026-08-02)

A **World Model** is a cognitive-inspired neural network architecture that learns a compressed spatial and temporal representation of an environment, enabling an agent to predict future states given its current state and action. Synthesized in deep reinforcement learning by [[David Ha]] and [[Jürgen Schmidhuber]] (2018), this approach decouples spatial compression and temporal dynamics from decision-making policies.

## Core Components
* **Vision (V)**: Usually a [[Variational Autoencoder]] (VAE), which compresses high-dimensional pixel streams into a compact latent vector $z$ inside the [[Latent Space]].
* **Memory (M)**: A recurrent model, typically an MDN-RNN, which models $P(z_{t+1} | a_t, z_t, h_t)$ to capture temporal dependencies and environment stochastics.
* **Controller (C)**: A compact neural network or linear policy optimized using black-box evolution strategies (such as CMA-ES) rather than backpropagation.

## Hallucinated Dreams and Safety
Because the Memory model predicts a probability distribution over future states, a World Model can generate infinite trajectories of virtual experience. The agent can train entirely inside these "hallucinated dreams" before deployment into physical reality. To prevent the policy from finding exploits in the model's approximate logic, a temperature parameter ($\tau$) is introduced. High-temperature dreams force the controller to develop robust, error-tolerant strategies.

## Relevance to Biological and Genomic Fields
This paradigm has profound implications for translating AI into molecular biology and clinical medicine:
* **Clinical Trajectory Simulation**: Patient health states can be modeled in a clinical [[Latent Space]], allowing the MDN-RNN to simulate the temporal progression of a disease under varying clinical interventions without endangering real-world patients.
* **Limits of LLMs vs World Models**: While Large Language Models can generate text sequences, World Models ground representations in spatial and temporal dynamics, offering a more robust mechanistic framework for physical and genomic environments.
