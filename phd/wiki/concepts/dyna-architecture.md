---
type: concept
title: Dyna Architecture
aliases: []
tags:
  - concept
  - phd
updated: 2026-08-01
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
