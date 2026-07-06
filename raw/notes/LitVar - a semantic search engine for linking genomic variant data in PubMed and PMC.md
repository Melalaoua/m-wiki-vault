**authors**:: Alexis Allot, Yifan Peng, Chih-Hsuan Wei, Kyubum Lee, Lon Phan, Zhiyong Lu
**date**::   ```2024-06-20 09:34 ```
**tags**:: #master/StageS4 
**groupe**:: Biology
**sous-groupe**:: #biology/genetics 
**pertinence**:: 10
**links**:: https://academic.oup.com/nar/article/46/W1/W530/4995688
**modification date**:: ```Thursday 20th June 2024 09:34:49 ```

```ad-abstract
## Abstract

The identification and interpretation of genomic variants play a key role in the diagnosis of genetic diseases and related research. These tasks increasingly rely on accessing relevant manually curated information from domain databases (e.g. SwissProt or ClinVar). However, due to the sheer volume of medical literature and high cost of expert curation, curated variant information in existing databases are often incomplete and out-of-date. In addition, the same genetic variant can be mentioned in publications with various names (e.g. ‘A146T’ versus ‘c.436G>A’ versus ‘rs121913527’). A search in PubMed using only one name usually cannot retrieve all relevant articles for the variant of interest. Hence, to help scientists, healthcare professionals, and database curators find the most up-to-date published variant research, we have developed LitVar for the search and retrieval of standardized variant information. In addition, LitVar uses advanced text mining techniques to compute and extract relationships between variants and other associated entities such as diseases and chemicals/drugs. LitVar is publicly available at [https://www.ncbi.nlm.nih.gov/CBBresearch/Lu/Demo/LitVar](https://www.ncbi.nlm.nih.gov/CBBresearch/Lu/Demo/LitVar).
```

## Notes

- ==LitVar employs several state-of-the-art text mining and information extraction components in its data processing as shown in Figure 1. First, we processed the entire set of PubMed abstracts and PMC-OA full-text articles in the BioC XML format==

- We then normalized all detected entities to corresponding database identifiers (e.g. MeSH identifiers for chemical and diseases). When possible, we map variants in different forms into dbSNP identifiers (RSIDs). Otherwise, we normalize them into standard HGVS formats. After entity tagging, non-human papers were removed in order to be consistent with dbSNP, and a sentence splitter (25) was applied to segment remaining articles into individual sentences. 

- Finally, we extracted relations between entities based on sentence co-occurrence. Our LitVar data is being updated every month

![[Pasted image 20240620095003.png]]





```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```