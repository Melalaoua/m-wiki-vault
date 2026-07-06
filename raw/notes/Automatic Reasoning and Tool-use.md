tags:: #thelaboratory/AI 

Combinaison du [[Chain-of-Thought Prompting]] avec l'utilisation d'outils est une manière d'adopter une approche forte et robuste et permettre aux LLMs d'effectuer beaucoup de tâches. 
[Paranjape et al., (2023)](https://arxiv.org/abs/2303.09014)proposent un framework qui utilise les LLM gelés et générer automatiquement des étapes intermédiaires de raisonnement comme programme.

ART fonctionne ainsi : 
- Pour une tâche donnée, sélection de raisonnement à plusieurs étapes et utilisation d'outils depuis une librairie.
- Au moment du test, la génération s'arrête à chaque fois qu'un outil est invoqué, l'output de cet outil est intégré à l'output et la génération reprend.


ART encourage le modèle à décomposer les tâches et à utiliser des outils appropriés, dans un style zéro-shot.

Additionnellement, ART peut s'étendre aux humains pour corriger les erreurs de raisonnement et aussi pour ajouter de nouveaux outils en mettant ajour à les tâches ou la librairie. Le processus est démontré ci-dessous.

![[Pasted image 20230714121043.png]]

ART est meilleur que le [[Few-shot Prompting]] ou le [[Chain-of-Thought Prompting]] au benchmarks BigBench et MMLU. Il dépasse les performance des programmes CoT fait à la main quand le feedback humain est prit en compte.

Ci-dessous un tableau démontrant les performance du ART au benchmark.
![[Pasted image 20230714121315.png]]


> Suiv [[Automatic Prompt Engineer]]
> Prev [[Retrieval Augmented Generation]]