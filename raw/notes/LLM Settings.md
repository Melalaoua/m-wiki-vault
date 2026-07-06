tags:: #thelaboratory/AI 


En travaillant sur la confection de prompt, on interagit avec le LLM via une API (dans le cas d'OpenAI), ou directement avec le modèle. Dans les deux cas, on peut configurer les paramètres du LLM pour faire varier nos résultats.

- **Temperature** : Pour faire court, plus la température est basse, plus le LLM se déterministe dans un sens où le prochain token le plus probable sera choisis. 
  
  Faire monter la température mène à plus d'aléatoire, ce qui promeut des résultats plus diversifiés, plus créatifs. 
  
  On augmente le poids des autres tokens candidats.
  
  En terme d'application, il est préférable d'utiliser des températures plus basses pour des tâches factuelles comme du QA pour avoir des réponses concises et précises.


>Suite [[Basics of Prompting]]
>Prev [[Prompt Engineering]]