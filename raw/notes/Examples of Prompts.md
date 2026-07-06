tags::  #thelaboratory/AI 

La section précédente permettait d'introduire des examples basiques de prompts.

Ici on va donner plus d'exemples, comment utiliser les prompts pour différentes tâches et introduire des concepts clés tout du long.

Parfois, la meilleure manière d'apprendre un concept, c'est au travers d'exemples. Les exemples qui suivent illustrent comme bien utiliser des prompts bien construits pour différentes tâches.

### Résumé de textes.
---
Une tâche populaire attribuée aux LLMs comme chatGPT. On retrouve les résumés de texte dans beaucoup de domaines. Les LLMs sont prometteurs pour cette tâche, nous renvoyer que les informations importantes et nécessaires.

Dans l'exemple qui suit, on est intéressé par les antibiotiques :

*Prompt*
```
Explain antibiotics 
A:
```

*Output* :
```
Antibiotics are a type of medication used to treat bacterial infections. They work by either killing the bacteria or preventing them from reproducing, allowing the body’s immune system to fight off the infection. Antibiotics are usually taken orally in the form of pills, capsules, or liquid solutions, or sometimes administered intravenously. They are not effective against viral infections, and using them inappropriately can lead to antibiotic resistance.
```

Le "A:" est un format explicite dans une prompt. On l'utilise pour dire au model qu'on attends une réponse. Ce n'est pas très clair pourquoi c'est utile, mais on va le détailler dans d'autres exemples.

On peut reprendre notre prompt précédent pour avoir une résumé en une phrase

*Prompt*
```
Antibiotics are a type of medication used to treat bacterial infections. They work by either killing the bacteria or preventing them from reproducing, allowing the body’s immune system to fight off the infection. Antibiotics are usually taken orally in the form of pills, capsules, or liquid solutions, or sometimes administered intravenously. They are not effective against viral infections, and using them inappropriately can lead to antibiotic resistance.Explain the above in one sentence:
```

*Output*:
```
Antibiotics are medications used to treat bacterial infections by either killing the bacteria or stopping them from reproducing, but they are not effective against viruses and overuse can lead to antibiotic resistance.
```


Voir la suite  de la page : https://www.promptingguide.ai/introduction/examples


>Suite [[Prompt Techniques]]
>Prev [[General Tips for Designing Prompts]]