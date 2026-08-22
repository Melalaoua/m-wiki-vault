---
type: concept
title: "Common Sense"
aliases: []
tags: [concept, phd]
updated: 2026-08-21
status: developing
---

# Common Sense

## Common Sense

Common sense is treated in this source as a specific, definable capability rather than a vague catch-all: **the ability to use models of the world to fill in blanks** — predicting the future, or more generally inferring information about the world that is unavailable from perception or memory. This definition is offered as an alternative to treating common sense as an emergent side-effect of scale, and it grounds the entire architectural proposal developed in the paper (see [[world-models]] and the broader [[deep-learning]] context this document argues against).

### Common sense as a collection of world models

The document's core claim is that common sense in animals and humans "can be seen as a collection of models of the world that can tell an agent what is likely, what is plausible, and what is impossible." This is not a single monolithic faculty but an emergent property of many predictive models operating at different levels of abstraction — from low-level physical expectations (object permanence, [[Intuitive Physics|intuitive physics]], gravity, inertia) up through increasingly abstract concepts, largely acquired through observation with minimal direct intervention, especially early in development.

Crucially, the source proposes that this collection of models need not be architecturally separate for each domain. One hypothesis advanced is that animals and humans possess a **single, configurable world model engine**, plausibly located in the prefrontal cortex, that is dynamically reconfigured for the task at hand by a [[configurator-module]]. Under this hypothesis, common sense "emerges from a collection of models of the world **or from a single model engine configurable to handle the situation at hand**" — the configurability itself is what allows one underlying substrate to produce knowledge-sharing and reasoning by analogy across superficially unrelated tasks, rather than requiring the brain to store a distinct model per situation.

This reframes common sense as **grounded intelligence**: a hierarchy of models running from low levels of abstraction (raw sensorimotor regularities) up to high levels, including knowledge acquired through language. Language-derived knowledge sits at the top of this hierarchy rather than constituting common sense on its own.

### The proposed substrate: self-supervised H-JEPA

The document's speculative but concrete proposal is that **self-supervised learning applied to a configurable [[Hierarchical JEPA (H-JEPA)|H-JEPA]]** — the hierarchical extension of the [[Joint-Embedding Predictive Architecture]] developed earlier in the paper — could constitute the substrate of machine common sense. The mechanism is explicit: common sense may emerge from learning world models that capture the **self-consistency and mutual dependencies of observations** in the world, which in turn allows an agent to (a) fill in missing information and (b) detect violations of its own world model. This ties common sense directly back to the paper's technical machinery: [[Energy-Based Models (EBM)|energy-based models]] trained with non-contrastive objectives (e.g. [[VICReg]]) that learn representations abstract enough to be predictable, at multiple time scales and levels of abstraction, without requiring reconstruction of every irrelevant pixel-level detail.

### Contrast with large language models

The document draws a sharp, explicit contrast between this world-model-grounded conception of common sense and the knowledge exhibited by large language models. Its central claims:

- AI systems, "even when (pre-)trained with self-supervised mode (e.g. from text) seem to exhibit very limited levels of common sense, making them somewhat brittle."
- LLMs "possess a surprisingly large amount of background knowledge extracted from written text," but **much of human common-sense knowledge is not represented in any text** and instead results from direct interaction with the physical world.
- Because LLMs "have no direct experience with an underlying reality, the type of common-sense knowledge they exhibit is very shallow and can be disconnected from reality."
- More broadly, the paper argues that scaling generative token-based models is not sufficient for human-level intelligence: such models operate on tokenized, discrete data, which is workable for text but poorly suited to representing the complex uncertainties of continuous, high-dimensional signals like video — precisely the domain from which embodied common sense is hypothesized to arise. This is offered as a direct rebuttal to claims (attributed to Brown et al., 2020) that scaling transformer architectures alone is enough.
- The absence of abstract, explorable latent variables in current generative models is also cited as limiting their reasoning capacity, and by extension their capacity to build or apply common-sense models rather than merely regurgitate textual statistics.

This positions common sense as fundamentally an **embodied, prediction-based, grounded** phenomenon — inseparable from a system's capacity to build and query hierarchical [[World Models|world models]] — rather than a byproduct of exposure to large text corpora.

### Relation to other architectural components

The source ties common sense back to specific modules of its proposed [[Cognitive Architecture]]: the [[World model|world model module]]'s twofold role (estimating missing state information, predicting plausible futures) is essentially a mechanistic account of what "filling in blanks" requires; the [[Configurator Module]]'s ability to reconfigure a shared world-model engine is what allows common-sense-like generalization across tasks rather than task-specific brittle competence.

---

**projectRelevance:**
- `thesis-topic-shift-world-models-vs-llms` — This is a direct, load-bearing source for the pitch's central open question ("What are the strengths of World Models and how can they be translated to genomic/clinical fields?" and the LLM-vs-World-Models comparison generally). LeCun's explicit argument that LLM knowledge is shallow and ungrounded while common sense requires grounded, embodied world models is precisely the theoretical grounding needed to argue for a topic shift away from LLM-centric approaches toward world-model approaches in clinical/molecular diagnosis.

Source: [[phd/wiki/sources/phd202610356apathtowardsautonomousmach|10356_a_path_towards_autonomous_mach]]
