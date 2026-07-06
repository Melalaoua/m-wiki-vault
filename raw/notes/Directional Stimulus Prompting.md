tags:: #thelaboratory/AI 

[Li et al., (2023)](https://arxiv.org/abs/2302.11520) propose une nouvelle méthode de prompting afin de mieux guider le LLM pour générer l'output voulu.

Un LM de "police" tunable est entrainé afin de générer le stimulus/astuce. 

Ci-dessous le direction stimulus prompting en comparaison avec des méthodes standard de prompting. Le LM de police peut être petit et optimisé pour générer des astuces qui vont guider un autre LLM avec des paramètres gelés.

![[Pasted image 20230715080720.png]]

> Suiv [[ReAct]]
> Prev [[Active-Prompt]]