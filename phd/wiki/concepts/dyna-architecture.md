---
type: concept
title: Dyna Architecture
aliases: []
tags:
  - concept
  - phd
updated: 2026-08-21
status: developing
---

# Dyna Architecture

The **Dyna Architecture** is a class of intelligent agent designs developed by Richard Sutton that integrates trial-and-error learning, reactive execution, and offline planning into a single algorithm. 

### Key Components
* **World**: The actual environment. Real interactions update both the active reactive policy/value functions and the learned **World Model**.
* **World Model**: Simulates one-step state transitions and rewards based on past experiences.
* **Relaxation Planning**: Uses the world model to generate *hypothetical experiences* that update the policy and value functions during computational idle-time.

### Variations
* **Dyna-PI**: Uses dynamic programming's policy iteration with separate policy and evaluation function representations.
* **Dyna-Q**: Incorporates Q-learning, consolidating values and policy into a single $Q(x, a)$ table, reducing implementation complexity.
* **Dyna-Q+**: Includes an explicit uncertainty-based exploration bonus ($C \sqrt{n_{xa}}$) integrated directly into the simulated updates to proactively resolve environmental changes, resolving both the *blocking* and *shortcut* planning problems.

Source: [[phd/wiki/sources/phd2026integrated|Integrated Architectures for Learning, Planning, and Reacting Based on Approximating Dynamic Programming]]

## From [[phd/wiki/sources/phd202610356apathtowardsautonomousmach|10356_a_path_towards_autonomous_mach]] (2026-08-21)

## From "A Path Towards Autonomous Machine Intelligence" (LeCun)

LeCun cites Sutton's Dyna architecture (1991) as the classic precedent for what his proposed cognitive architecture calls [[phd/wiki/concepts/mode-2-planning-and-reasoning|Mode-2]] reasoning: inference over action sequences using a learned predictive model, distinguished from purely reactive ([[phd/wiki/concepts/mode-1-reactive-operation|Mode-1]]) behavior. In LeCun's framing, Dyna is positioned within a broader lineage of "learnable models" work — alongside more recent approaches (Ha & Schmidhuber, Hafner et al.'s world-model and Director systems) — that revives model-based planning as an alternative to sample-inefficient [[phd/wiki/concepts/reinforcement-learning-rl|model-free reinforcement learning]].

LeCun frames Dyna's core contribution — planning by imagining action sequences and predicting their outcomes through a learned model rather than exploring the real world — as the historical justification for why his own architecture's [[phd/wiki/concepts/world-model|world model]] module exists at all: it "lessens the need to perform an expensive and dangerous search for good actions... by trying multiple actions in the external world," directly echoing Dyna's *relaxation planning* via hypothetical experience. He explicitly draws the parallel to [[phd/wiki/concepts/model-predictive-control|Model-Predictive Control]] with receding horizon, noting that his Mode-2 procedure differs from classical MPC (and, implicitly, from Dyna's tabular setting) mainly in that the world model and cost function are *learned* rather than hand-designed — situating Dyna as a bridge between classical optimal control and modern differentiable world-model architectures like his proposed [[phd/wiki/concepts/joint-embedding-predictive-architecture|JEPA]]/[[phd/wiki/concepts/hierarchical-jepa-h-jepa|H-JEPA]].

No new variant, mechanism, or component of Dyna itself is introduced here — the source treats it purely as intellectual ancestry for model-based planning, not as an architecture to extend.

**projectRelevance:** thesis-topic-shift-world-models-vs-llms — the citation reinforces the historical case for model-based/world-model planning as a sample-efficient alternative to reward-driven RL and LLM-style approaches, directly bearing on the open question of World Model strengths for the thesis pivot pitch.
