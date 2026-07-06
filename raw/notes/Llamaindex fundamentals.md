tags:: #thelaboratory/AI 

Suite du tutoriel sur [[Llamaindex]]

Dans cette page, nous allons discuter des fondamentaux de Llamindex et ses composants principaux. On abordera le sujet ainsi :
1. Nodes
2. Document loaders.
3. Indexes.
4. Retrievers.
5. Query Engines.


### 1. Nodes.
---
Les nodes sont l'unité fondamentale de Llamaindex. Un node est rien de plus qu'un type de donnée qui contient plusieurs bouts de texte. 

A chaque fois qu'un document est fournit, on peut le diviser en multiples morceaux et les stocker dans des nodes.

### 2. Document Loader.
---
Les documents loader de Llamaindex sont une interface pour extraire les données d'une source. La source peut être une page web, une vidéo youtube, un pdf, etc... Llamaindex supporte un tas de types de documents et on va en étudier certains pour comprendre.

### 3. Indexes.
---
Un index, dans llamindex, est un type de données qui s'organise et stocke l'information en provenance des multiples sources, les rendant plus facile à retrouver, stocker. Un indexe est constitué d'un tas de nodes.

Llamaindex offre une variété d'indices qui seront étudié dans ce cours.

### 4. Retrievers.
---
Un retriever, dans llamaindex, aide à récupérer un set de nodes basé à partir d'un certaine requête. C'est comme un outil qui cherche les informations pertinentes lors de nos requêtes parmis un large dataset. Il en existe une variété.

### 5. Query Engines.
---
Un query engines est un processus qui prend en charge les demandes de l'utilisateur, interagit avec les données (comme les indexes), et renvoie une réponse synthétisée.

LLamaindex offre une variété.

### 6. Exemple.
---
```python
!wget https://raw.githubusercontent.com/hwchase17/chat-your-data/master/state_of_the_union.txt

!mkdir data

!mv state_of_the_union.txt data/
```


On utilisera SimpleDirectoryReader

```python
from llama_index import SimpleDirectoryReader

documents = SimpleDirectoryReader('./data').load_data()

```

On divise nos données en différents nodes.
```python
from llama_index.node_parser import SimpleNodeParser
parser = SimpleNodeParser()
nodes = parser.get_nodes_from_documents(documents)
```


On créer un index
```python
from llama_index import LLMPredictor, VectorStoreIndex
from langchain import OpenAI
os.environ["OPENAI_API_KEY"] = ""

index = VectoreStoreIndex(nodes)
```

On créé un retriever : on utilisera le vectorindexretriever qui récupère un top k (k arbitraire) de ceux qui correspondent à notre recherche dans le document, prenons pour exemple k =2
```python
from llama_index.retrievers import VectorIndexRetriever

retriever = VectorIndexRetriever(
				index = index,
				similarity_top_k = 2
)
```


Crééons une query engine : on peut construire cette engine au dessus de notre retriever et commencer à faire des requêtes.

```python
from llama_index.query_engine import RetrieverQueryEngine

query_engine = RetrieverQueryEngine(
					retriever=retriever
)

```


On peut faire nos requêtes

```python
response = query_engine.query("What did the author do growing up ?")
```