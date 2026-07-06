**authors**:: Zeming Lin 1,2†, Halil Akin1†, Roshan Rao1†, Brian Hie1,3†, Zhongkai Zhu1
, Wenting Lu1 , Nikita Smetanin1 , Robert Verkuil1 , Ori Kabeli1 , Yaniv Shmueli1 , Allan dos Santos Costa4, Maryam Fazel-Zarandi1 , Tom Sercu1 , Salvatore Candido1 , Alexander Rives1,2*
**date**::   ```2024-01-15 12:02 ```
**tags**:: #papiers/stageS2 
**groupe**:: Biology
**sous-groupe**:: #biology/AI  
**pertinence**:: 6
**links**:: https://www.science.org/doi/10.1126/science.ade2574
**modification date**:: ```Monday 15th January 2024 12:02:40 ```

```ad-abstract
Recent advances in machine learning have leveraged evolutionary information in multiple sequence alignments to predict protein structure. We demonstrate direct inference of full atomic-level protein structure from primary sequence using a large language model. As language models of
protein sequences are scaled up to 15 billion parameters, an atomic-resolution picture of protein structure emerges in the learned representations. This results in an order-of-magnitude acceleration
of high-resolution structure prediction, which enables large-scale structural characterization of metagenomic proteins. We apply this capability to construct the ESM Metagenomic Atlas by predicting structures for >617 million metagenomic protein sequences, including >225 million
that are predicted with high confidence, which gives a view into the vast breadth and diversity of natural proteins
```

## Notes
- Introduction sur l'évolution des LM, faisant preuve d'efficacité en few-shot en traduction, raisonnement, résoudre des problèmes mathématiques.
- Les LM on la capacité à reconnaître des patternes dans les séquences protéiques dans l'évolution. 
- Dans le papier, ils ont mit au point un modèle à 15 milliards de paramètres, capable de résoudre en end-to-end la structure atomique de la séquence protéique.

```ad-quote
This removes costly aspects of the current state-of-the-art structure prediction pipeline, which eliminates the need for a multiple sequence alignment (MSA) while greatly simplifying the neural architecture used for inference. This results in an improvement in speed of up to 60× on the inference forward pass alone while also removing the search process for related proteins entirely, which can take >10 min with the high-sensitivity pipelines used by AlphaFold (12) and RoseTTAFold (13) and is a meaningful part of the computational cost even with recent lower-sensitivity fast pipelines(30). In practice, this means the speedup over the state-of-the-art prediction pipelines is up to one to two orders of magnitude.
```



```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```