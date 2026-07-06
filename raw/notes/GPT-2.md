tags:: #AI/models 
source:: [1](https://jalammar.github.io/illustrated-gpt2/)

Le GPT-2 n'a pas d'architecture particulièrement nouvelle, en effet son architecture est très similaire au [[Attention is all you need|decoder-only des transformers]]. Toutefois, GPT-2 est un transformer-based très large (LLM) entrainé sur une quantité massive de données.

On va explorer son architecture en détail. Cette note fait écho à la note [[The Illustrated Transformer]], reposant sur les travaux du même auteur Jay Alammar


### C'est quoi un  Language model ?
Un LM est un model AI capable de prendre une phrase en entrée et de prédire la suite. Le plus connu LM est le t9 des téléphones.

Toutefois GPT-2 est nettement plus puissant et sophistiqué que le correcteur des téléphones. Il a été entrainé sur 40GB de données (WebText).

![[Pasted image 20240114175207.png]]

Comme vu dans [[The Illustrated Transformer]], le transformer "originel" possède une partie encoder et une partie decoder. C'est une architecture appropriée pour la traduction. Toutefois on observe maintenant une division entre encoder-only et decoder-only, accumulant les parties d'un même type les unes sur les autres pour plus de performances, entrainées sur des quantités massives de données, saupoudré d'une puissance de calcule démesurée.

![[Pasted image 20240114175428.png]]

GPT-2 est un decoder-only et il produit un token à la fois. Pour chaque token produit, le token est ajouté à la séquence d'input pour la prochaine génération de tokens, on parle d'**auto-regression**. 

GPT-2 est un decoder-only et possède donc, pour chaque couche decoder, une sous-couche de Self-Attention <u>masquée</u>, l'information des tokens à droite est masquée

![[Pasted image 20240114175815.png]]
![[Pasted image 20240114175824.png]]

