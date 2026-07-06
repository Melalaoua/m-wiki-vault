**authors**:: Shuya Abe 1, Shinichiro Tago 1 , Kazuaki Yokoyama 2 , Miho Ogawa 2, Tomomi Takei 2, Seiya Imoto 3
and Masaru Fuji 1,
**date**::   ```2024-01-26 10:58 ```
**tags**:: #papiers/stageS2 
**groupe**:: Biology
**sous-groupe**:: #biology/genetics #biology/AI 
**pertinence**:: 8
**links**:: https://www.mdpi.com/2072-6694/15/4/1118
**modification date**:: ```Friday 26th January 2024 10:58:45 ```

```ad-abstract
Background: To treat diseases caused by genetic variants, it is necessary to identify disease-causing variants in patients. However, since there are a large number of disease-causing variants, the application of AI is required. We propose AI to solve this problem and report the results of its application in identifying disease-causing variants. Methods: To assist physicians in their task of identifying disease-causing variants, we propose an explainable AI (XAI) that combines high estimation accuracy with explainability using a knowledge graph. We integrated databases for genomic medicine and constructed a large knowledge graph that was used to achieve the XAI. Results: We compared our XAI with random forests and decision trees. Conclusion: We propose an XAI that uses knowledge graphs for explanation. The proposed method achieves high estimation performance and explainability. This will support the promotion of genomic medicine.
```

## Notes
To treat diseases caused by genetic mutations, such as mutations in genes and
cancer cells, genomic medicine is being promoted to identify disease-causing variants in individual patients using comprehensive genetic analysis ([[Séquençage ADN (attention)|next-generation sequencing]], or NGS) for diagnosis and treatment. However, clinical interpretation of the large amount of variant data output by NGS is a time-consuming task and has become a bottleneck in the promotion of genomic medicine. Although AI development to support this task has been conducted in various fields, none has yet been realized that has both high estimation accuracy and explainability at the same time. Therefore, we propose an AI with high estimation accuracy and explanatory power, which will eliminate the bottlenecks in genomic medicine.

L'interprétation clinique des données NGS se fait par l'étude de papiers médicaux, bases de données, étude cliniques des patients, c'est une tâche intense et coûteuse demandant une haute expertise.

L'application des AI dans la médecines est prometteuse et a pu par exemple prédire la métastase de noeuds lymphatiques dans le Cancer du sein, ou dans la progression de la maladie d'Alzheimer.


Dans le papier, ils ont couplé une modèle d'AI avec des bases de données externes de génétique médicale, (OMIM, [[The Monarch Initiative in 2024 - an analytic platform integrating phenotypes, genes and diseases across species|The Monarch Initiative]], ...).

Ils ont construit un [[Knowledge Graph]] regroupant, en utilisant une ontologie, articles de médecine, bases de données public, information cliniques, guidelines comme l'ACMG, JSH, ASH, NCCN.

![[Pasted image 20240126111520.png]]



```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```