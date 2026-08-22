---
type: concept
title: "Cognitive Architecture"
aliases: []
tags: [concept, phd]
updated: 2026-08-21
status: developing
---

# Cognitive Architecture

## Overview

The **Cognitive Architecture** proposed in "A Path Towards Autonomous Machine Intelligence" is Yann LeCun's blueprint for an autonomous intelligent agent built entirely out of differentiable, trainable modules. It is offered as an answer to the paper's central diagnosis: current AI/ML systems need vastly more training trials than humans or animals because they lack [[world-models]] — internal models of how the world works that let an agent predict, reason, and plan largely from observation rather than expensive trial-and-error interaction. The architecture is the paper's organizing device for turning that diagnosis into a concrete system design (Figure 2 in the source), with every module assumed to be differentiable and most of them trainable, so that gradients of a global cost can, where possible, be back-propagated across the whole system for planning, reasoning, and learning.

The architecture is composed of six interacting modules: **[[Perception Module|perception]]**, **[[world-models]]**, **[[Cost module|cost]]** (itself split into an [[Intrinsic Cost module]] and a [[Trainable Critic module]]), **[[Actor Module|actor]]**, **[[Short-Term Memory Module|short-term memory]]**, and a governing **[[Configurator Module|configurator]]**. Their coordination is meant to support two distinct modes of operation — a fast reactive mode and a slower deliberative mode — echoing Daniel Kahneman's System 1/System 2 distinction.

## The modules

**Perception** receives raw sensor signals and estimates the current state of the world, potentially in a hierarchical fashion across multiple levels of abstraction. It can be primed or configured by the configurator to extract task-relevant information.

**World model** is described as "the most complex piece of the architecture." It has two jobs: (1) filling in missing information about the state of the world that perception alone does not supply, and (2) predicting plausible future states of the world, possibly several alternative ones, parameterized by latent variables that capture uncertainty. This is the module the paper's technical contribution — the [[joint-embedding-predictive-architecture]] (JEPA) and its hierarchical extension H‑JEPA — is designed to instantiate; see also [[world-models]] and [[biological-world-models-via-jepa]].

**Cost module** measures the agent's "discomfort" as a scalar energy, computed as the sum of two sub-modules: an immutable, hard-wired **Intrinsic Cost** (analogous to the amygdala) encoding basic drives — pain, hunger, curiosity, social/empathic drives, task-specific goals such as a legged robot's drive to stand and walk — and a **Trainable Critic** that predicts future intrinsic costs from states retrieved out of short-term memory, trained similarly to critics in [[Reinforcement Learning (RL)|actor-critic RL]] methods (e.g., A2C). Immutability of the intrinsic cost is treated as essential to prevent "behavioral collapse" or drift toward bad behavior. Because both sub-modules are differentiable, energy gradients can be back-propagated through world model, actor, and perception alike.

**Short-term memory** stores triplets of past/current/future world states and their intrinsic-cost values, architecturally similar to Key-Value Memory Networks, and functionally likened to the hippocampus. The world model reads and writes it while making temporal predictions or spatially completing/correcting the current state estimate.

**Actor** proposes action sequences, which the world model and cost module evaluate, feeding back gradients (or discrete-optimization signals) so the actor can compute an action sequence that minimizes estimated future cost — a process explicitly compared to [[Model-Predictive Control]] in classical optimal control. The actor comprises a reactive **policy module** and a heavier **action optimizer**; a trained policy can later be distilled ("compiled") from expensive optimizer-driven planning so that skills learned deliberately become fast reflexes, a form of amortized inference.

**Configurator** is the executive-control module: it takes input from every other module and reconfigures them on the fly by modulating parameters and attention circuits, priming perception, world model, and cost modules toward a given goal, and — its most important and least specified function — decomposing complex tasks into sequences of subgoals for the cost module to pursue. The paper explicitly flags the configurator as "the most mysterious" and least understood part of the whole proposal.

## Two operating modes

