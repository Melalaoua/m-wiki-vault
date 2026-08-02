---
type: source
title: "World Models"
citekey: phd2026world
source_type: pdf
captured: 2026-08-02
site: phd
url: 
raw: phd/raw/phd/1803.10122v4.pdf
aliases: []
tags: [source, personal]
updated: 2026-08-02
status: developing
read_status: critiqued
last_sitting: 2026-08-02T15:39:39.430Z
---

# World Models

Original: [[phd/raw/phd/1803.10122v4.pdf]]

## Skim (pass 1)

**Your recall:**

The proposed architecture in this paper is elegantly capable of encoding the observed world in it currently situated in (virtual for now), encode it and use the latent state in his internal world model to take action. The architecture is capable of driving a false formula car in a openAI gym environment, or dodge fireballs in another.

The architecture is capable of modelling the future state of the world by 'dreaming' and coming up with hypothetical scenarios on its own.

**Your triage verdict:** worth pass 2

**My own read (after yours):**

### My Calibration Read

"World Models" introduces a modular reinforcement learning architecture that decouples representation learning from policy optimization using three components: a Variational Autoencoder (V) for spatial compression, an MDN-RNN (M) to predict future temporal states, and a highly compact linear controller (C) trained via evolution strategies. Its primary contribution is demonstrating that an agent can be trained entirely inside its own "hallucinated dream"—a virtual environment simulated in the latent space of the predictive world model—and successfully transferred back to solve the actual task. 

**One thing worth noting** is the challenge of "cheating" the world model, where the controller exploits inaccuracies in the simulator to find adversarial policies (e.g., making fireballs disappear). To prevent this, the authors introduce a temperature parameter ($\tau$) to inject stochasticity into the MDN-RNN, proving that training agents in a noisier, high-uncertainty dream world actually forces them to learn highly robust policies that generalize better to the real environment.

## Pass 2 (your takeaways)

### p. 2

**Your recall:**

The initial motivation for implementing world model is to mimic real human behavior. We usually imagines lower-dimensional world in our head in order to take action. The proposed architecture is motivated by implementing the same idea inside reinforcement algorithms by allowing them to compute lower-dimensional version of their observed world and to take action based on the calculated state

Recall check: needed the answer revealed.

**Your critique:**

How can we be sure that the world model is capable of effectively predict the causal effect of actions & encode the multitude of parameters that real world encode

**My objection (mine, after yours):**

**My objection:** A more immediate structural hazard is the inevitability of the controller exploiting the world model's inevitable flaws. When an agent is trained entirely inside a hallucinated environment, the optimization process acts as an adversary that actively searches for and overfits to the model's approximation errors, such as unphysical state transitions. Because the controller is given a massive search space over the model's hidden dynamics, it will easily develop unrealistic "exploits" that yield high virtual rewards in the dream but cause catastrophic failure when the policy is transferred back to the actual, unexploitable environment.

### pp. 3–4

**Your recall:**

The three core components proposed : 
1. The vision model : an variational autoencoders encoding an abtract, compressed representation of the world.
2. The M model : predict the future based on the observed compressed state (z) from the V model and the action taken by the controler.
3. Takes as input the current observed state (z) of the world and the prediction (hidden state h) of the world model and produce an action. The action is fed back to the world model and the action is taken by the agent (action fed into the environment).

**Your critique:**

I do not identify objection to the stretch.

**My objection (mine, after yours):**

**My own objection:** A major vulnerability in this framework is the decoupled, unsupervised training of the VAE (V) model, which relies strictly on pixel-level reconstruction loss and is completely blind to task-specific rewards. Consequently, the model risks discarding small but critical task-relevant features (such as distant hazards or fine track indicators) while dedicating valuable latent capacity to reconstructing prominent but task-irrelevant background details. This representation bottleneck severely limits the approach's scalability to complex environments where key decision-making cues are visually subtle.

### pp. 5–6

**Your recall:**

Two experience were made : First the controler has access to only the vision model (VAE) and second access to both the vision model and the M-model. 

1. The model has decent results, but struggle on sharp turns and unexpected turns.
2. The model is much more intuitive and good to follow the tracks.

**Your critique:**

I don't knbow

**My objection (mine, after yours):**

**My Objection:** 

A critical bottleneck in this framework is the complete decoupling of the vision model (VAE) from the downstream reinforcement learning objective. Because the VAE is trained in a purely unsupervised, task-agnostic manner, it allocates its latent capacity based entirely on pixel-wise reconstruction loss, leading it to compress high-variance background details while ignoring tiny, task-critical features (like distant fireballs or minor road details) that represent only a fraction of the pixel variance. Without a top-down feedback mechanism or joint training with the reward signal, the agent is highly vulnerable to losing vital information in the bottleneck of its own world model.

### pp. 7–10

**Your recall:**

Yes, the agent can successfully learn a policy within a hallucinated dream as observed by increasing the temperature Tau, the virtual score is higher, also the actual score of the agent

Recall check: needed the answer revealed.

**Your critique:**

I don't know

**My objection (mine, after yours):**

**My Objection:** 

A key weakness of this decoupled architecture is the task-agnostic nature of the unsupervised VAE, which compresses visual scenes without any awareness of downstream goals or rewards. Because the vision and memory models are trained independently of the controller, the system is highly prone to discarding tiny, task-critical visual features—such as distant hazards or subtle goal-related cues—while wasting valuable network capacity on high-frequency, task-irrelevant background textures. This architectural separation prevents the world model from scaling effectively to visually complex environments where success depends on detecting fine-grained, reward-relevant details.

### p. 11

**Your recall:**

