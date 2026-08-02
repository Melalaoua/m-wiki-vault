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
read_status: skimmed
last_sitting: 2026-08-02T15:06:30.253Z
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
