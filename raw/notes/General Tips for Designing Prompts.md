tags:: #thelaboratory/AI 


Voici quelques astuces à garder en tête lorsqu'on réalise nos prompts.

### Commence simple.
---
Quand tu te lance dans le designing de prompts, garde toujours en tête que c'est un processus itératif, qui requiert beaucoup d'expérimentation pour avoir les résultats optimaux. Utiliser des playground comme celui de OpenAI ou Cohere est un bon outil.

Tu peux partir d'une prompt simple et rajouter des éléments et du contexte pour obtenir de meilleurs résultats. Répéter l'opération plusieurs fois est vital pour cette raison. Mais tu vas voir certains exemples où la spécificité, la simplicité et être concis amène souvent à de meilleurs résultats.

Quand on a une tâche importante, impliquant beaucoup de sous-tâches, on peut les diviser en tâches simples et les incrémenter l'une après l'autre pour obtenir de meilleurs résultats. Ceci permet d'ajouter trop d'éléments et de complexité en une seule prompt.

### L'instruction.
---
On peut réaliser des prompts efficaces pour des tâches diverses en utilisant des ordres qui dis au modèle ce qu'on veut : "Ecris, Classifie, Résume, Traduits, Organise, etc..."

Garde en tête que tu as besoin d'expérimenter pour savoir ce qui marche le mieux. Essaie différents ordres, mots clés, contextes, données et regarde ce qui fonctionne le mieux pour ta tâche.

Habituellement, plus tu es spécifique et pertinent est le contexte avec la tâche, plus ce sera mieux. 

Certains recommandent de placer les instructions au debut du prompt, d'autres recommandent des séparateurs clairs comme ### pour séparer les instructions du contexte.

Par exemple : 

*Prompt*
```
### Instruction ###
Traduit le text ci-dessous en espagnol : 
Text : "Bonjour"
```

*Output* : 
```
¡Hola!
```


### Spécificité.
---
Soit très spécifique dans les instructions et les tâches que tu souhaites que ton modèle performe. Plus tu es descriptif et détaillé dans ton prompt, meilleur sera le résultat. C'est particulièrement important quand tu veux un résultat spécifique, ou un style de génération particulier. Il n'y a pas de tokens particulier ou de mots-clés qui donne à de meilleurs résultats. C'est plus important d'avoir des prompts bien descriptives et dans le bon format. En fait, donner des exemples dans le prompt est une manière très efficaces d'avoir le résultat voulu dans le format voulu.

Quand tu design des prompts, garde toujours en tête la longueur de la prompt, des API comme celle d'OpenAI limitent la longueur de la prompt, même de manière structurelle le modèle ne s'en sortira pas au bout d'un certain montant.

Pense à faire des prompts bien spécifiques et détaillées. Mais rajouter trop de détails inutiles n'est pas nécessairement une bonne approche. Les détails doivent être pertinent avec la tâche voulue. C'est quelque chose que tu vas devoir expérimenter beaucoup.

Prenons un exemple, essayons un prompt simple où on veut extraire des informations spécifiques à partir d'un texte donné : 

*Prompt*
```
Extract the name of places in the following text. 
Desired format:
Place: <comma_separated_list_of_company_names>
Input: "Although these developments are encouraging to researchers, much is still a mystery. “We often have a black box between the brain and the effect we see in the periphery,” says Henrique Veiga-Fernandes, a neuroimmunologist at the Champalimaud Centre for the Unknown in Lisbon. “If we want to use it in the therapeutic context, we actually need to understand the mechanism.""
```

*Output*
```
Place: Champalimaud Centre for the Unknown, Lisbon
```



### Evite les choses imprécises.
---
Avec les astuces que tu viens de recevoir sur le fait d'être détaillé, précis, etc.. c'est facile de tomber dans le piège de paraître trop détaillé dans les prompts que l'on génère, créant potentiellement des imprécisions, des impuretés. C'est parfois mieux d'être spécifique et direct. L'analogie ici est similaire à la communication efficace -- plus tu es direct, plus efficacement sera transmis le message.

Par exemple, imaginons que tu es intéressé par le prompt engineering et tu veux en savoir plus, 

*Prompt*
```
Explique le concepte de prompt engineering. L'explication doit rester courte, quelques phrases, et pas trop descriptive.
```

Le prompt ci-dessus ne précise pas combien de phrase, ni le style. Tu obtiendras quand même une réponse cohérente et bonne. Tu peux obtenir mieux avec des prompts plus précises 

*Prompt*
```
En 2-3 phrases, explique le compte de prompt engineering à une étudiant de lycée.
```


### To do or not to do ?
---
Une autre astuce communément donnée quand on en vient au prompt designing, c'est d'éviter de dire ce qu'il ne faut pas faire mais plutôt dire ce qu'il faut faire, ceci permet de mieux concentrer le modèle.

voici un exemple :

*Prompt*
```
The following is an agent that recommends movies to a customer. DO NOT ASK FOR INTERESTS. DO NOT ASK FOR PERSONAL INFORMATION.
Customer: Please recommend a movie based on my interests.
Agent: 
```

*Output*
```
Sure, I can recommend a movie based on your interests. What kind of movie would you like to watch? Do you prefer action, comedy, romance, or something else?
```


Mais voici une prompt mieux construite :
```
The following is an agent that recommends movies to a customer. The agent is responsible to recommend a movie from the top global trending movies. It should refrain from asking users for their preferences and avoid asking for personal information. If the agent doesn't have a movie to recommend, it should respond "Sorry, couldn't find a movie to recommend today.".
Customer: Please recommend a movie based on my interests.
Agent:
```

*Output*
```
Sorry, I don't have any information about your interests. However, here's a list of the top global trending movies right now: [list of movies]. I hope you find something you like!
```


> Suite [[Examples of Prompts]]
> Prev [[Prompt Elements]]