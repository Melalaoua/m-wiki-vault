---
type: concept
title: "World Models"
aliases: []
tags: [concept, phd, personal]
updated: 2026-08-01
status: developing
---

# World Models

Predictive models of environment dynamics that allow agents to simulate future states internally (in 'imagination'). Used extensively in reinforcement learning and planning, where an agent evaluates potential action sequences using a latent space without interacting with the real environment.

Source: [[phd/wiki/sources/phd2026leworldmodel|LeWorldModel: Stable End-to-End Joint-Embedding Predictive Architecture from Pixels]]

## From [[phd/wiki/sources/phd2026integrated|Integrated Architectures for Learning, Planning, and Reacting Based on Approximating Dynamic Programming]] (2026-08-01)

A **World Model** is an internal agent representation that mimics the transitions, rewards, and dynamics of the real world. Historically popularized by Richard Sutton's [[Integrated Architectures for Learning, Planning, and Reacting Based on Approximating Dynamic Programming]] in 1990, world models allow an agent to generate hypothetical experiences to plan actions offline or in real-time execution loops.

Modern incarnations include [[Joint-Embedding Predictive Architecture]] (JEPA) and [[Biological World Models via JEPA]]. Unlike model-free architectures, world models permit *relaxation planning*, drastically improving sample efficiency by allowing the agent to 'think' and simulate outcomes before acting.
