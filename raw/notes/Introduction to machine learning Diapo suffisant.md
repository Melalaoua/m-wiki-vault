---
Date : October 6, 2022 10:30 AM
---

up:: [[ImmunoHD]]
tags:: #academia/master, #master/ImmunologieHD



# 1. Machine learning general concepts.

L’IA c’est le mot global qui va rergrouper tout les plans d’apprentissage, à l’intérieur on retrouve le machine learning qui est l’ensemble des techniques qui permettent à un ordianteur d’apprendre des données via un algorithme qui va créer des models.

Deep learning : réseaux de neurones.

Le modèle va être capable de créer des prédictions à partir de données.

POurquoi le ML est important ?

C’est devenu omnipréscent en science ou dans la vie de tout les jours. 

Deux avantages : fonctionne assez bien,  économise beaucoup de temps sur le long terme.

Plusieurs catégories de machines learning:

Trois grandes 

Supervisé, non-supervisé et par renforcement.

La plupart du temps on voit le supervisé. Les données + le bon diagnostic.

Le non supervisé : essayer de trouver des groupes en réalisant du clustering. Pas de label, diagnostic, juste réaliser des groupes et points de données smilaire.

Par renforcement : tout les systèmes interactifs et séquentiels (exemple : jouer aux echecs). 

### Apprentissage supervisé : sous-catéogire.

Classification : on prédit une classe (image de chien ou de chat, patient en bonne santé ou non). Le but final est de faire la différence entre un nombre n de classes.

Regression : prédire une valeur (la durée de vie, rythme cardiaque, …).

### Training, Testing, Predicting.

La construction d’un modèle d’intelligence artificelle et 

D’abord l’entrainement de notre modèle : on a nos données brut, qu’on va séparer en deux groupes. On utilise les 80% pour entrainer l’agorithme qui va produire un modèle qu’on devra vérifier.

Après l’entrainement on évalue les performance (metrics) sur le jeu de test des 20% utilisés pendnat l’entrainement (qu’il n’a pas vu auparavant). si les métriques sont bonne, on garde le modele pour prédire des futures données.

Deux métriques très simples : 

- Matrice de confusion : simple matrice ou en X on met le vrai label (le vrai diagnostiqueà et en Y la classe prédite.
- Calculating accuracy : quelle est la proportion de bonne précision ?

### Classic ML (shallow) and Deep-learning.

Ces deux méthodes sont plutôt différentes avec des applications bien distinctes.

## 2. Data are te most important part of ML.

Qu’est ce qu’on appelle des données ?

Ca peut prendre plusieurs formes. On va avoir des données bruts, chaque colonnes correspondant à des observations et aussi un diagnostique associé à cette personne.. On peut avoir des données plus bruts comme des textes, des images, des sons.

### Scikit-learn decision map.

Librairie python qui permet de faire du machine learning.

### Features and labels.

Définition assez précise en ML

Ce qu’on appelle features : X1 à XN des ritères que l’on va utiliser pour faire l’entrainement.

Label : le diagnostique associé

L’intélligence artificelle ne raisonne pas avec du texte, mais uniquement avec des nombres. Uniquement des stats, dérivés et calculs. Pour fonctionner un algorithme a besoin de petits nombres (entre -1 et 1) et il faudra convertir nos features en nombres.

On réalise de l’encoding. L’ordinal encoding : on remplace juste chacun des labels par 0 ou 1. One hote encoding, on transforme nos valeurs dans un vecteur de 0 et de 1.

Il faudra traiter les données numériques pour les réechelonner autour de 0. L’idée est de faire une distribution autour de la gaussienne (normalisation).

## Classic machine learning models.

Pour les modèles classiques, à quoi ils servent ? Forces ? utilitiés ?

Variété d’algorithme qui fonctionne très bien pour les données tabuluées demendant très peu de données

Peuvent traiter des images, mais être capable de représenter nos données sous la forme d’un tableau.

Différence avec le Deep learning au niveau des perf ?

 

### Decision tress, random forest, boosting methods.

Arbre de décision , base des algorithmes

### Hyper-paramètres.

Comment je sais cobien d’arbre j’ai besoin pour ma tache : c’est ce qu’on appelle un hyper-paramètres.

Une limite du nombre d’arbres, de largeurs, de profondeurs. Trouver les meilleurs paramètres : tuning d’hyperparamtères.

Chercher le set de paramètre qui produit le modèle avec les meilleures performances.

## IV. Neural networks and deep-learning.

![bubble-chat.png](Pro/Scholar/no01.%20Notes/01%20S1/English/ImmunoHD/20221006%20Introduction%20to%20machine%20learning/Introduction%20to%20machine%20learning%20Diapo%20suffisant%2098df077f02b9466e8c2b14c27de3ad4f/bubble-chat.png)

$\Large\texttt{Commentaires}$

---

---

$\Large\texttt{Fin de page}$