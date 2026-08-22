---
type: map
title: "JEPA and Learned World Models: LeCun's Cognitive Architecture"
aliases: []
tags: [map, phd]
updated: 2026-08-21
status: stable
---

# JEPA and Learned World Models: LeCun's Cognitive Architecture

Technical proposal laid out in [[phd202610356apathtowardsautonomousmach|LeCun's "A Path Towards Autonomous Machine Intelligence]]" together with adjacent formulations of world models, and traces its conceptual lineage back through classical model-based control and forward into a concrete trainable system.

### Core diagnosis and architecture

Current ML systems require far more training trials than humans or animals because they lack internal [[phd/wiki/concepts/world-models|World Models]] that let an **agent predict and reason from observation** rather than costly interaction. 

The proposed remedy is a [[phd/wiki/concepts/cognitive-architecture|Cognitive Architecture]] of six differentiable, mostly trainable modules : perception, world model, cost (split into Intrinsic Cost and Trainable Critic), actor, short-term memory, and a [[phd/wiki/concepts/configurator-module|Configurator Module]].

The cognitive architecture is supported by a fast reactive Mode-1 and a deliberative Mode-2. It is explicitly framed as [[phd/wiki/concepts/model-predictive-control|Model-Predictive Control]] with receding horizon, distinguished from classical MPC in that both the world model and cost function are *learned* rather than hand-designed, with roots traced to Sutton's [[dyna-architecture|Dyna Architecture]] as historical precedent for planning via a learned predictive model.

The Configurator is flagged by the source itself as the architecture's most speculative, least-specified component, responsible for reconfiguring the shared world-model engine and decomposing tasks into subgoals — a mechanism named but never operationalized.

### JEPA: the technical centerpiece

The architecture's world-model module is meant to be instantiated by the [[phd/wiki/concepts/joint-embedding-predictive-architecture|Joint-Embedding Predictive Architecture]] (JEPA), which **==predicts latent embeddings of future states rather than reconstructing raw observations==**, formalized as an energy $$E_w(x, y, z) = D(s_y, Pred(s_x, z))$$ 

JEPA is best understood as an instance of the general [[phd/wiki/concepts/energy-based-models-ebm|Energy-Based Models]] framework, which unifies [[phd/wiki/concepts/supervised-learning|self-supervised]] methods around a shared training problem, energy collapse, and a shared remedy split into contrastive versus regularized (non-contrastive) methods, the latter judged more promising for escaping the curse of dimensionality. 

JEPA's own anti-collapse regime is specified as four criteria (informativeness of $s_x$ and $s_ŷ$, predictability of $s_y$ from $s_x$, minimal information in $z$), concretely implemented by [[phd/wiki/concepts/vicreg|VICReg]] and Barlow Twins as "dimension-contrastive" losses. Stacking this mechanism across time scales yields [[hierarchical-jepa-h-jepa|Hierarchical JEPA (H-JEPA)]], intended to resolve the tension between detailed short-horizon and abstract long-horizon prediction via temporal pooling and discrete latents for multi-modal futures.

### Grounding, common sense, and rival approaches

The architecture's philosophical payoff is a redefinition of [[phd/wiki/concepts/common-sense|Common Sense]] as the ability of world models to fill in missing information, contrasted with large language models, whose knowledge is characterized as text-derived and ungrounded. This grounds the broader claim that JEPA/H-JEPA-based common sense could outperform LLM-style approaches for physically or biologically grounded reasoning.

### Complementary and contrasting world-model traditions

Other pages in this cluster supply comparison points: the [[phd/wiki/concepts/dyna-architecture|Dyna Architecture]] as Sutton's original relaxation-planning precedent; the Ha & [[phd2026world|Schmidhuber Vision-Memory-Controller world model]] as an alternative, evolution-trained, generative ([[phd/wiki/concepts/variational-autoencoder|VAE]]-based) decomposition rather than LeCun's differentiable energy-driven design; and the general concept of [[latent-space|Latent Space]], populated by classical linear methods like [[principal-component-analysis|Principal Component Analysis]] and by the [[phd/wiki/concepts/variational-autoencoder|Variational Autoencoder]], whose reconstruction-based generative objective JEPA explicitly rejects in favor of representation-space prediction. The [[sketched-isotropic-gaussian-regularizer|Sketched-Isotropic-Gaussian Regularizer]] (SIGReg) appears as a later, concrete anti-collapse mechanism used in an end-to-end, pixel-trained JEPA system, and is flagged as sitting in tension with LeCun's original framing of collapse-prevention as primarily a non-contrastive/regularized (VICReg-style) rather than stop-gradient/EMA-based problem — an open contradiction within this cluster's sources.

## Pages in this area

- [[phd/wiki/concepts/joint-embedding-predictive-architecture|Joint-Embedding Predictive Architecture]]
- [[phd/wiki/concepts/world-models|World Models]]
- [[phd/wiki/concepts/sketched-isotropic-gaussian-regularizer|Sketched-Isotropic-Gaussian Regularizer]]
- [[phd/wiki/concepts/latent-space|Latent Space]]
- [[phd/wiki/concepts/variational-autoencoder|Variational Autoencoder]]
- [[phd/wiki/concepts/principal-component-analysis|Principal Component Analysis]]
- [[phd/wiki/concepts/dyna-architecture|Dyna Architecture]]
- [[phd/wiki/concepts/hierarchical-jepa-h-jepa|Hierarchical JEPA (H-JEPA)]]
- [[phd/wiki/concepts/cognitive-architecture|Cognitive Architecture]]
- [[phd/wiki/concepts/configurator-module|Configurator Module]]
- [[phd/wiki/concepts/energy-based-models-ebm|Energy-Based Models (EBM)]]
- [[phd/wiki/concepts/vicreg|VICReg]]
- [[phd/wiki/concepts/common-sense|Common Sense]]
- [[phd/wiki/concepts/model-predictive-control|Model-Predictive Control]]
