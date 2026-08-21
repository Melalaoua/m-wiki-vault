---
type: concept
title: "Hierarchical JEPA (H-JEPA)"
aliases: []
tags: [concept, phd]
updated: 2026-08-21
status: developing
---

# Hierarchical JEPA (H-JEPA)

## Hierarchical JEPA (H-JEPA)

Hierarchical JEPA (H-JEPA) is the multi-level extension of [[phd/wiki/concepts/joint-embedding-predictive-architecture|Joint-Embedding Predictive Architecture]] (JEPA) proposed in this document as the mechanism for enabling prediction at multiple time scales and multiple levels of abstraction, and for grounding hierarchical planning under uncertainty. It sits at the core of the paper's proposed [[phd/wiki/concepts/hierarchical-learning|hierarchical]] [[phd/wiki/concepts/world-models|world model]] architecture, and is presented as one of the paper's central contributions: "JEPA and Hierarchical JEPA: a non-generative architecture for predictive world models that learn a hierarchy of representations."

### Motivation: why prediction needs to be hierarchical

The paper argues that a single-level [[phd/wiki/concepts/joint-embedding-predictive-architecture|JEPA]] faces an inherent tension between detail and horizon: low-level representations carry a great deal of detail about the input and support accurate short-term prediction, but the same detail makes long-term prediction difficult, since fine-grained trajectories become increasingly unpredictable as they depend on more and more external, unpredictable events. High-level, abstract representations strip away detail and thereby make longer-term prediction tractable, at the cost of precision. The canonical illustration given is driving: given a proposed sequence of steering and pedal actions over the next several seconds, a driver can accurately predict the car's detailed trajectory over that same short period, but predicting the exact trajectory over a longer period is much harder because it depends on other cars, traffic lights, and pedestrians — unpredictable external events. Yet the driver can still make an accurate higher-level prediction, e.g., that the car will probably arrive at its destination within a predictable time frame. H-JEPA is proposed as the architectural mechanism for capturing both regimes simultaneously: detailed short-horizon prediction at low levels, abstract long-horizon prediction at high levels.

### Architecture

