tags:: #thelaboratory/AI 

![[Pasted image 20230714121452.png]]
Source : [Zhou et al., (2022)](https://arxiv.org/abs/2211.01910)

Zhou et al proposent APE, une manière automatique d'ingénieur de Prompt. C'est un framework automatic pour générer des instructions, la sélection des instructions est aussi automatique.

La génération des instructions se fait en langage naturel et adressé à une boîte noire d'optimisation en utilisant des LLMs afin de générer et chercher des candidats.

La première étape implique un LLM a qui on donne un exemple d'output afin de générer les instructions candidates les plus adéquates.

Ces solutions candidates vont guider les procédures suivantes. Les instructions sont exécutée en utilisant un modèle cible, ainsi, la meilleur solution est choisie basée sur des scores.


APE démontre un meilleur prompting que le "Let's think step by step" du [[Chain-of-Thought Prompting]] ([kojima et al., (2022)](https://arxiv.org/abs/2205.11916))

Le prompt "Let's work this out in a step by step way to be sure we have th eright answer" implique du [[Chain-of-Thought Prompting]] et améliore les performance des benchmarks  MultiArith et GSM8K :
![[Pasted image 20230714122155.png]]

Ce papier montre l'importance des sujet liés au prompt engineering qui est d'optimiser automatiquement les prompts. Voici quelques papiers intéressant sur le sujet :
- [AutoPrompt](https://arxiv.org/abs/2010.15980) : propose une approche d'automatiquement créer des prompts pour un set de diverses tâches basé sur un recherche guidée par le gradient.
- [Prefix tuning](https://arxiv.org/abs/2101.00190) : un alternative plus légère de fine-tuning qui gèle les paramètres du LLM mais optimise une sous-ensemble spécifique de vecteur, relatifs à certaines tâches (appelés préfix).
- [Prompt tuning](https://arxiv.org/abs/2104.08691) : propose un méchanisme de soft-apprentissage via des prompts et en utilisant la back-propagation.


> Suiv [[Active-Prompt]]
> Prev : [[Automatic Reasoning and Tool-use]]