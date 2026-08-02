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
updated: 2026-08-02
status: developing
read_status: pass2
last_sitting: 2026-08-02T13:26:09.988Z
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

## Pass 2 (your takeaways)

### §1 Introduction to Dyna, p. 2

**Your recall:**

The core intuition behind the dyna architecture is that the more pragmatic way for robot to evolve in uncertain environments  is by planning based on what it learnt and observed before

**Your critique:**

I assume the gap you're talking about is that the computational ressource to plan at inference time are scarce, it was just not possible for robot to plan when faced with uncertainty at inference time. I think it's actually real, yes

**My objection (mine, after yours):**

**My objection:** While you focus on computational scarcity, this overlooks the critical issue of safety and sample inefficiency in the trial-and-error learning process that Dyna proposes as a fallback. In physical robotics, unconstrained online exploration is rarely feasible because trial-and-error actions can easily cause catastrophic, irreversible damage to the hardware or environment before an accurate model can be learned. Thus, the primary gap in classical planning is often addressed not through real-world trial-and-error, but through high-fidelity offline simulation, robust control theory, or strict safety-critical constraints.

### §2 Dyna-PI: Dyna by Approximating Policy Iteration, p. 3

**Your recall:**

Easy, 4 components : 
1. The policy which is basically an action for the robot to follow. The action is calculated based on the current state of the world.
2. The world : the external environment. Receives the action from the policy and output a state n+1 which reflects the consequences of the action.
3. Mimic of the world.
4. The evaluation function : updates the world model & policy based on the produced state

Recall check: needed the answer revealed.

**Your critique:**

How can we be sure of the map produced by the evaluation function is correct ?

**My objection (mine, after yours):**

**My Objection:** 

While the user's objection focuses on the accuracy of the evaluation function, a more critical bottleneck lies in the highly inefficient search control mechanism used for planning. By selecting states for hypothetical experiences uniformly at random, the algorithm wastes immense computational resources simulating irrelevant or distant states that have no bearing on the agent's immediate path. Without a targeted heuristic to prioritize which state-action transitions to replay, this planning approach fails to scale effectively beyond small, tabular grid-worlds.

### §3 A Navigation Task, pp. 4–5

**Your recall:**

An improvement x100 better than without planning. The architecture takes 10~ish steps per trial instead of few hundreds without planning. The Dyna-PI architecture greatly enhance performance in the maze task.

**Your critique:**

This implies that the environment stay the same without evolving or changing over-time ?

**My objection (mine, after yours):**

**My objection:** 

A fundamental vulnerability of the proposed Dyna architecture is its susceptibility to compounding model errors, where planning using an inaccurate or incomplete world model can severely degrade both the policy and value functions. In realistic, high-dimensional, or stochastic environments, learning a precise transition model is often exponentially harder than learning a model-free policy directly. By evaluating the system only on a tiny, deterministic grid-world where a perfect tabular model can be quickly memorized, the paper glosses over how easily minor errors in a learned model can compound during hypothetical "relaxation planning" steps, ultimately leading the agent to optimize for a delusional representation of reality.

### §4 Problems of Changing Worlds

**Your recall:**

If a blocking object is added, the  system will takes a hundred step to find a way around it. Even if it's most optimal path is now blocked, it'll not try to find another route since all others hypothetical actions are reduced to 0.
The same happens if a shortcut is added, the model will stay on it optimal path calculated before the shortcut wasn't existing

Recall check: answered correctly on the follow-up. ✅

**Your critique:**

I don't know.

**My objection (mine, after yours):**

**My objection:** 

The proposed solution to the shortcut and blocking problems in Dyna-Q+ relies heavily on a tabular exploration bonus ($\sqrt{n_{xa}}$) that tracks the exact time elapsed since a specific state-action pair was last experienced. In any realistic, continuous, or high-dimensional state space, exact states are virtually never visited twice, which renders this tabular tracking metric completely useless. Without a mechanism to generalize uncertainty and exploration bonuses across similar states, the architecture's ability to handle changing environments cannot scale beyond trivial, discrete grid worlds.

### §5 Dyna-Q: Dyna by Q-learning, p. 6

**Your recall:**

Dyna-Q implements  Q-Learning proposed by Watkins in 1983 which is a different reinforcement learning technique ; policy and evaluation are now maintained together. The system calculate a matrice of state-action pairs and keep only the best one. This reduce the data structure from two to one, remove an update rule, and eliminate the alpha parameter.

**Your critique:**

I don't know

**My objection (mine, after yours):**

**My Objection:** 

The framework’s reliance on a learned world model assumes the model can accurately represent the environment, but in complex or stochastic real-world scenarios, learning an accurate transition model is notoriously difficult. Even minor inaccuracies or approximations in this learned model can be severely exploited during the offline "hypothetical" planning phases, leading to highly suboptimal or catastrophic policies when executed in the actual world. This fundamental challenge of "model exploitation" is entirely obscured by the paper’s reliance on simple, deterministic, and tabular grid-world demonstrations.

### §6 Changing-World Experiments, pp. 7–8

**Your recall:**

The DYna-Q+ is much efficient and faster, adapting very well to environment changes like block and shortcuts.

**Your critique:**

The numbers actually support the claim.

**My objection (mine, after yours):**

**My Objection:** 

While the charts display visually distinct performance curves, the paper relies entirely on qualitative visual inspection of averages without reporting any measures of statistical variance, such as standard deviation, standard error, or confidence intervals. Because reinforcement learning processes utilizing stochastic exploration (like Boltzmann action selection) naturally exhibit high run-to-run variability, the absence of dispersion metrics makes it impossible to determine whether the reported differences are statistically robust or represent a stable, meaningful effect size. Consequently, the raw numbers provided are insufficient to scientifically validate the magnitude of the claims.

### §7 Limitations and Conclusions, p. 9

**Your recall:**

The dyna is inefficient in high dimensional complex spaces.

**Your critique:**

I did not understand your question

**My objection (mine, after yours):**

**My objection:** Although the author claims that Dyna architectures are "fully compatible" with compact function approximators like connectionist networks to handle larger state spaces, the empirical results are strictly limited to a trivial, tabular 54-state grid-world. In practice, combining off-policy bootstrapping planning (such as Q-learning in Dyna) with function approximation introduces severe risks of representation drift, instability, and divergence. These fundamental challenges of scaling the architecture are entirely masked by the perfect, low-dimensional state representations used in the paper's simple simulations.
