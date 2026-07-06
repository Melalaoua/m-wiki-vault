source:: [Jay Alammar](https://jalammar.github.io/illustrated-transformer/)
tags:: #AI/architecture 

Cette note fait écho à mes récentes recherches sur les [[Transformers Neural Networks]]. De fait beaucoup de ce qui sera écrit ici peut être une répétition de cette note adjacente.

L'architecture Transformers a été présentée dans le papier [[Attention is All You Need]]. Il est possible d'intégrer cette application dans le package [Tensor2Tensor](https://github.com/tensorflow/tensor2tensor), ou par [PyTorch](http://nlp.seas.harvard.edu/2018/04/03/attention.html)

Deux composants principaux constituent l'architecture transformers : La partie Encoder et la partie Decoder

![[The_transformer_encoders_decoders.png]]
![[The_transformer_encoder_decoder_stack.png]]


Les différents encodeurs constituant la partie encoder ont tous une structure identiques, mais des poids différents. Chaque encoder est subdivisé en 2 sous-couches.
![[Transformer_encoder.png]]

Les données entrantes rencontrent tout d'abord la couche de "Self-Attention" permettant à l'encoder de regarder chaque mot qui constitue la séquence d'entrée lorsque ce dernier essaie d'encoder un seul mot spécifique. Il regarde TOUT les mots de l'entrée pour UN SEUL mot de cette même entrée. 

Ce qui sort de la couche de self-attention est directement implémenté dans une couche de neurones Feed-Forward pour <u>chaque</u> token de l'input.

La partie decoder possède 2 couches identiques à celle décrite ci-dessus. 

![[Transformer_decoder.png]]


La plus basse  couche des encoders possède un composant permettant de faire l'embeddings des mots. Chaque encoder recoit des vecteurs de taille 512, soit en provenance de l'embedding module (pour l'encoder le plus bas) soit de l'encoder précédant.

Chaque vecteur est envoyé dans la couche de self-attention puis dans le FFN pour envoyer son output dans l'encoder  suivant. Ci-dessous l'exemple pour l'encoder le plus bas dans la hiérarchie.
![[encoder_with_tensors_2.png]]


### Self-Attention.

Prenons la phrase suivante  comme input : "The animal didn't cross the street because it was too tired"

A quoi réfère "it" ? Lorsque le modèle process ce mot, le mécanisme de self-attention lui permet d'associer ce mot à "animal".

Lorsque le modèle process chaque token (1 token est presque égal à 1 mot), self-attention permet à ce dernier de regarder chaque autre token dans l'input afin d'avoir des indices lui permettant d'effectuer un meilleur encoding de ce mot.

![[transformer_self-attention_visualization.png]]


<u>Première étape</u> dans le calcul de la self-attention, pour chaque mot, 3 vecteurs sont générés : ==Query vector, Key vector et Value vector==

![[transformer_self_attention_vectors.png]]
Chacun de dimension 64 (l'embedding a une dimension de 512). Ces trois vecteurs sont obtenus en multipliant l'embedding vector par 3 matrices entrainées durant le training du modèle.

Query, Key et Value vectors sont des abstractions utiles lorsqu'il en vient de calculer l'attention. (expliqué par la suite)

La <u>seconde étape</u> dans le calcul de la self-attention, consiste à calculer la un score. Pour chaque mot, ce score est calculé, prenons pour exemple le mot "Thinking", il est nécessaire d'effectuer le score de chaque mot de la séquence d'entrée contre ce même mot. The score determines how much focus to place on other parts of the input sentence as we encode a word at a certain position.

On multiplie le query vector du mot contre le key vector de chaque mot (lui-même inclu, voir ci dessous).
![[transformer_self_attention_score.png]]

La <u>troisième</u> et <u>quatrième étape</u> consiste à diviser le score par 8 (racine carré de 64)  puis un softmax (normalise le score pour qu'ils soient tous positif et la somme de tous fait 1)

![[self-attention_softmax.png]]

La <u>cinquième étape</u> est de multiplier chaque value vector (bleu) par le softmax score afin de garder "intact" les valeurs des mots sur lesquels nous voulons nous concentrer, et éliminer les mots non pertinents.

La <u>sixième étape</u> est d'additionner ces vecteurs, donnant l'output de la couche de self-attention à cette position, pour ce mot (token)  

![[self-attention-output.png]]

On a vu comment la self-attention était calculée pour un seul vecteur, toutefois, dans les transformers, ce calcul est fait en matrice (plus rapide).

![[self-attention-matrix-calculation.png]]

Vu qu'on effectue le calcul sous forme de matrices, on peut fusionner l'étape 2 à 6 en une seule formule afin d'avoir la matrice de self-attention.

![[self-attention-matrix-calculation-2.png]]


### The Beast With Many Heads.
Le papier [[Attention is All You Need]] a rafiné le module de self-attention en ajoutant un mécanisme "multi-headed" attention, améliorant les performance de l'attention de deux manières :

1. Permet d'étendre l'habilité du modèle à se concentrer sur différentes positions en même temps.
2. La mise en place de multiples sous-espaces de représentations. 

![[transformer_attention_heads_qkv.png]]
![[transformer_attention_heads_z.png]]

Il faut condenser ces multiples matrices de self attention de la même matrice d'embeddings en une seule. Les matrices Z sont concaténées et multipliée par une seule matrice.
![[transformer_attention_heads_weight_matrix_o.png]]

Ci-dessous un résumé de ce qu'ont vient de dire.
![[transformer_multi-headed_self-attention-recap.png]]


### Representing The Order of The Sequence Using Positional Encoding

Le transformer rajoute un vecteur à chaque input embedding, suivant un patterne spécifique que le modèle comprend, l'aidant à déterminer la position de chaque token, ou la distance entre différents mots dans une séquence. 

![[transformer_positional_encoding_vectors.png]]
Voir l'article pour comprendre les positional embeddings.

### Résidus
Chaque sous-couche des encoders (slef-attention, ffnn) a une connection résiduelle autour d'elle, suivit par une étape de normalization.
![[transformer_resideual_layer_norm_2.png]]

Cette connection résiduelle s'applique aussi aux decoders.
![[transformer_resideual_layer_norm_3.png]]


### Le Decoder
L'encoder commence par processer la séquence en entrée. L'output du top encoder est transformé en un set de vecteurs K et V, ils seront utilisé pour chaque decoder dans sa couche "encoder-decoder attention", l'aidant le decoder à se concentrer aux bons endroits de l'input seq.
![[transformer_decoding_1.gif]]

Cette étape est répétée jusqu'à qu'un symbole spécial est atteint indiquant que le transformer decoder a terminé de générer son output.
![[transformer_decoding_2.gif]]
