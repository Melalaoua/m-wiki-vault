**authors**:: Albert Q. Jiang, Alexandre Sablayrolles, Antoine Roux, Arthur Mensch,
Blanche Savary, Chris Bamford, Devendra Singh Chaplot, Diego de las Casas,
Emma Bou Hanna, Florian Bressand, Gianna Lengyel, Guillaume Bour,
Guillaume Lample, Lélio Renard Lavaud, Lucile Saulnier, Marie-Anne Lachaux,
Pierre Stock, Sandeep Subramanian, Sophia Yang, Szymon Antoniak, Teven Le Scao,
Théophile Gervet, Thibaut Lavril, Thomas Wang, Timothée Lacroix, William El Sayed
**date**::   ```2024-01-13 14:44 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI
**sous-groupe**:: #AI/models 
**pertinence**:: 10
**links**:: https://arxiv.org/abs/2401.04088?utm_source=substack&utm_medium=email,  https://www.youtube.com/watch?v=mc2Qli9ImOI
**modification date**:: ```Saturday 13th January 2024 14:44:07 ```

```ad-abstract
We introduce Mixtral 8x7B, a [[A Review of Sparse Expert Models in Deep Learning|Sparse Mixture of Experts (SMoE)]] language model. Mixtral has the same architecture as Mistral 7B, with the difference that each layer is composed of 8 feedforward blocks (i.e. experts). For every token, at each layer, a router network selects two experts to process the current state and combine their outputs. Even though each token only sees two experts, the selected experts can be different at each timestep. As a result, each token has access to 47B parameters, but only uses 13B active parameters during inference. Mixtral was trained with a context size of 32k tokens and it outperforms or matches Llama 2 70B and GPT-3.5 across all evaluated benchmarks. In particular, Mixtral vastly outperforms Llama 2 70B on mathematics, code generation, and multilingual benchmarks. We also provide a model fine-tuned to follow instructions, Mixtral 8x7B - Instruct, that surpasses GPT-3.5 Turbo, Claude-2.1, Gemini Pro, and Llama 2 70B - chat model on human benchmarks. Both the base and instruct models are released under the Apache 2.0 license.
```

## Notes
- [[A Review of Sparse Expert Models in Deep Learning|Architecture SMoE]] avec 32K de contexte pour 13B de paramètres "actifs" pendant l'inference (plus rapide). ![[Pasted image 20240113145731.png]]
- Decoder-only (comme GPT)
- Meilleure performances que LLAMA2 (70B) et que GPT3.5.
- Basé sur l'architecture [[Attention is all you need|transformers]]
- Le papier aborde la technique [Megablock](https://arxiv.org/abs/2211.15841) pour entrainer plus efficacement (+40%) les MoE et la technique [Expert Parallelism](https://arxiv.org/abs/1701.06538) 
- Reprend les fonctionnalités d'un modèle mistral 7b classique :
	- Sliding window : Entrainés ur 8K context length mais avec une fenêtre théorique de 128K tokens.
	- GQA : Grouped Query Attention : plus rapide.

![[Pasted image 20240117141830.png]]

- D'après [HuggingFace](https://huggingface.co/docs/transformers/model_doc/mixtral) , le nombre total de paramètre s'élève à 85B, toutefois avec l'architecture SMoE, la puissance de calcul nécessaire équivaut à celle d'un modèle 14B. Mais à priorit les 8 couches doivent être chargée dans la RAM (70 gB).
- "If the model is quantized to 4bits, a single A100 is enough to fit the entire 84B model." = coût d'une A100 : 20 279€ (LDLC)
- Présentent aussi Mixtral 8x7B finetuned par [[Direct Preference Optimization  - Your Language Model is Secretly a Reward Model|DPO]] 
- 32K context window
![[Pasted image 20240117142609.png]]

- Distinction entre le **==sparse paramater count==** : c'est à dire le nombre total de paramètres et le **==Active parameter count==** qui est le nombre total de paramètres du nombre K d'experts choisis.

- Le MoE layer peut être [[MegaBlocks - efficient sparse training with Mixture-Of-Experts|distribué sur un seul GPU]],  ou bien [[Expert Parallelism - The Sparsely-Gated Mixture of Experts Layer|répartis sur de multiples GPU]]. 

- Pas de patternes évidents observés dans les experts : il n'y a pas d'expert "spécialisés" en biologie, mathématiques, etc..




```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```