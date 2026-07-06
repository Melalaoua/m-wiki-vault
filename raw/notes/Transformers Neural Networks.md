tags:: #thelaboratory/AI 
source:: [1](https://builtin.com/artificial-intelligence/transformer-neural-network), [2](https://jalammar.github.io/visualizing-neural-machine-translation-mechanics-of-seq2seq-models-with-attention/), [3](https://www.youtube.com/watch?v=4Bdc55j80l8), [4](https://prasad-jayanti.medium.com/what-is-query-key-value-qkv-attention-3b8f9eb15124)
additional:: [[how_to_work_with_large_language_models]]

Les transformers est une architecture de neurone initialement proposée dans un papier célèbre de google : [Attention is all you need](https://arxiv.org/abs/1706.03762)

Les transformers visent à résoudre le problèmes des tâches séquence-à-séquence tout en pouvant gérer des dépendances à longue distance entre les mots.


## RNN.
--
Pour comprendre les transformers, il faut comprendre les RNN
Quelle est la différence des RNN (recurrence neural networks) par rapport aux ANN (artificial neural network).
![[Pasted image 20230626135030.png]]

Les RNNs sont des feed-forward neural networks qui se "déroulent". Ils sont conçus pour prendre en entrée des séries d'entrées sans limites sur la taille de la séquence (exemple : un texte). On parle de série parce que ca sous-entend que les éléments de la séries ont un lien avec leurs voisins.

![[Pasted image 20230626135035.png]]

Mais, les feed forward "retiennent" aussi l'information lors du training ? Oui, c'est le cas pour les RNNs aussi, mais les RNNs retiennent aussi les output des inputs précédents.
![[Pasted image 20230626135138.png]]


#### Modèles RNN.
Les RNNs peuvent utilisés dans divers types de  modèles :
- Les **Vector-sequence models** : prennent en entrée un vecteur fixe et produisent un vecteur de n'importe quelle taille - *exemple : prends en entrée une image et en sort une description.*
- Les **Sequence-vector Model**s: prennent en entrée un vecteur de n'importe quelle taille et en produisent un vecteur d'une taille fixe - *exemple : sentiment analysis of a movie rates the review of any movie, positive or negative, as a fixed size vector.*
- Les **Sequence-to-Sequence Models** : Le plus populaire et les plus utilisés, prennent une séquence en entrée et produisent une autre séquence de taille variable - *exemple : traduction de textes* 

#### Désavantages.
1. Lents à entrainer.
2. Les longues séquences ont tendance à avoir un "gradient d'oubli" qui fait que pour des séquences très larges le modèle aura tendance à "oublier" ses premiers inputs


L'article parle aussi des LTSM (long short-term memomry neurons) mais je le traite pas ici.

Donc les LTSM et les RNN ont deux gros problèmes : vanishing gradient, slow training.

### Seq-to-Seq.
--
Un modèle seq2seq est, comme dit juste au dessus, un modèle qui prends en entrée une séquence de taille variable pour sortir une séquence de taille variable elle aussi.

Les S2S sont constitués d'un **encodeur** et un **décodeur**.
>L'encoder prend chaque éléments de la séquence d'entrée, compile l'information et la capture dans un vecteur (appelé le **contexte**). Après avoir process l'information de la séquence d'entrée <u>en entière</u>, l'encodeur envoie le contexte au décodeur qui va commencer à produire la séquence de sortie, item par item.

Le contexte est un vecteur (un liste de nombre, en gros) dans le cas de la traduction. L'encoder et le décodeur sont en général des réseaux de neurones.

La taille du contexte peut être déterminée lorsque l'on configure le modèle. C'est typiquement le nombre d'unités cachées dans l'encodeur qui est un RNN.

Les RNN prennent deux entrées à chaque étape : l'hidden state et le l'entrée (dans le cas d'un traducteur : le mot).

A chaque étape de l'encodeur, un nouvel hidden stade est généré, avec un output vector. Le dernier hidden state est transmis au décodeur qui produire l'output.




### Résoudre le problème de vanishing gradient
--
Imaginons que je te donne un livre sur la biologie et je veux que tu me donne une explication sur la voie des RAS, deux choix s'offrent à toi :
- Soit tu le livre en entier et tu fais ton explication.
- Soit tu regardes l'index du livre et tu vas directement étudier la partie sur les RAS.

Quel est le plus efficace ? La seconde méthode. De plus, l'explication à l'issue de la première méthode sera trop vague, généraliste, avec trop d'informations tandis que la seconde sera précise.

C'est comme ça que fonctionne le système d'attention des transformers, un peu comme les humains, ils savent sur quoi se concentrer.

*Je pense qu'un entre deux serait utile ici, bien que se focus directement sur le sujet est plus efficace, avoir des notions globales sur la biologie permettrait de mieux comprendre la voie des RAS par exemple, mais ce n'est pas le sujet.*


### Transformers.
--
Une des nouveautés dans les transformers est que l'entrée peut être passée en parallèle, permettant au GPU de mieux optimiser sa puissance et de fait une vitesse de training accrue.
On découvre aussi les "multi-headed attention layer" permettant de résoudre le problème de vanishing gradient.

Dans les RNN, on doit passer une mot après l'autre dans le séquence de manière continue. Dans les transformers tout les mots peuvent être passés en même temps.

![[Pasted image 20230627075931.png]]


#### L'encoder.
Les ordinateurs ne comprennent pas les mots, images, ... ils comprennent plutôt les nombres, vecteurs, matrices, la première étape est donc la conversion de mot à vecteur. Comment est-ce possible ?

##### Embedding Space
Un dictionnaire de chaque mot d'une langue où les mots avec des significations similaires sont regroupés. Chaque mot, en fonction de sa signification, est cartographié et assigné à une valeur particulière.

Toutefois, des mots peuvent avoir des significations différentes en fonction de leur position dans la phrase, c'està  ca que sert le positional encoding.

On va maintenant attaquer la partie essentielle des encoders : self-attention.

##### Multi-headed Attention.
La notion de self-attention réfère à la capacité de déterminer la pertinence d'un mot par rapport aux autres mots et de générer des vecteurs d'attention (vector attention). Pour chaque mot, on peut générer un vecteur d'attention qui capture le contexte de la relation entre chaque mot d'une séquence.

##### Feed Forward.
Une réseau de neurones classique est appliqué à chaque vecteur d'attention afin de le transformer en un vecteur qui est acceptable pour la partie décodeur.

#### Decoder.
Même chose au début : embedding space et positional encoding.

##### Masked multi-head attention.
