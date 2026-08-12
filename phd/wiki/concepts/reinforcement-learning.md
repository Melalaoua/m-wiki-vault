---
type: concept
title: Reinforcement Learning (RL)
aliases: []
tags:
  - concept
  - personal
updated: 2026-08-12
status: developing
---

# Reinforcement learning (RL)

[[supervised-learning]] aims to trains models by optimizing to mathc ideal exemplars 
[[unsupervised-learning]] fit the models to a dataset.
[[reinforcement-learning]] trains the models holistically through trial and error. Used prominently in robotics, videos games, reasoning models where the space of possible solutions and approaches are particularly large, open-ended or difficult to define.

> In RL literature, an AI system is often referred to as an "agent".

RL operates on interdependent **==state-action-reward==** data tuples ( [[phd2026230104104v2| dreamerV3]]). Instead of minimizing the error, the objectif of RL is optimizing parameters to maximize the reward.

- the **state space** : all available information relevant to decisions that the model might make. Evolves which each action the model takes.
- **the action space** : all the decisions the model is permitted to make at a moment. (all legals moves in a board at time t).
- **Reward signal** : Feedback (positive or negative), expressed in a scalar-value as a result of each action. Can be determined by explicit rules, reward function, or separately by a reward model.
- **Policy** : the "thought process" that drives an RL agent's behavior.  A policy (π) is a function that takes a state ( s ) as input and returns an action (a ):   π(s)→a .


Consider a maze:  a policy-based agent might learn "at this corner, turn left", while a value-based agent learns a score for each position and simply moves to an adjacent position with a better score.
- [[proximal-policy-optimization]] (PPO) the models learns a policy directly (policy-based).
- value-based methods like [[phd2026integrated|Q-learning]], the agent learns a value function that computes a score for how "good" each state is, then chooses actions that lead to higher-value states.
- Hybrid approach, such as [[phd2026191201603v3|actor-critic methods]], learn a value function that's then used to optimize a policy.

- In deep RL, the policy is represented as a [[deep-learning|neural-network]]

