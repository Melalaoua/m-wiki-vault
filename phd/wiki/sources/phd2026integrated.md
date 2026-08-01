---
type: source
title: "Integrated Architectures for Learning, Planning, and Reacting Based on Approximating Dynamic Programming"
citekey: phd2026integrated
source_type: pdf
captured: 2026-08-01
site: phd
url: 
raw: phd/raw/phd/sutton1990.pdf
aliases: []
tags: [source, personal]
updated: 2026-08-01
status: developing
read_status: skimmed
last_sitting: 2026-08-01T20:58:23.568Z
---

# Integrated Architectures for Learning, Planning, and Reacting Based on Approximating Dynamic Programming

Original: [[phd/raw/phd/sutton1990.pdf]]

## Skim (pass 1)

**Your recall:**

Looks like two architecture are presented here : Dyna-PI and Dyna-Q. 

Dyna-PI is composed of 4 composants : a policy; a world model, an evaluation function and a world.

I'm not sure to understand each architecture yet. I'm lacking technical terms (is it deep learning ?). What i understood is that the architecture are much better than classical reinforcement learning because they are able to "plan" before acting. 

I might be mistaken but the Dyna-Q architecture is different from the first because instead of having 2 trained model (the action & world model), it has only one. But I haven't grasped completly that neither.

**Recall check** (Page 5): Which specific components from Dyna-PI does Dyna-Q merge into a single structure, and does Dyna-Q still retain an explicit world model?

Dyna-Q combines the policy and the evaluation function into a single structure (the Q-value table), but it still maintains and uses a learned world model to generate hypothetical experiences for planning.

**Your triage verdict:** worth pass 2

**My own read (after yours):**

**Model's Calibration Read:**

This seminal paper introduces the **Dyna** framework, which unifies reinforcement learning, world-modeling, and execution-time planning (via simulated experience) into a single, cohesive architecture. Sutton contributes two specific implementations: Dyna-PI, which approximates classic policy iteration, and Dyna-Q, which integrates Watkins’ Q-learning to streamline the system into a single data structure of Q-values. Notably, to address environments that change over time, the paper proposes incorporating an uncertainty-based exploration bonus directly into the planning updates, allowing the agent to actively plan paths to explore untried state-action pairs. However, a key limitation of this foundational work is its reliance on small, tabular state-spaces; scaling these architectures to complex domains requires integration with function approximators (like neural networks) where the convergence guarantees of dynamic programming no longer strictly hold.
