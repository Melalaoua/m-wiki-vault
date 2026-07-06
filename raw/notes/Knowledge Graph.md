tags:: #thelaboratory/data 
source:: [1](https://www.ibm.com/topics/knowledge-graph?source=post_page-----110844f22a1a--------------------------------)[2](https://towardsdatascience.com/why-you-need-a-knowledgegraph-and-how-to-build-it-ac4f35cb75b7) [3](https://www.youtube.com/watch?v=y7sXDpffzQQ),[4](https://www.ontotext.com/knowledgehub/fundamentals/what-is-a-knowledge-graph/)

A knowledge graph, also known as a semantic network, represents a network of real-world entities—i.e. objects, events, situations, or concepts—and illustrates the relationship between them. This information is usually stored in a graph database and visualized as a graph structure, prompting the term knowledge “graph.”

A knowledge graph is made up of three main components: nodes, edges, and labels. Any object, place, or person can be a node. An edge defines the relationship between the nodes. For example, a node could be a client, like IBM, and an agency like, Ogilvy. An edge would be categorize the relationship as a customer relationship between IBM and Ogilvy.

A represents the subject, B represents the predicate, C represents the object

It is also worth noting that the definitions of knowledge graphs vary and there is [research](https://ceur-ws.org/Vol-1695/paper4.pdf) (link resides outside of ibm.com), which suggests that a knowledge graph is no different than a knowledge base or an ontology. Instead, it argues that the term was popularized by the Google’s Knowledge Graph in 2012.

**TLDR: A knowledge graph organizes events, people, resources, and documents in a graph database for advanced analysis. This article will explain the purpose of a knowledge graph and show you the basics of how to translate a relational data model into a graph model, load the data into a graph database, and write some sample graph queries.**

Un knowledge graph est une sorte de base dedonnées en graphe, construite pour gérer un réseau de processus et d'entités. Les noeuds représentent les personnes, évenements, lieux, ressources, docuements. Les relation entre les noeuds sont stockés dans des vertice. Les relations sont stockés dans la base de données avec un nom et une direction.

Tout les databse en graphe ne sont pas des KG. Pour être considéré comme un KG, le design doit impliquer la modèle semantique de l'entreprise. You are in essence creating a **seamless web** out of all parts of the business that interact, and using the business semantics to closely tie data to the processes they represent. This can serve as the **foundation for future generative LLM model** use.

To illustrate a diverse set of data in a knowledge graph, let’s look at a simple example for supply chain logistics. The business process might be modeled like this:

![[Pasted image 20231213111508.png]]


### Pourquoi un knowledge Graphe ?
Les bases de données relationnelles sont utiles pour créer des listes, mais performent moins pour les réseaux de diverses entités. Un exemple de tâches qu'une base de données relationnelles ne sera pas bonne pour :
- Analyser les interactions d'un patient avec des dizaines de personnes, lieux, et subit multiples procédures pour être soigné.
- Trouver des patternes dans les fraudes financières entre un vendeur en ligne, un client et les transactions incluses.
- Optimiser les dépendences et interconnections entre les élements d'une supply chain.

Ci-dessus figurent des exemples de **réseaux** de personnes, évènements, ressources. C'est très complexe d'aller retrouver cette interconnexion dans une base de données relationnelles, cela implique multiples INNER JOIN.

De plus, plus la requête implique de données, plus elle sera lente (exponentiel), tandis que les bases de données en graphe on une relation linéaire en fonction de la quantité de données. *==In the future, we should expect to see enterprise data groups adopting a combination of== ==**relational databases for isolated analysis**== ==on one business function, and== ==**knowledge graphs for complex, networked processes**== ==that span functions.==*


Un Knowledge Graph est une sorte de base de données en graphe, ils sont construits pour pouvoir gérer une diversité de réseaux d'entités et de processus. 

![[Pasted image 20231222152510.png]]

Les KG (knowledge graph) reposent sur un modèle knowledge : une collection de descriptions interconnectées de concepts, entités, relations, évenements où:

- Les descriptions ont une sémantiques définies qui permet à la fois aux programmes et aux humains de la comprendre sans ambuiguïtés. 
- Les descriptions s'interconnectent, formant un réseau.
- Divers types de données sont interconnectés et décris par une sémantique en accord avec le KM (knowledge model).

#### Caractéristiques clés.
Les KG combinent les caractéristiques de plusieurs paradigmes en data :
- Database : car la donnée peut être queried par des requêtes structurées.
- Graph : car la donnée peut être analysée sous la forme d'un réseau structuré.
- Knowledge base, car le KG supporte une sémantique définie, qui peut être utilisée pour étudier les données, et rajouter des données.

Les KG sont écris au format [[RDF]], donnant le meilleur framework pour intégrer les données, les unifier et les relier pour réutilisation :
- **Expressivity**: The standards in the Semantic Web stack – RDF(S) and OWL – allow for a fluent representation of various types of data and content: data schema, taxonomies and vocabularies, all sorts of [metadata](https://www.ontotext.com/knowledgehub/fundamentals/metadata-fundamental/), reference and master data. The [RDF*](http://graphdb.ontotext.com/documentation/9.2/free/devhub/rdf-sparql-star.html) extension makes it easy to model provenance and other structured metadata.

- **Performance**: All the specifications have been thought out, and proven in practice, to allow for efficient management of graphs of  billions of facts and properties.

- **Interoperability**: There is a range of specifications for data serialization, access (SPARQL Protocol for end-points), management (SPARQL Graph Store) and federation. The use of globally unique identifiers facilitates data integration and publishing.

- **Standardization**: All the above is standardized through the W3C community process, to make sure that the requirements of different actors are satisfied – all the way from logicians to enterprise data management professionals and system operations teams.