H-JEPA extends JEPA (labeled JEPA-1, JEPA-2, etc., in the paper's figures) into a stack of levels, each performing joint-embedding prediction, with **temporal pooling** used between levels to coarse-grain the representation and support longer-term prediction at each successive level. The paper envisions architectures "with many levels, possibly using convolutional and other modules," using this temporal pooling to move from fine, frequent representations at the bottom to coarse, infrequent representations at the top.

Discrete [[phd/wiki/concepts/latent-space|latent variables]] can be used within this hierarchy to represent qualitatively distinct alternatives — for example, a discrete latent variable "may be used to represent multiple alternative routes" a driver could take, illustrating how H-JEPA handles multi-modal future possibilities at a given level of abstraction rather than collapsing them into a single blurred prediction.

The paper treats the ability to represent sequences of world states at several levels of abstraction as "essential to intelligent behavior," directly linking the architecture to the paper's broader claims about [[phd/wiki/concepts/hierarchical-learning|hierarchical]] concept and skill acquisition in humans and animals.

### Hierarchical planning under uncertainty

H-JEPA is proposed as the basis for hierarchical planning under uncertainty (Mode-2 reasoning, in the paper's terminology for deliberate, model-based action). With multi-level representations of world states and actions available, a complex task can be decomposed into successively more detailed sub-tasks, instantiated into action sequences only when informed by local conditions — rather than requiring the entire plan to be specified in low-level detail up front.

Consistent with the paper's "deep learning philosophy," the intermediate representations of action plans at each level are meant to be *learned* rather than hand-designed. A key conceptual move is that, in this hierarchical planning scheme, high-level "actions" are not literal actions but **targets for the lower-level predicted states** — conditions that a lower-level state must satisfy for the high-level prediction to be considered accurate. [[phd/wiki/concepts/cost-module|Cost modules]] at intermediate levels (e.g., taking a lower-level state and a high-level condition) measure the extent to which the state satisfies the condition, effectively operationalizing subgoals. The paper notes that naive top-down greedy planning through this hierarchy can be improved by jointly optimizing action sequences across all layers rather than optimizing level by level.

The document traces this "action as condition to be satisfied by the level below" idea to classical control theory, giving the example of a proportional servomechanism, which can be understood as being given a target state with a quadratic cost measuring the squared distance between target and current state — a direct historical precedent for the H-JEPA hierarchical planning scheme.

### Handling uncertainty within the hierarchy

Because the real world is not fully predictable, H-JEPA must represent uncertainty at each level. The paper enumerates the underlying sources: aleatoric uncertainty (the world being intrinsically stochastic, chaotic, or only partially observable) and [[phd/wiki/concepts/epistemic-uncertainty|epistemic uncertainty]] (incomplete sensing, insufficient perceptual representation, bounded rationality of the world model, or limited training data). Uncertainty is handled by predictors with [[phd/wiki/concepts/latent-space|latent variables]] that carry information about the prediction not derivable from the prior observation; these latents must be regularized (via mechanisms discussed for [[phd/wiki/concepts/joint-embedding-predictive-architecture|JEPA]] more generally — discretization, low dimensionality, sparsity, or stochasticity) to avoid energy collapse and to force the system to predict as much as possible without leaning on the latent. At planning time, latents are sampled from Gibbs distributions derived from these regularizers, with regularizer parameters optionally conditioned on previous states and retrieved memories to bias generation toward coherent trajectories.

A practical consequence noted in the source is combinatorial: if each latent variable has k discrete possible values, the number of possible predicted trajectories grows as k^t over t time steps, so directed search and pruning strategies (the paper mentions Monte-Carlo Tree Search) are necessary at each level to keep planning tractable. With multiple predicted trajectories in hand, the [[phd/wiki/concepts/actor-module|actor]] can choose optimal action sequences that minimize average cost, or a combination of average cost and variance, to manage risk.

### Component modules used across levels

The paper's discussion of the concrete micro-architecture for H-JEPA levels suggests different module types are appropriate at different levels: low-level, short-term prediction in video-like data is best handled by extracting local feature vectors and displacing them according to predicted motion (with latent variables encoding displacement maps that modulate routing), while longer-term, higher-level prediction — involving objects and their interactions — is better modeled with a transformer architecture, prized for being equivariant to permutation and thus naturally suited to variable sets of interacting discrete objects. The agent is additionally proposed to maintain a separate ego-model of itself (possibly without latent variables, since the effects of one's own actions on proprioception are more predictable than the external world's evolution), which can double as a template for modeling other agents.

World state at each level is proposed to be maintained not as a flat vector but in a **key-value associative [[phd/wiki/concepts/short-term-memory-module|memory]]**, updated only where an event actually changes the state, akin to memory-augmented networks and entity networks, with the world model's output taking the form of query-value pairs used to modify or add memory entries — all differentiably, so gradients can be backpropagated through memory operations.

### Relationship to the rest of the cognitive architecture

H-JEPA feeds directly into the [[phd/wiki/concepts/actor-module|actor module]]'s three roles: inferring optimal action sequences via the [[phd/wiki/concepts/cost-module|cost module]] and predictions from the world model, producing latent-variable configurations representing unknown portions of world state, and training [[phd/wiki/concepts/policy-module|policy networks]] for fast Mode-1 reactive action. When the world model and cost are well-behaved, gradient-based optimization can backpropagate through the unfolded H-JEPA and cost to infer optimal action sequences (a hierarchical instance of [[phd/wiki/concepts/model-predictive-control|model-predictive control]]); when they are not, gradient-free methods (dynamic programming, beam search, Monte-Carlo tree search) are proposed as alternatives.

### Open questions flagged by the source

The paper is explicit that H-JEPA is a proposal rather than a demonstrated system. It flags as unresolved: whether an H-JEPA can actually be built and trained end-to-end from raw video; whether it would learn the sort of abstract concept hierarchy (edges, depth, occlusion, object permanence, intuitive physics) hypothesized elsewhere in the document; which latent-regularization mechanism (discrete, low-dimensional, sparse, or stochastic) will prove best in practice; and how the [[phd/wiki/concepts/configurator-module|configurator module]] — responsible for decomposing a complex task into a sequence of subgoals across the hierarchy — would actually learn to do so, which the paper calls the most mysterious and least specified part of the whole architecture. The source also notes that humans appear able to spontaneously cycle through alternative interpretations of an ambiguous percept (citing the Necker cube), and that H-JEPA as specified lacks a described mechanism for this kind of exploration across multiple latent configurations during Mode-2 planning.

### Relation to prior/adjacent work named in the source

H-JEPA is positioned against the paper's broader survey of learned world models and hierarchical planning in the literature: it contrasts with the [[phd/wiki/concepts/dyna-architecture|Dyna architecture]]'s Mode-2-style model use in reinforcement learning, with Wayne and Abbott's stack of trained forward models specifying intermediate goals, with pose-parameter goal specification in some robotics work, and with the Director system's end-to-end hierarchical world model trained via reinforcement learning — the paper explicitly calls hierarchical planning "a largely unsolved problem," situating H-JEPA as its proposed, but untested, resolution route.

---

**projectRelevance:**
- thesis-topic-shift-world-models-vs-llms — H-JEPA is the paper's flagship architecture for multi-scale, multi-abstraction predictive world models and is central evidence for the strengths (and open weaknesses) of world-model approaches versus LLMs that this project needs to evaluate for the thesis pitch.

Source: [[phd/wiki/sources/phd202610356apathtowardsautonomousmach|10356_a_path_towards_autonomous_mach]]
