---
type: concept
title: "Model-Predictive Control"
aliases: []
tags: [concept, phd]
updated: 2026-08-21
status: developing
---

# Model-Predictive Control

## Model-Predictive Control

Model-Predictive Control (MPC) is a classical planning and reasoning paradigm from optimal control theory, used in the paper "A Path Towards Autonomous Machine Intelligence" as the conceptual template for **Mode-2** reasoning within its proposed [[phd/wiki/concepts/cognitive-architecture|cognitive architecture]]. The paper's central move is to reframe MPC not as a technique relying on hand-engineered dynamics and objectives, but as a procedure whose two core components — the [[world-models|world model]] and the [[phd/wiki/concepts/cost-module|cost module]] — are learned end-to-end.

### MPC as the mechanism of Mode-2

The paper describes the [[phd/wiki/concepts/actor-module|actor module]]'s deliberative operation (Mode-2, contrasted with the purely reactive Mode-1) as proceeding through a cycle: the actor proposes an initial sequence of actions, the world model predicts the resulting sequence of world states, the cost module evaluates a total cost as a sum over time steps, and the actor then revises the action sequence to lower that cost, typically via [[phd/wiki/concepts/gradient-based-optimization|gradient-based optimization]] through backpropagation, though [[phd/wiki/concepts/dynamic-programming|dynamic programming]] and other gradient-free strategies (combinatorial optimization, simulated annealing, heuristic tree search) are also admitted when the action space is discrete or the cost landscape is non-smooth. This is stated explicitly to be "akin to model-predictive control in optimal control" (citing Bryson and Ho, 1969), and elsewhere as being "essentially what is known as Model-Predictive Control (MPC) with receding horizon in the optimal control literature."

Only the first action of the optimized sequence is executed, after which the cycle repeats with updated perception — the standard receding-horizon character of MPC — though the paper does not dwell on this detail beyond invoking the MPC label itself.

### The paper's contribution: learned dynamics and learned cost

The document is explicit that what distinguishes its use of MPC from classical optimal control is that **both the model and the objective are learned rather than designed by hand**: "The difference with classical optimal control is that the world model and the cost function are learned." This reframes MPC's two traditional engineering burdens — building an accurate dynamics model of the plant/environment, and specifying a cost function that encodes the desired behavior — as learning problems solved by the architecture's other modules:

- The world model is trained largely through [[phd/wiki/concepts/self-supervised-learning|self-supervised learning]] on observed trajectories, particularly via the [[phd/wiki/concepts/joint-embedding-predictive-architecture|Joint Embedding Predictive Architecture]] (JEPA) and its hierarchical extension (H-JEPA), rather than being derived from first-principles physics or system identification.
- The cost function is decomposed into an immutable [[phd/wiki/concepts/intrinsic-cost-module|Intrinsic Cost module]] (hard-wired basic drives) plus a [[phd/wiki/concepts/trainable-critic-module|Trainable Critic module]] that learns to predict future intrinsic energy — allowing the objective driving MPC's optimization to itself be shaped by training and by the [[phd/wiki/concepts/configurator-module|configurator module]]'s subgoal-setting, rather than fixed a priori.

This learned-MPC framing is what lets the architecture use imagined rollouts through the world model to search for good action sequences "lessening the need to perform an expensive and dangerous search for good actions... by trying multiple actions in the external world" — directly addressing the sample-inefficiency problem the paper opens with. Because both the world model and cost module are differentiable, gradients of the estimated cost can be backpropagated through the unrolled world model to the proposed actions, giving MPC-style optimization a route that classical, hand-modeled MPC does not have by default.

### Related mechanisms in the same framework

- **Uncertainty handling**: since the world model may be inexact or the environment stochastic ([[phd/wiki/concepts/aleatoric-uncertainty|aleatoric uncertainty]], [[phd/wiki/concepts/epistemic-uncertainty|epistemic uncertainty]]), MPC-style planning in this architecture must evaluate multiple predicted trajectories (via sampled latent variables) and can optimize for average cost or a risk-sensitive combination of average and variance of cost.
- **Hierarchical MPC**: the paper extends the MPC loop to a hierarchical setting where high-level predicted states/actions serve as conditions or targets that lower-level MPC-style optimization must satisfy — described as a modern, learned analogue of the "action as condition satisfaction" idea from classical proportional servomechanisms.
- **Amortization**: repeatedly solving the MPC optimization is costly, so the paper proposes training a reactive [[phd/wiki/concepts/policy-module|policy module]] to approximate the optimal actions found by Mode-2/MPC, via [[phd/wiki/concepts/amortized-inference|amortized inference]] — letting skills learned through costly planning be "compiled" into fast, planning-free Mode-1 behavior.
- **Prior art acknowledged**: the paper situates its proposal against Sutton's [[phd/wiki/concepts/dyna-architecture|Dyna Architecture]] (Mode-2-style inference over actions using a predictive model in reinforcement learning) as an older instance of the same MPC-via-learned-model idea, and notes MPC's roots go back to classical optimal control (Bryson and Ho, 1969).

### Significance

The paper's positioning of Mode-2 as "MPC with learned world model and cost" is a load-bearing conceptual bridge: it lets a differentiable, trainable [[phd/wiki/concepts/cognitive-architecture|cognitive architecture]] inherit a well-understood control-theoretic planning procedure while replacing its two hand-designed ingredients with modules trained from data — world models learned largely by observation and objectives learned/composed from intrinsic drives and a trainable critic. This is the mechanism by which the architecture claims to support reasoning and planning without relying on symbolic logic, addressing one of the paper's opening challenges: reconciling gradient-based learning with reasoning and planning.

### Project relevance

- [[phd/wiki/maps/thesis-topic-shift-world-models-vs-llms|thesis-topic-shift-world-models-vs-llms]]: this MPC framing is a concrete mechanism by which learned world models support planning and reasoning — a capability the paper argues generative LLMs lack (they cannot dynamically specify goals or search over action sequences against a learned cost). It bears directly on the open question of how world-model approaches could translate into reasoning/planning strengths relevant to diagnosis, versus LLMs' more limited reasoning.

Source: [[phd/wiki/sources/phd202610356apathtowardsautonomousmach|10356_a_path_towards_autonomous_mach]]
