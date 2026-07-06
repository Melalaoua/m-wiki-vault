**authors**:: Lilian Weng
**date**::   ```2024-01-13 15:23 ```
**tags**:: #papiers/stageS2 
**groupe**:: AI
**sous-groupe**:: #AI/architecture 
**pertinence**:: 5
**links**:: https://lilianweng.github.io/posts/2023-01-27-the-transformer-family-v2/
**modification date**:: ```Saturday 13th January 2024 15:23:26 ```

```ad-abstract
Many new Transformer architecture improvements have been proposed since my last post on [“The Transformer Family”](https://lilianweng.github.io/posts/2020-04-07-the-transformer-family/) about three years ago. Here I did a big refactoring and enrichment of that 2020 post — restructure the hierarchy of sections and improve many sections with more recent papers. Version 2.0 is a superset of the old version, about twice the length.
```

## Notes
![[Pasted image 20240113152431.png]]

L'article fait une différence entre les "[[Attention is All You Need|vanilla transformers]]" et les transformers encoder-only (BERT) ou decoder-only ([[GPT-4]])


### Attention et self-attention
L'**attention** est un mécanisme chez les NN concentrant leur "attention" vers un jeu de donnée précis. La quantité d'attention est déterminée par des poids d'apprentissage 


**Self-attention** est un type d'attention où le modèle effectue une prédiction pour une partie des données en utilisant une autre partie de ses observation faite pour ces mêmes données.

Pour mieux comprendre ces deux notions, voir le 2nd lien en source de [[Transformers Neural Networks]]


```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```