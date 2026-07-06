tags:: #thelaboratory/AI 


### Basic Prompts.
---
On peut effectuer beaucoup de choses avec des prompts simples, mais la qualité de nos résultats dépends de l'information qu'on fournit à notre LLM, et la qualité des données.

Un prompt peut contenir l'information ou les instructions, la question, qu'on passe au model. Le prompt peut contenir des informations comme le contexte, l'inputs, des exemples. On peut utiliser ces informations pour donner des instructions au modèle et avoir des résultats meilleurs.

Un simple exemple :

*Prompt*
```
The sky is
```

*Output*
```
blue
The sky is blue on a clear day. On a cloudy day, the sky may be gray or white.
```

Comme on peut le voir, le LLM nous renvoie une suite de notre texte. L'output peut paraître inattendu, ou bien loin de ce qu'on attendait.

Cet exemple basique met en lumière la nécessité de donner du contexte, instructions, au modèle.

*Prompt*
```
Complete the sentence :
The sky is
```

*Output*
```
so beautiful today.
```

C'est un peu meilleur ? On a dit au modèle de compléter la phrase, donc le résultat semble plus cohérent à notre input. C'est démarche de confectionner des prompts de plus en plus optimisés pour diriger le modèle à effectuer une tâche, c'est du [[Prompt Engineering]]


### Prompt Formatting
---
On vient d'effectuer une prompt très simple juste avant. Un prompt standard suit le format suivant : 
``<Question> ?
ou 
`<Instruction>

On peut formatter ça en un format de QA (question answering), ce qui est standard dans un tas de datasets QA, comme suit :
```
Q: <Question> ?
A:
```

En réalisant des prompts comme ci-dessus, c'est du [[Zero-shot Prompting]], c'est-à-dire, qu'on dit directement au modèle qu'on attend une réponse, sans exemples ou démonstrations sur la tâche qu'on souhaite effectuer.

En partant de la technique qu'on vient de présenter, une autre technique existe, dénommée [[Few-shot Prompting]] qui consiste à donner quelques exemples comme suit :
```
<Question> ?
<Answer>
<Question> ?
<Answer>
<Question> ?
<Answer>
<Question> ?
<Answer>
<Question> ?
```

Le format du QA ressemblerait à quelque chose comme ça :
```
Q: <Question> ?
A: <Answer>
Q: <Question> ?
A: <Answer>
Q: <Question> ?
A: <Answer>
Q: <Question> ?
A: <Answer>
Q: <Question> ?
A: 
```

Garde à l'esprit qu'il n'est pas requis d'utiliser le format QA. Le format du prompt dépend de la tâche donnée. Par exemple, on peut réaliser une simple classification de la tâche et donner des exemple pour démontrer la tâche qui suit :

*Prompt*
```
This is awesome // Positive
This is bad! // Negative
Wow that movie was rad! // Positive
What a horrible show! //
```

*Output*
```
Negative
```

Le Few-shot prompting permet de mettre en contexte le modèle.


> Suite [[Prompt Elements]]
> Prev : [[LLM Settings]]