---
type: concept
title: World Models
aliases: []
tags:
  - concept
  - phd
updated: 2026-08-21
status: developing
---

# World Models

Predictive models of environment dynamics that allow agents to simulate future states internally (in 'imagination'). Used extensively in reinforcement learning and planning, where an agent evaluates potential action sequences using a latent space without interacting with the real environment.

Source: [[phd/wiki/sources/phd2026leworldmodel|LeWorldModel: Stable End-to-End Joint-Embedding Predictive Architecture from Pixels]]

## From [[phd/wiki/sources/phd2026integrated|Integrated Architectures for Learning, Planning, and Reacting Based on Approximating Dynamic Programming]] (2026-08-01)

A **World Model** is an internal agent representation that mimics the transitions, rewards, and dynamics of the real world. Historically popularized by Richard Sutton's [[phd2026integrated| Integrated Architectures for Learning, Planning, and Reacting Based on Approximating Dynamic Programming]] in 1990, world models allow an agent to generate hypothetical experiences to plan actions offline or in real-time execution loops.

Modern incarnations include [[joint-embedding-predictive-architecture]] (JEPA) and [[biological-world-models-via-jepa]]. Unlike model-free architectures, world models permit *relaxation planning*, drastically improving sample efficiency by allowing the agent to 'think' and simulate outcomes before acting.

## From [[phd/wiki/sources/phd2026world|World Models]] (2026-08-02)

A **World Model** is a cognitive-inspired neural network architecture that learns a compressed spatial and temporal representation of an environment, enabling an agent to predict future states given its current state and action. Synthesized in deep reinforcement learning by [[David Ha]] and [[Jürgen Schmidhuber]] (2018), this approach decouples spatial compression and temporal dynamics from decision-making policies.

## Core Components
* **Vision (V)**: Usually a [[phd/wiki/concepts/variational-autoencoder|variational-autoencoder]] (VAE), which compresses high-dimensional pixel streams into a compact latent vector $z$ inside the [[latent-space]].
* **Memory (M)**: A recurrent model, typically an MDN-RNN, which models $P(z_{t+1} | a_t, z_t, h_t)$ to capture temporal dependencies and environment stochastics.
* **Controller (C)**: A compact neural network or linear policy optimized using black-box evolution strategies (such as CMA-ES) rather than backpropagation.

## Hallucinated Dreams and Safety
Because the Memory model predicts a probability distribution over future states, a World Model can generate infinite trajectories of virtual experience. The agent can train entirely inside these "hallucinated dreams" before deployment into physical reality. To prevent the policy from finding exploits in the model's approximate logic, a temperature parameter ($\tau$) is introduced. High-temperature dreams force the controller to develop robust, error-tolerant strategies.

## Relevance to Biological and Genomic Fields
This paradigm has profound implications for translating AI into molecular biology and clinical medicine:
* **Clinical Trajectory Simulation**: Patient health states can be modeled in a clinical [[latent-space]], allowing the MDN-RNN to simulate the temporal progression of a disease under varying clinical interventions without endangering real-world patients.
* **Limits of LLMs vs World Models**: While Large Language Models can generate text sequences, World Models ground representations in spatial and temporal dynamics, offering a more robust mechanistic framework for physical and genomic environments.

## From [[phd/wiki/sources/phd202610356apathtowardsautonomousmach|10356_a_path_towards_autonomous_mach]] (2026-08-21)

Yann LeCun frames world models not as one technique among several but as *the* missing capability separating current AI from human and animal intelligence. His diagnosis: machine learning systems today need vastly more training trials than a human or animal to reach reliable performance, "so that even the rarest combination of situations will be encountered frequently during training" — a brute-force substitute for genuine understanding. The proposed remedy is enabling machines to "learn to represent the world, learn to predict, and learn to act largely by observation," rather than through costly, potentially dangerous direct interaction.

**Two functions, not one.** LeCun decomposes the world model's role into exactly two jobs: 
1. estimating missing information about the state of the world not given directly by perception, and
2. Predicting plausible future states of the world

This is a sharper functional split than the page's current framing of "simulate future states" — the world model is doing state completion (filling gaps in an incomplete percept) as much as it is doing forward prediction, and multiple plausible future states are predicted in parallel, "parameterized by latent variables that represent the uncertainty about the world state," rather than a single trajectory or distribution collapse.

**Biological motivation.** The architecture's justification is explicitly comparative: "The answer may lie in the ability of humans and many animals to learn world models, internal models of how the world works," acquired mostly through passive observation with minimal direct intervention, "particularly in the first few weeks and months" of development — building hierarchical concepts from concrete to abstract. LeCun goes further than analogy, hypothesizing a single hardware substrate: "animals and humans have only one world model engine somewhere in their prefrontal cortex," dynamically configured for whatever task is at hand by a [[Configurator Module]] — rather than separate models learned per situation. This reuse hypothesis is offered as an explanation for cross-task generalization and reasoning by analogy, and speculatively for the felt singularity of conscious thought ("humans can essentially perform a single 'conscious' reasoning and planning task at a time").

**World model as substrate for common sense.** Rather than a separate capability, [[common-sense]] is redefined here as *emergent from* the world model's completion function: "the ability to use models of the world to fill in blanks... or more generally filling in information about the world that is unavailable from perception or from memory." This positions world models as categorically different from [[Large language models]], whose knowledge is described as text-derived and "disconnected from reality" for lack of direct physical experience — a contrast directly relevant to the open question in [[thesis-topic-shift-world-models-vs-llms]] about whether world-model grounding offers genuine advantages over LLMs for clinical/molecular reasoning.

**Contrast with the Ha & Schmidhuber V-M-C decomposition already on this page**: LeCun's world model is embedded in a larger differentiable [[Cognitive Architecture]] (perception, world model, actor, cost, configurator, memory) where prediction is tightly coupled to an [[Energy minimization]]-based action-selection loop (the [[Actor Module]] and [[Cost module]]), rather than a standalone V-M-C pipeline trained by evolution strategies. The mechanism for handling uncertainty also differs: instead of an MDN-RNN's explicit probability distribution, LeCun pushes stochasticity into regularized latent variables inferred, sampled, or predicted per prediction step — designed specifically to avoid representing "every pixel value of every future frame," in favor of prediction restricted to abstract representation space via [[joint-embedding-predictive-architecture]]
.
