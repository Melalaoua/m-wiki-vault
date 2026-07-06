tags:: #thelaboratory/AI 
source:: [[Language Models are Few-Shot Learners]]

On a vu la capacité des LLMs a gérer le [[Zero-shot Prompting]], toutefois ils présentent certaines limites en zero-shot pour des taches plus complexes. Le Few-shot prompting peut être utilisé comme technique pour établir un contexte sur lequel le bot puet s'entrainer. On ajoute des démonstrations, des exemples, sur lequel notre bot va pouvoir utiliser pour se mettre en condition.

*Prompt*
```
A "whatpu" is a small, furry animal native to Tanzania. An example of a sentence that usesthe word whatpu is:
We were traveling in Africa and we saw these very cute whatpus.To do a "farduddle" means to jump up and down really fast. An example of a sentence that usesthe word farduddle is:
```

*Output*
```
When we won the game, we all started to farduddle in celebration.
```

On peut observer que le modèle a plus ou moins "appris" de l'exemple précédent pour effectuer la tâche donnée. Il a fallu d'un seul exemple c'est du "1-shot". Pour des tâches plus complexes, on peut augmenter le nombre d'exemples.

- L'espace entre le label et l'exemple sont très important
- Le format utilisé joue un rôle dans la performance du modèle, il est meilleur d'avoir des tags aléatoires plutôt que triés.
- 

*Prompt*
```
This is awesome! // Negative
This is bad! // Positive
Wow that movie was rad! // Positive
What a horrible show! //
```

*Output* 
```
Negative
```

On voit bien que la réponse est bonne alors que nos labels sont aléatoires (negatif - positif - positif)

Limitations sur les tâches plus complexe nécessitant du raisonnement.


> Suite [[Chain-of-Thought Prompting]]
> Prev [[Prompt Techniques]]