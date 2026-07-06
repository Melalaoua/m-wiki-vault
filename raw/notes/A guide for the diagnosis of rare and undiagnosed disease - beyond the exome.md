**authors**:: Shruti Marwaha1,2* , Joshua W. Knowles1,3 and Euan A. Ashley1
**date**::   ```2024-01-24 10:06 ```
**tags**:: #papiers/stageS2 
**groupe**:: Health
**sous-groupe**:: #health
**pertinence**:: 7
**links**:: https://genomemedicine.biomedcentral.com/articles/10.1186/s13073-022-01026-w
**modification date**:: ```Wednesday 24th January 2024 10:06:15 ```

```ad-abstract
Rare diseases affect 30 million people in the USA and more than 300–400 million worldwide, often causing chronic illness, disability, and premature death. 

Traditional diagnostic techniques rely heavily on heuristic approaches, ==coupling   clinical experience from prior rare disease presentations with the medical literature==. A large number of rare disease patients remain undiagnosed for years and many even die without an accurate diagnosis. In recent years, gene panels, microarrays, and exome sequencing have helped to identify the molecular cause of such rare and undiagnosed diseases. These technologies have allowed diagnoses for a sizable proportion (25–35%) of undiagnosed patients, often with actionable findings. However, a large proportion of these patients remain undiagnosed. In this review, we focus on technologies that can be adopted if exome sequencing is unrevealing. We discuss the benefits of sequencing the whole genome and the additional benefit that may be offered by long-read technology, pan-genome reference, transcriptomics, metabolomics, proteomics, and methyl profiling. We highlight computational methods to help identify regionally distant patients with similar phenotypes or similar genetic mutations. Finally, we describe approaches to automate and accelerate genomic analysis. The strategies discussed here are intended to serve as a guide for clinicians and researchers in the next steps when encountering patients with nondiagnostic exomes.
```

## Notes
L'arrivée du [[Séquençage ADN (attention)|NGS]] a eu un effet important sur le diagnostique de maladie génétique rare où beaucoup de maladie non diagnostiquées ont été diagnostiquées par le [[OM01 - Exome et génome|ES]] (exome sequencing)

[[GE01 - Introduction générale à la génétique humaine|Séquences les membres de la famille et performer une ségrégation sur les résultats]] permet d'éliminer des centaines de variants non-causal

L'analyse en trio doit pouvoir être prise ne compte par l'AI, cette analyse peut se faire de manière automatique, les résultats, si existants, doivent être mis à disposition de l'AI.

Ce papier présente des techniques à mettre en place lorsque l'analyse par ES ne fonctionne pas.

#### Genome sequencing.
L'ES capture que les régions codantes du génome et parfois les UTRs. Mais l'ES présente des limites comme une couverture non uniforme dans les premiers régions, dans les régions riches en GC/AT, et régions à faible complexité, de plus l'ES, par définition, est limité par les sondes utilisées.

L'ES est aussi limité dans la détection de SV, régions répétées, variants pathogéniques dans les régions introniques profondes (??). 

Le Whole Genome sequencing peut palier ce problème. Tout  comme l'ES, on distingue deux types de séquençage le [[Séquençage ADN (attention)|short-read et long-read]]

![[Pasted image 20240124103045.png]]


### Transcriptomiques.

Le [[Bases de l'analyse de données en RNASeq et TCR BC|RNA-seq]] est cité dans le papier avec différents expériences qui se sont montré concluantes dans le diagnostique de maladies génétiques rare.

Le RNA-seq est préférentiellement réalisé sur les tissus malades, mais le RNA-seq sur des tissus non-invasif (fibroblastes peau, sang, [[Cellules souches hématopoïétiques dans l’embryogénèse#Types.|iPS]]) et de méthodes comme [[CRISPR CAS9]] pour les gènes peu exprimés.

### Omiques.
[[OMII - La métabolomique.|métabolomiques]], [[Spectrométrie de masse|protéomiques]].




