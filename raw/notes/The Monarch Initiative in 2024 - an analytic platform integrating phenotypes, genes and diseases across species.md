**authors**:: Tim E. Putman 1 , Kevin Schaper 1 , Nicolas Matentzoglu 2 , Vincent P Rubinetti 1 ,
Faisal S. Alquaddoomi 1 , Corey Cox 1 , J. Harry Caufield 3 , Glass Elsarboukh 1 ,
Sarah Gehrke 1 , Harshad Hegde 3 , Justin T. Reese 3 , Ian Braun 4 , Richard M. Bruskiewich 5 ,
Luca Cappelletti 6 , Seth Carbon 3 , Anita R. Caron 7 , Lauren E. Chan 8 ,
Christopher G. Chute 9 , Katherina G. Cortes 1 , Vinícius De Souza 7 , Tommaso Fontana 10 ,
Nomi L. Harris 3 , Emily L. Hartley 4 , Eric Hurwitz 1 , Julius O.B. Jacobsen 11 ,
Madan Krishnamurthy 1 , Bryan J. Laraway1 , James A. McLaughlin 7 , Julie A. McMurry 1 ,
Sierra A.T. Moxon 3 , Kathleen R. Mullen 1 , Shawn T. O’Neil 1 , Kent A. Shefchek 1 ,
Ray Stefancsik 7 , Sabrina Toro 1 , Nicole A. Vasilevsky 4 , Ramona L. Walls 4 ,
Patricia L. Whetzel 1 , David Osumi-Sutherland7 , Damian Smedley 11 , Peter N. Robinson 12 ,
Christopher J. Mungall 3 , Melissa A. Haendel 1 and Monica C. Munoz-Torres 1 , *
**date**::   ```2024-01-23 14:11 ```
**tags**:: #papiers/stageS2  
**groupe**:: Health
**sous-groupe**:: #health/diagnosis , #health/data
**pertinence**:: 10
**links**:: https://pubmed.ncbi.nlm.nih.gov/38000386/
**modification date**:: ```Tuesday 23rd January 2024 14:11:30 ```

```ad-abstract
Bridging the gap between genetic variations, environmental determinants, and phenotypic outcomes is critical for supporting clinical diagnosis
and understanding mechanisms of diseases. It requires integrating open data at a global scale. The Monarch Initiative advances these goals by developing open ontologies, semantic data models, and knowledge graphs for translational research. The Monarch App is an integrated platform combining data about genes, phenotypes, and diseases across species. Monarch’s APIs enable access to carefully curated datasets and advanced analysis tools that support the understanding and diagnosis of disease for diverse applications such as variant prioritization, deep phenotyping, and patient profile-matching. We have migrated our system into a scalable, cloud-based infrastructure; simplified Monarch’s data ingestion and knowledge graph integration systems; enhanced data mapping and integration standards; and developed a new user interface with novel search and graph navigation features. Furthermore, we advanced Monarch’s analytic tools by developing a customized plugin for OpenAI’s
ChatGPT to increase the reliability of its responses about phenotypic data, allowing us to interrogate the knowledge in the Monarch graph using state-of-the-art Large Language Models. The resources of the Monarch Initiative can be found at monarchinitiative.org and its corresponding code repository at github.com/monarch-initiative/monarch-app
```

## Notes

Monarch Initiative : Consortium international harmonisant les données entre diverses disciplines scientifiques afin de faciliter le diagnostic medical.  

Ce projet vise à rassembler toutes les données phénotypiques (humaines ET autres espèces).

## API
Présence d'une API.
![[Pasted image 20240123145422.png]]

## [[Knowledge Graph]].
(semantic network) Réseau d'enttiés (evenements, situations, concepts) qui illustre la relation entre-elles.
#### Structure de la KG.
La Monarch's KG est composés de deux éléments : une collection de données avec diverses sources ([[#Data sources]]) et des ontologies.

Les composants sont représentés sous forme de noeuds, edges et labels. Un source de données ingérées importe les données depuis les sources citées en [[#Data sources]] pour le transformer dans la structure de la KG.

Les ontologies sont intégrées sous formes de couches sémantiques ([PHENIO](https://github.com/monarch-initiative/phenio)), servant de hiérarchie pour la structure de la KG et la classifications des données ingérées.

La KG intégre gene, maladies et données phénotypiques, ils ont enlevés les variants de gènes et génotypes ainsi que leur associations, car trop complexe (on pourra connecter avec [[VaRanK -  a simple and powerful tool for ranking genetic variants]])

#### Data Modele:
La KG intègre le data modèle de [[Biolink Model - A universal schema for knowledge graphs in clinical, biomedical, and translational science|BioLink]] qui est une standardisation des entités biologiques (gène, maladie, phénotype, etc...) et leur associations.


#### Data sources: 
The Monarch KG integrates knowledge from 33 heterogeneous data sources, including research organism knowledgebases (e.g. MGD (7), ZFIN (8), WormBase (9), FlyBase (10), Xenbase (11) SGD (12), PomBase (13), DictyBase (14) and BGeeDB (15)), catalogs of human models of disease (Mondo (16)) and gene-to-disease information (OMIM(17), Orphanet (orpha.net/consor/cgi-bin/index.php), information about signaling and metabolic pathways (Reactome (18)), protein-to-protein association net works (STRING (19)), and other ontologies ([[The Human Phenotype Ontology|HPO]] (4) with abnormal human phenotypes, Gene Ontology (20) with gene functional annotations, and PHENIO with integrated data about phenotypes across species and genetic backgrounds;also below) (Figure 3). We note that, historically, we utilized individual model organism database resources, how ever, since the Alliance of Genome Resources (30) has come into fruition, we now leverage their pre-harmonized genotype phenotype data

![[Pasted image 20240123160742.png]]

![[Pasted image 20240123160753.png]]



- Semsimian : outil pour mesurer la similarité phénotypique des phénotypes d'un patient et ceux d'une maladie particulière.

```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```