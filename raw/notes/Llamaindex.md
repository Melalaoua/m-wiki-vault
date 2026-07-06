tags:: #thelaboratory/AI 
source:: [1](https://github.com/SamurAIGPT/LlamaIndex-course)

ChatGPT est entrainé sur une quantité phénoménale de données, mais que faire si l'on souhaite entrainer ce dernier sur des données privées ? Il existe 3 moyens.
1. Entrainer un modèle open-source comme [Llama.cpp](https://github.com/ggerganov/llama.cpp)
2. Lui passer tout nos documents en entrée, on est limité niveau taille (contexte).
3. Passer seulement les données pertinentes au LLM

Llamaindex fonctionne en utilisant la 3e méthode, on va étudier comment avec l'aide d'exemples. 

### Entrainer chatGPT avec nos documents.
---
Voici un exemple de comment on peut entrainer chatGPT sur nos documents.

Nous allons utiliser llamaindex pour entrainer chatGPT sur nos données privées. Certains concepts mentionné ici comme VectorStoreIndex seront expliqué après.

On utilise un simple fichier pour lire nos données. Le lecteur de llamaindex peut lire des données depuis tout types de fichier et les convertir en format de fichier sur lequel on peut s'entrainer.


```python
from llama_index import VectorStoreIndex, SimpleDirectoryReader
import openai

openai.api_key = ""
documents = SimpleDirectoryReader('data').load_data()
index = VectorStoreIndex.from_documents(documents)
```

Maintenant nous allons créer une interface Llamaindex appelé "query engine" pour questionner nos documents. Encore une fois, sera expliqué ultérieurement. Avec cette interface, on peut questionner nos données en language naturel.

```python
query_engine = index.as_query_engine()
response = query_engine.query("What is NATO?")
print(response)
```