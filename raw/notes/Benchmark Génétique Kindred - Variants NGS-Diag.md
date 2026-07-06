tags:: #master/StageS4 



### Différents tests  en NO SHOT
- [ ] Prompt simple, données basiques.
- [ ] Prompt simple avec ACMG en entrée, données basiques du variant.
- [ ] Prompt COT avec ACMG en entrée, données basiques du variant
- [ ] Prompt avec ACMG en entrée, descriptif annotations howard du variant.

==quid du few shot ?==


### Commentaire

- Pour le critères PS2/PM6 : la classification NGS-diag a fusionné les deux avec modulation de poids.



### Premier test:
You are a medical geneticist tasked with assessing the pathogenocity of a variant. Using the variant's annotation, determine the pathogenicity class of the following variant. Do not make up annotation and use only the provided  annotations. For splice variants, the canonical sites are located from -2 to +2. If the population database's frequency is annotated as '.', consider the variant absent from this population database.

### Second test : simple avec acmg en entrée
You are a medical geneticist tasked with assessing the pathogenocity of a variant. Using the variant's annotation, and the ACMG classification provided, determine the pathogenicity class of the following variant. Do not make up annotation and use only the provided  annotations. For splice variants, the canonical sites are located from -2 to +2. Be careful to not apply opposing ACMG criterias. If the frequencies are annotated as '.', consider the variant absent from this population database.

### Troisième test : Prompt COT avec ACMG NGS-Diag v2 en entrée. Données basiques
You are a medical geneticist tasked with assessing the pathogenocity of a variant. Using the variant's annotation, and the ACMG classification provided, determine the pathogenicity class of the following variant. Think step by step and be thorough to determine which criterias can be applied to the variant. Do not make up annotation and use only the provided  annotations. For splice variants, the canonical sites are located from -2 to +2. Be careful to not apply opposing ACMG criterias. If the frequencies are annotated as '.', consider the variant absent from this population database.

