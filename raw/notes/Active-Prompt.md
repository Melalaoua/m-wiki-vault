tags:: #thelaboratory/AI 


Les méthodes de [[Chain-of-Thought Prompting]] dépendent uniquement sur un set d'exemples annotés par les humains. Le problème est que ces exemples ne sont pas uniformément efficaces pour différentes tâches. Afin de résoudre cela, [Diao et al., (2023)](https://arxiv.org/pdf/2302.12246.pdf) on récemment proposé une nouvelle approche de prompting appelé Active-Prompt afin d'adapter les LLMs aux différents examples spécifiques à des tâches (annotés par des humains dans un style [[Chain-of-Thought Prompting]])

Ci-dessous une illustration de l'approche. La première étape est de questionner le LLM avec ou sans des exemples en CoT. Un ensemble k de réponses sont générées en accord avec le set de questions juste avant. 

Une métrique d'incertitude est calculée basée sur les k réponses. La plus incertaines des question est sélectionnée pour annotation par un humain. Les nouveaux exemples sont ensuites utilisés par la suite.

![[Pasted image 20230714123125.png]]


> Suiv [[Directional Stimulus Prompting]]
> Prev [[Automatic Prompt Engineer]]