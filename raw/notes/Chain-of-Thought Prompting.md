tags:: #thelaboratory/AI 
source:: [[Chain-of-Thought Prompting Elicits Reasoning in Large Language Models]]

Le CoT permet de réaliser des raisonnements plus complexes via l'introduction d'étapes intermédiaires. On peut combiner le [[Few-shot Prompting]] à cette technique pour obtenir des résultats meilleurs.


![[Pasted image 20230712194445.png]]
> [Source](https://arxiv.org/abs/2201.11903)

*Prompt*
```
The odd numbers in this group add up to an even number: 4, 8, 9, 15, 12, 2, 1.
A: Adding all the odd numbers (9, 15, 1) gives 25. The answer is False.

The odd numbers in this group add up to an even number: 17, 10, 19, 4, 8, 12, 24.
A: Adding all the odd numbers (17, 19) gives 36. The answer is True.

The odd numbers in this group add up to an even number: 16, 11, 14, 4, 8, 13, 24.
A: Adding all the odd numbers (11, 13) gives 24. The answer is True.

The odd numbers in this group add up to an even number: 17, 9, 10, 12, 13, 4, 2.
A: Adding all the odd numbers (17, 9, 13) gives 39. The answer is False.
The odd numbers in this group add up to an even number: 15, 32, 5, 13, 82, 7, 1. 
A:
```

*Output*
```
Adding all the odd numbers (15, 5, 13, 7, 1) gives 41. The answer is False.
```


### Zero-shot COT.
---
![[Pasted image 20230712194651.png]]
> [Source](https://arxiv.org/abs/2205.11916)

Une idée plus récente est le [[Zero-shot Prompting|zero-shot]] CoT qui consiste à rajouter des "Réfléchissons étape par étape" au prompt original. Voici un exemple simple

*Prompt*:
```
I went to the market and bought 10 apples. I gave 2 apples to the neighbor and 2 to the repairman. I then went and bought 5 more apples and ate 1. How many apples did I remain with?
```

*Output*
```
11 apples
```

C'est faux, maintenant changeons notre prompt original.

```
I went to the market and bought 10 apples. I gave 2 apples to the neighbor and 2 to the repairman. I then went and bought 5 more apples and ate 1. How many apples did I remain with? Let's think step by step.
```

*Output*
```
First, you started with 10 apples.
You gave away 2 apples to the neighbor and 2 to the repairman, so you had 6 apples left.
Then you bought 5 more apples, so now you had 11 apples.
Finally, you ate 1 apple, so you would remain with 10 apples.
```

On voit l'efficacité du "Réfléchissons étape par étape" dans ce sujet là.


### Auto-CoT.
---
Le CoT implique de rajouter manuellement des exemples pour montrer le raisonnement à suivre par le modèle. Cet effort peut mener à des solutions plus optimisées. [Zhang et al (2022)](https://arxiv.org/abs/2210.03493) proposent une approche similaire afin d'éliminer l'étape manuelle du CoT en mettant en avant le "Let's think step by step" et générer des chaines de raisonnement étape par étape chez les bots.

Ce processus peut toutefois mener à des erreurs et de fait une diversification entre les few-shot CoT et le Zero-shot CoT est nécessaire. Les auteurs proposent l'auto-CoT, qui prends pour exemple des question diversifiées et génères des raisonnements pour construire des démonstrations.

Auto-Cot consiste en 2 étapes principales : 
- Stage 1) **question clustering** : Séparer les questions d'un dataset en plusieurs groupements.
- Stage 2) **Demonstration sampling** : Selectionner un portion représentative des questions pour chaque cluster et générer des chaînes de raisonnement en utilisant le zero-shot CoT avec de simples [[Heuristics|heuristiques]].

Les heuristiques peuvent être tout simplement des chaines de question, encourageant le modèle à utiliser des démonstrations simples et précises.

The processus est démontré ci-dessous.
![[Pasted image 20230712233642.png]]


> Suiv [[Self-Consistency]]
> Prev [[Few-shot Prompting]]