Adopt a more curious approach by the model in training by rewarding curiosity, information seeking, novel exploration of the world it does not know yet.

Recall check: needed the answer revealed.

**Your critique:**

The agnostic nature of the VAE which is compress to pixel-level what it sees. By compressing what it observes, the VAE can miss important features/elements which can be crucial to the world model.

**My objection (mine, after yours):**

**My Objection:**

While the unsupervised VAE's lossy compression is a major bottleneck, a more fundamental vulnerability of this architecture is the controller's susceptibility to discovering adversarial policies that exploit inaccuracies in the MDN-RNN's dynamic transitions. Because the controller is trained entirely inside a simulated "dream" environment, it can easily learn to manipulate the model's imperfect statistical approximations—such as tricking the memory model into never generating fireballs—leading to behaviors that achieve perfect scores in simulation but fail catastrophically in the real environment. Mitigating this exploitability requires delicate tuning of the environment's "temperature" ($\tau$) to artificially inject noise, which merely papers over the world model's underlying incapacity to strictly enforce actual physical laws.

### p. 12

**Your recall:**

Feed-Forward convolutional Network (CNN) in games are an excellent approach to learn world dynamics

**Your critique:**

I don't knwo

**My objection (mine, after yours):**

**My Objection:** 
The proposed architecture relies heavily on a decoupled, unsupervised VAE (V Model) that optimizes purely for pixel-level reconstruction loss, which is a major bottleneck for complex environments. Because the spatial representations are learned independently of the task's reward signal, the VAE is highly prone to wasting network capacity on visually dominant but task-irrelevant background details while completely dropping tiny, pixel-sparse cues that are critical for decision-making. This lack of goal-directed representation learning severely limits the paradigm's scalability to visually rich environments where the agent must distinguish subtle, task-critical objects from complex background noise.

### p. 13

**Your recall:**

?

Recall check: needed the answer revealed.

**Your critique:**

I don't know

**My objection (mine, after yours):**

**My objection:** 

The framework's heavy reliance on a random policy to gather the initial training dataset of 10,000 rollouts is a major bottleneck that limits its scalability to complex environments with sparse rewards. In more sophisticated tasks, random exploration will fail to uncover critical state-spaces or transition dynamics, leaving the VAE and MDN-RNN entirely blind to task-essential features. Without an online, active exploration strategy tightly coupled with the world model's training from the start, this offline separation of representation learning and policy optimization remains highly restricted to simple, easily explorable domains.

### pp. 14–21

**Your recall:**

1. The image is downsized to 64x64 pixel. The VAE produce two vectors tau and micron
2. An LSTM + a mixture density network are used for the M model. Trained in 20 epochs.
3. CMA-ES was used to train the M model.

Recall check: answered correctly on the follow-up. ✅

**Your critique:**

I don't know

**My objection (mine, after yours):**

**My Objection:** 

A major limitation of this approach is the compounding error inherent in the MDN-RNN's step-by-step autoregressive predictions, which causes the simulated "dream" environment to rapidly drift away from actual game physics over longer horizons. Because the VAE is trained entirely unsupervised and independently of the task's reward structure, the compressed latent space frequently discards critical but visually small task-relevant details (like distant hazards) while wasting capacity on irrelevant background textures. This representation decoupling makes the agent highly prone to exploiting inaccuracies in the dynamics model, necessitating fragile, environment-specific tuning of the temperature parameter ($\tau$) to prevent policy failure during transfer.

## Critique (pass 3)

### Strongest objection

**Your answer:**

1. The variational encoder can miss important detail or add irrelevant detail to the latent state, hindering the world model capabilities.

**My calibration (mine, after yours):**

**My objection:** 

While representation loss in the encoder is a bottleneck, a more critical vulnerability lies in compounding prediction errors and the resulting adversarial exploitation of the transition model (M) during long-horizon rollouts. Because the controller is trained entirely inside its own hallucinated "dreams," it easily discovers and exploits unphysical transition dynamics (such as the "extinguishing fireballs" exploit) where the predictive model's approximations break down. The authors' proposed solution of manually tuning a temperature parameter ($\tau$) is a fragile, task-dependent heuristic that does not scale to complex, high-dimensional environments where compounding model drift is inevitable.

### Alternative explanation

**Your answer:**

I don't know

**My calibration (mine, after yours):**

**My assessment:** 

An alternative explanation for the high transferability of the VizDoom policy is that the injected temperature ($\tau = 1.15$) acted as a form of brute-force domain randomization rather than a high-fidelity simulation of game dynamics. By forcing the controller to survive in an artificially chaotic, hyper-stochastic dream environment, the evolutionary algorithm may have simply regularized the policy to adopt an extremely conservative, jittery obstacle-avoidance heuristic. Consequently, its success in the actual environment might stem from this over-sensitized behavioral robustness rather than the agent developing a genuine, predictive "mental model" of enemy fireball trajectories.

### Falsifying experiment

**Your answer:**

I don't know

**My calibration (mine, after yours):**

**My calibration:** 

A critical gap left open is designing an experiment to test whether the policy trained inside the "hallucinated dream" fails to generalize when the real environment introduces fine-grained, chaotic dynamics that the lossy VAE and MDN-RNN compression cannot capture. For example, one could systematically introduce minor physical perturbations—such as sudden wind resistance in the Car Racing environment or micro-latencies in VizDoom—and measure if the dream-trained policy collapses while a traditionally trained model-free policy remains robust. If the dream-trained agent cannot adapt to these subtle but critical real-world variations, it would falsify the core claim that unsupervised world models can reliably replace training in the actual environment.
