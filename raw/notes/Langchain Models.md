tags:: #thelaboratory/AI 


En provenance d'un tutoriel sur [[Langchain]]

Un modèle est un programme qui est entrainé pour réaliser des tâches spécifiques, entrainé sur un corpus de données. Cette page ne traitera pas la section sur comment entrainer un modèle, ca demande beaucoup de données, beaucoup de puissance de calcul, c'est encore inaccessible au grand publique.



### 1. LLM (Large Language Model).
---
Parlons des LLM, les LLM sont entrainé pour réaliser des tâches linguistiques comme la génération de texte (exemple :chatGPT). On observe une explosion du nombre de LLM cette année (2023), on va se focus sur le LLM de openAI : GPT.

On connaît actuellement 4 modèles openAI : Davinci, Ada, Babbage et Curie.

```python
from langchain.llms import OpenAI

llm = OpenAI(temperature = 1, openai_api_key = "")
prompt = ""
print(llm(prompt))
```

#### Estimer le nombre de tokens.
Comme c'est une API, on est taxé au nombre de mots ou "tokens", et les modèles ont un contexte, c'est-à-dire un nombre de tokens limité (8K, 16K, 32K, ...). Il est donc interessant de vérifier le nombre de tokens pour ses prompts.

```python
llm.get_num_tokens(prompt)
```


#### Streaming.
Le streaming est un concept majeur des LLM dans lequel on peut afficher l'output qui se construit en direct par le LLM (comme chatGPT).

```python
from langchain.llms import OpenAI
from langchain.callbacks.streaming_stdout import StreamingStdOutCallbackHandler

llm = OpenAi(temperature=1, streaming = True, callbacks = [StreamingStdOutCallbackHandler()], openai_api_key="")

resp =  llm(prompt)
```


### 2. Chat Models.
---
On va maintenant attaquer les modèles de chat, le fameux GPT3.5 entre dans cette catégorie, la différence majeure entre les modèles LLM qu'on a vu juste avant et les modèles de chats est :
- Ils sont beaucoup moins chers.
- Peuvent tenir des conversations comme si on avait une discussion avec un humain.

Vu que les modèles de chats peuvent tenir des conversation, il faut générer une liste de chat à intégrer dans notre entrée.

```python

from langchain.chat_models import ChatOpenAI
from langchain import PromptTemplate, LLMChain
from langchain.prompts.chat import (
				ChatPromptTemplate,
				SystemMessagePromptTemplate,
				AIMessagePromptTemplate,
				HumanMessagePromptTemplate
)

from langchain.schema import (
				AiMessage,
				HumanMessage,
				SystemMessage
)
```

Au lieu d'utiliser une classe OpenAi, on va utiliser la classe ChatOpenAI pour créer notre modèle de Chat.

```python
chat = ChatOpenAI(temperature = 0.5, openai_api_key="")
```

Les messages pour un modèle de chat sont classifier en trois catégories :
- **System message** : le prompt initial envoyé au modèle pour définir comment le modèle doit doit se comporter.
- **Human message** : l'input de l'utilisateur.
- **AI Message** : Réponse du modèle.

ChatGPT a besoin d'une liste de tout ces message pour être capable de comprendre le contenu et tenir la conversation.

Voici un exemple :
```python
messages = [
			SystemMessage(content = "You are a helpful assistant that paraphrases the sentence."),
			HumanMessage(content = "I love programming.")
]
chat(messages)
```


### 3. Templates pour les modèles de chat.
---
Nous avons discuté des [[Langchain Introduction|templates]] et en quoi ils nous permettent de générer des prompt dynamiques. Il est possible de faire la même avec les modèles de chat.

On définit un message système avec une variable dans notre input. On peut donc changer de manière dynamique la tâche

```python
template = "Tu es un assistant qui {task}"
system_message_prompt = SystemMessagePromptTemplate.from_template(template)

human_template = "{text}"
human_message_prompt = HumanMessagePromptTemplate.from_template(human_template)

chat_prompt = ChatPromptTemplate.from_messages([system_message_prompt, human_message_prompt])

chat(chat_prompt.format_prompt(task="paraphrases les messages", text="J'aime la bagarre").to_messages())
```

Tout comme la page d'introduction sur langchain, on peut aussi faire des inputs sequentiels.

```python
chain = LLMChain(llm=chat, prompt=chat_prompt)

chain.run(task="Paraphrases the sentence", text="I love programming.")
```


### 4. Streaming avec les modèles de chat.
---
On a vu juste avant l'utilité du streaming. Il est possible de faire la même chose avec les modèles de chat.

```python
from langchain.callbacks.streaming_stdout import StreamingStdOutCallbackHandler

chat = ChatOpenAi(streaming = True, callbacks = [StreamingStdOutCallbackHandler()] temperature = 0.5, openai_api_key="")

resp = chat([HumanMessage(content="Write me a poem on beauty.")])
```


### 5. Embedding Models.
---
Jusqu'à maintenant on a parlé de la génération de texte par les modèles. On va attaquer d'un sorte de modèles totalement différents. : les embeddings models.

#### Embeddings.
Premièrement, il faut comprendre ce qu'est un embedding. Un embedding est générallement associé à une pièce d'un texte qui représente un propriété de ce dernier.

Pour donner un exemple, considérons le mot "bon", "meilleur" et "mauvais". Si nous trouvons l'embeddings de ces mots, on observe que l'embedding de "bon" sera plus proche de "meilleur" tandis que l'embedding "mauvais" sera le plus lointain. La raison étant que l'embedding d'un mot a connaissance de la signification de ce dernier. Ainsi, les mots avec des signification proche auront des embeddings proches.


Les embeddings peuvent être interessant pour des opérations comme l'exemple suivant : Considérons E(x), l'embedding d'un mot x.

E(king) - E(male) + E(female) ~= E(queen)

La signification de cela est que si on soustrait l'embedding d'un mot, ici le mot male, au mot "King" et on y ajoute l'embedding du mot "female" on obtient l'embedding du mot "Queen". Comme les humains qui comprennent de manière intuitive que retirer le genre Homme et rajouter le genre Femme au mot Roi donne le mot Reine. Maintenant les machines peuvent le comprendre aussi.


#### Use-cases.
Maintenant que nous avons une idée de ce qu'est un embedding, la tâche d'un modèle d'embedding est de créer ces embeddings pour un texte donné. Un modèle qui génère des embedding peut mettre en évidence des propriétés comme nous l'avons fait juste avant.

Une fois que ces embeddings sont générés, on peut les utiliser pour réaliser des tâches de recherches sémantique similaire à des applications comme Chatbase, PDF.ai, SiteGPT. On peut créer des embeddings pour tout nos documents ou pages web et quand un utilisateur fait une requête, on peut rechercher les éléments pertinents à sa demande.

Voici un exemple : 
```python
from langchain.embeddings import OpenAIEmbeddings

embeddings = OpenAIEmbeddings(open_api_key="")
text = "This is dummy content."

doc_result = embeddings.embed_documents([text])
```

Comme on peut le voir, l'output du modèle est un vecteur qui est une représentation de notre text "This is a dummy content." Pour identifier deux phrases similaires, on peut calculer la distance entre les vecteurs. Si la distance est petite, alors nos mots sont similaires.

