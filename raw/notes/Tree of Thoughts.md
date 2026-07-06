tags:: #thelaboratory/AI 

Pour les tâches qui nécessitent de l'expérimentation, de la stratégie, les prompts traditionnelles échouent. [Yao et el. (2023)](https://arxiv.org/abs/2305.10601) et [Long (2023)](https://arxiv.org/abs/2305.08291) ont récemment proposé le ToT ou Tree of Thougts. 

C'est un framework qui généralise au dessus du [[Chain-of-Thought Prompting]] et encourage l'exploration vers des pensées qui servent d'étapes intermédiaire au problème général.

ToT mantien un arbre de pensées, où les pensées (ou relfexions) représentent une séquence de langages cohérents et intermédiaires vers la résolution du problème.
Cette approche permet au LLM de s'auto-évaluer sur sa progression vers la résolution du problème via un processus de raisonnement.

La capacité du LLM a générer et évaluer des pensées/raisonnements est ensuite combiné à des algorithmes de recherches (e.g breadth-first search and depth-first search) afin d'établir une exploration systématique des raisonnements avec anticipation et retour en arrière.

Le framework ToT est illustré ci-dessous.
![[Pasted image 20230713172409.png]]

Quand on utilise le ToT, différentes tâches requiert de définir un nombre de candidats et aussi le nombre d'étapes et le nombre de pensées/reflexions. Par exemple, comme démontré dans le papier, un jeu de 24 est utilisé comme raisonnement mathématique, qui requiert de décomposer ses pensées en 3 étapes, chacune impliquant une question intermédiaire. A chaque étape, le Bo5 des candidats est gardé.

Pour effectuer un BFS dans un ToT pour le jeu de 24, le LLM est chargé d'évaluer chaque reflexions-candidate en "certainement, peut être, impossible" avec l'objectif d'atteindre 24.

Comme décrit pas les auteurs, l'idée est promouvoir les idées partiellement correct via une évaluation par anticipation, et éliminer les candidats impossibles à réaliser basé sur un "trop coûteux/peu coûteux", les autres sont conservés sous "peut être". Les valeurs sont échantillonnées trois fois pour chaque raisonnement. Le processus est décrit ci-dessous.
![[Pasted image 20230713172959.png]]


On peut voir que le ToT surpasse les autres techniques de prompting

![[Pasted image 20230713173347.png]]

Code disponible [ici](https://github.com/princeton-nlp/tree-of-thought-llm) et [ici](https://github.com/jieyilong/tree-of-thought-puzzle-solver)


Le ToT en prompting : 
```
Imagine three different experts are answering this question.All experts will write down 1 step of their thinking,then share it with the group.Then all experts will go on to the next step, etc.
If any expert realises they're wrong at any point then they leave.The question is...
```


>Suiv [[Retrieval Augmented Generation]]
>Prev [[Generate Knowledge Prompting]]