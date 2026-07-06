
tags:: #thelaboratory/AI 


Suite du tutoriel sur [[Llamaindex]]

Un llamaindex index est un type de données qui organise et stocke l'information (de diverses sources), la rendant plus facile à chercher. Un indexe est constitué de plusieurs nodes.

### Node.
Un node est l'unité structurelle de llamaindex. Un node n'est rien d'autre que des données sous un type spécifique, correspondant à une information.

A chaque qu'un document est fournit, on peut le diviser en plusieurs morceaux qui contiendront plusieurs nodes.


### Types d'index.
Llamaindex offre différents types de nodes que nous allons étudier maintenant.

#### List index.
List index stocke les nodes sous forme sequentielle, comme une liste de liste reliées. Par défaut, il prend les données en provenance de tout les nodes et les envoie sous forme de réponse.
![[Pasted image 20230709215550.png]]
Le list index offre différentes manières de "query" l'information, allant d'une requête(query) se basant sur les [[Langchain Models#Embeddings.|embeddings]] et qui récupère un top k des nodes correspondant, ou alors une addition de mots-clés agissant comme filtre.


#### Vector Store Index.
![[Pasted image 20230709215557.png]]
Le VSI stocke l'information de chaque node, correspondant à un embedding dans un vector store. Quand on cherche l'information dans notre index, il nous donne toujours un top k des plus similaires pertinents à notre demande.


#### Tree index.
![[Pasted image 20230709215608.png]]
Le tree index construit un arbre hiérarchique des nodes.

En interne, l'arbre est formé par un résumé de l'information. Il prend en entrée un document texte, construit l'arbre dans un style bottom-up où chaque node parent est le sommaire des nodes en dessous de lui.
![[Pasted image 20230709215622.png]]
Faire des requêtes à un tree index implique de partir du "Root node", jusqu'aux feuilles. Par défaut, (child_branch_factor = 1), un requête choisis un node enfant donné et un parent donné. Si on monte à child_branch_factor = 2, la requête choisis deux node-enfant par niveau.


#### Keyword Table Index.
Le GPTKeywordTableIndex implemente l'extraction de mots-clés depuis des nodes indexés, permettant de retrouver l'information pertinente à notre requête.

Quand on pose une question, on implémente en premier la génération de mots-clés issus de notre question. Ensuite, l'index cherche les documents pertinent et les envoie au LLM.

![[Pasted image 20230709215814.png]]


### Quand utiliser un index particulier ?

- **List index** : Le ListIndex est parfait quand on a pas beaucoup de documents, au lieu d'essayer de chercher l'information pertinente, l'index concatène tout les chunks et les envoies directement au LLM. Si nos données concaténées sont trop longues, l'index divise en différentes morceaux et demande au LLM de raffiner l'information.
  
  Quand on utilise le list index avec le paramètre embedding en True, c'est plus ou moins similaire au vectorstoreindex avec pour seule différence étant une liste d'index des nodes correspondant sans limite.
  
- **Vector index** : le vector index peut être utilisé si on veut récupérer que un certain nombre des meilleurs résultats les plus pertinents à notre requête, seul ceux dépassant un certain score sont sélectionnés.
  
- **Tree index** : seulement utile quand on fait des requêtes autour de la synthétisation.
  
- **Keyword Table Index** : Tout les nodes sont envoyés au LLM pour générer des mots-clés. Envoyer chaque document au LLM fait exploser les coûts de l'indexage. C'est plus lent et plus coûteux que les autres index. Ce n'est donc pas recommandé de l'utiliser sauf si on veut avoir des résultats plus qualitatifs. C'est le plus coûteux mais le plus puissant.