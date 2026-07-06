tags:: #thelaboratory/AI
source:: [[A Gentle Introduction to Graph Neural Networks]]

Les graphiques sont tout autour de nous, les objets réels sont souvent définis par leur interaction avec leur environnement, ou d'autres objets. Il est possible de représenter facilement cette visualisation par un graph.

Des chercheurs ont développé des réseaux de neuronnes se reposant sur des données en graph : ce sont les ==GNN ou graph neural networks==, on commence à les utiliser de plus en plus dans la recherche d'antibiotiques, physiques, détection des fake news, prédiction trafic, système de recommandation.



### I. Quelles genre de données sont mises en grpahique ?
---
Un graphe est une répresentation de relations (==edges==) entre les individus d'une collection (==nodes==).
![[Pasted image 20230403190225.png]]

Des informations peuvent être stockées dans les edges, ou les nodes. Et une relation (edge) peut avoir une direction, ou non.

Les graphes sont des structures très flexibles.



#### A. Relations homogènes.
Ce sont des outils très puissant pour représenter nos données. Et ils peuvent être utilisés pour représenter une vaste gamme de types de données.

##### 1. Images sous forme de graphes.
On imagine une image typiquement sous la forme d'un rectangle sur laquelle sont déposés des pixels pour former un tableau de pixels. On peut representer ce tableau.

![[Pasted image 20230403190843.png]]


##### 2. Textes sous formes de graphes.
Un texte peut être digitalisé en associant des indices à chaque lettre, mot ou indice, et représenter la séquence de ces indices. Ce qui créer un graph simple dirigé, où chaque indice ou lettre est un noeud relié par un edge.
![[Pasted image 20230403191052.png]]



#### B.Relations hétérogènes.

Les graphes sont des outils très utiles pour représenter des données hétérogènes. Dans les exemples qui vont suivre, le nombre de voisins à chaque noeud est variable (à l'inverse d'une image ou d'un texte). Ce genre de donnée sont très dur à représenter d'une autre manière que via un graphe.

###### <u>Molécules sous forme de graphes.</u>
Les molécules sont les briques fondamentales de la matière, constitués d'atomes dans un espace en 3 dimensions. Tout les particules interagissent entre-elles, mais quand une paire d'atome sont liées, elle forme une connection covalente, de différent types, de différentes tailles. C'est donc très intéressant de représenter ça sous forme de graphe.

![[Pasted image 20230403191606.png]]
![[Pasted image 20230403191557.png]]


###### <u>Social network.</u>
Les social networks sont des outils très puissant pour étudier des patternes comportementaux de personnes, institutions ou organisations. Un graph peut être utilisé pour représenter, au sein d'un groupe, les relations entre chaque.
![[Pasted image 20230403191856.png]]



### II. Qu'apportent de plus les graphiques ?



### III. Construire un GNN moderne.



### IV. Quelques exemples.