The architecture supports **Mode-1**, a purely reactive perception→policy→action pathway that bypasses the world model and cost module entirely (akin to System 1), and **Mode-2**, a model-predictive-control loop in which the actor proposes action sequences, the world model simulates their consequences, the cost module scores the resulting predicted trajectories, and the actor iteratively improves the proposal — gradient-based when the world model and cost are differentiable and well-behaved, or via dynamic programming, beam search, simulated annealing, or Monte-Carlo Tree Search when the action space is discrete or the cost landscape is non-smooth. Mode-2 is functionally System 2, and it is explicitly framed as receding-horizon MPC in which, unlike classical control, the world model and cost function are themselves learned rather than hand-designed.

## Differentiability as a unifying design principle

The architecture's defining commitment is that *all* modules be differentiable, and most be trainable — the explicit hedge against the difficulty of reconciling gradient-based learning with symbolic/logic-based reasoning. This lets a single scalar energy (the cost) drive learning and inference simultaneously across perception, world model, and actor. The paper's broader treatment of [[Energy-Based Models]], contrastive vs. regularized (non-contrastive) training, and the collapse problem in joint-embedding systems all exist to justify how the world-model module inside this architecture can be trained without labels or reconstruction, feeding directly into the design of JEPA/H‑JEPA as its concrete instantiation.

## Hierarchy and uncertainty

The architecture is meant to operate hierarchically: perception, world model, and actor can all represent state and action plans at multiple levels of abstraction and multiple time scales, with higher-level "actions" reinterpreted as conditions that lower-level predicted states must satisfy — an idea traced back to the classical proportional servomechanism in control theory. Uncertainty (aleatoric — intrinsic stochasticity, chaos, partial observability; epistemic — sensor, representational, or model limitations) is handled not by explicit probability distributions over outputs but by regularized latent variables inside the world model's predictor, sampled or optimized at planning time, with the attendant risk of exponential trajectory growth requiring pruning strategies such as MCTS.

## Biological grounding and open status

LeCun maps the modules onto candidate brain structures: perception to sensory cortices, world model and critic to prefrontal cortex, intrinsic cost to basal ganglia/amygdala, short-term memory to hippocampus, configurator to prefrontal executive-control structures, and actor to pre-motor cortex. A single, dynamically configurable world-model engine (rather than one model per task) is hypothesized to explain both computational reuse and cross-task knowledge sharing in animals and humans, and is offered as a speculative account of why conscious reasoning feels serial — and even of machine/animal "emotions" as a side-effect of the cost module's design (instantaneous emotions ≈ intrinsic cost, anticipatory emotions ≈ trainable critic).

The paper is candid that this is a research proposal, not a working system: it does not specify concrete architectures for the actor's search procedure, for latent-variable instantiation under Mode-2, for the predictor's routing/gating micro-architecture, or for how the configurator should learn to decompose tasks into subgoals. Building and training a working Hierarchical JEPA-based version of this architecture from video is flagged as an open, multi-year research problem.

## Relation to other approaches

The architecture is explicitly positioned against three rival bets for reaching human-level AI: scaling generative transformer-style language models, "reward is enough" pure [[Reinforcement Learning (RL)]], and hard-wired symbolic-reasoning augmentation — arguing that model-based reasoning through a learned, differentiable world model is more sample-efficient and more compatible with dynamically specified goals than any of the three. It also situates itself relative to prior model-based control and planning work, including [[Model-Predictive Control]], [[Dyna Architecture]], and hierarchical RL systems such as the Director architecture.

## Project relevance

- **[[thesis-topic-shift-world-models-vs-llms]]**: This is the primary source underpinning the argument that world-model-based architectures could offer sample-efficient, common-sense reasoning that current LLMs lack — directly informing the strengths/limits comparison this project needs for the topic-shift pitch.
- **[[project-meeps]]**: The modular, configurable, differentiable-agent design (perception/world-model/cost/actor/memory/configurator, Mode-1 vs Mode-2 processing) is a candidate architectural paradigm worth considering when documenting ADRs for Meeps' own multi-module, multi-brain design.

Source: [[phd/wiki/sources/phd202610356apathtowardsautonomousmach|10356_a_path_towards_autonomous_mach]]
