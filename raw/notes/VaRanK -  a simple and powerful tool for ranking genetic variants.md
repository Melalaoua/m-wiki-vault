**authors**:: [Véronique Geoffroy](https://pubmed.ncbi.nlm.nih.gov/?term=Geoffroy+V&cauthor_id=25780760)  [1](https://pubmed.ncbi.nlm.nih.gov/25780760/#full-view-affiliation-1 "Laboratoire de Génétique médicale, UMR_S INSERM U1112, IGMA, Faculté de Médecine FMTS, Université de Strasbourg , Strasbourg , France ; IGBMC, CNRS UMR 7104/INSERM U964/Université de Strasbourg , Illkirch Cedex , France.") , [Cécile Pizot](https://pubmed.ncbi.nlm.nih.gov/?term=Pizot+C&cauthor_id=25780760)  [2](https://pubmed.ncbi.nlm.nih.gov/25780760/#full-view-affiliation-2 "IGBMC, CNRS UMR 7104/INSERM U964/Université de Strasbourg , Illkirch Cedex , France.") , [Claire Redin](https://pubmed.ncbi.nlm.nih.gov/?term=Redin+C&cauthor_id=25780760)  [2](https://pubmed.ncbi.nlm.nih.gov/25780760/#full-view-affiliation-2 "IGBMC, CNRS UMR 7104/INSERM U964/Université de Strasbourg , Illkirch Cedex , France.") , [Amélie Piton](https://pubmed.ncbi.nlm.nih.gov/?term=Piton+A&cauthor_id=25780760)  [3](https://pubmed.ncbi.nlm.nih.gov/25780760/#full-view-affiliation-3 "IGBMC, CNRS UMR 7104/INSERM U964/Université de Strasbourg , Illkirch Cedex , France ; Laboratoire de Diagnostic Génétique, Hôpitaux Universitaires de Strasbourg , Strasbourg Cedex , France.") , [Nasim Vasli](https://pubmed.ncbi.nlm.nih.gov/?term=Vasli+N&cauthor_id=25780760)  [2](https://pubmed.ncbi.nlm.nih.gov/25780760/#full-view-affiliation-2 "IGBMC, CNRS UMR 7104/INSERM U964/Université de Strasbourg , Illkirch Cedex , France.") , [Corinne Stoetzel](https://pubmed.ncbi.nlm.nih.gov/?term=Stoetzel+C&cauthor_id=25780760)  [4](https://pubmed.ncbi.nlm.nih.gov/25780760/#full-view-affiliation-4 "Laboratoire de Génétique médicale, UMR_S INSERM U1112, IGMA, Faculté de Médecine FMTS, Université de Strasbourg , Strasbourg , France.") , [André Blavier](https://pubmed.ncbi.nlm.nih.gov/?term=Blavier+A&cauthor_id=25780760)  [5](https://pubmed.ncbi.nlm.nih.gov/25780760/#full-view-affiliation-5 "Interactive Biosoftware , Rouen , France.") , [Jocelyn Laporte](https://pubmed.ncbi.nlm.nih.gov/?term=Laporte+J&cauthor_id=25780760)  [2](https://pubmed.ncbi.nlm.nih.gov/25780760/#full-view-affiliation-2 "IGBMC, CNRS UMR 7104/INSERM U964/Université de Strasbourg , Illkirch Cedex , France.") , [Jean Muller](https://pubmed.ncbi.nlm.nih.gov/?term=Muller+J&cauthor_id=25780760)  [6](https://pubmed.ncbi.nlm.nih.gov/25780760/#full-view-affiliation-6 "IGBMC, CNRS UMR 7104/INSERM U964/Université de Strasbourg , Illkirch Cedex , France ; Laboratoire de Diagnostic Génétique, Hôpitaux Universitaires de Strasbourg , Strasbourg Cedex , France ; Laboratoire ICUBE, UMR CNRS 7357, LBGI, Université de Strasbourg , Strasbourg , France.")
**date**::   ```2024-01-23 13:48 ```
**tags**:: #papiers/stageS2 
**groupe**:: Biology
**sous-groupe**:: #biology/genetics #biology/bioinfo
**pertinence**:: 9
**links**:: https://pubmed.ncbi.nlm.nih.gov/25780760/
**modification date**:: ```Tuesday 23rd January 2024 13:48:37 ```

```ad-abstract
Background. Most genetic disorders are caused by single nucleotide variations (SNVs) or small insertion/deletions (indels). High throughput sequencing has broadened the catalogue of human variation, including common polymorphisms, rare variations or disease causing mutations. However, identifying one variation among hundreds or thousands of others is still a complex task for biologists, geneticists and clinicians. Results. We have developed VaRank, a command-line tool for the ranking of genetic variants detected by high-throughput sequencing. VaRank scores and prioritizes variants annotated either by Alamut Batch or SnpEff. A barcode allows users to quickly view the presence/absence of variants (with homozygote/heterozygote status) in analyzed samples. VaRank supports the commonly used VCF input format for variants analysis thus allowing it to be easily integrated into NGS bioinformatics analysis pipelines. VaRank has been successfully applied to disease-gene identification as well as to molecular diagnostics setup for several hundred patients. Conclusions. VaRank is implemented in Tcl/Tk, a scripting language which is platform-independent but has been tested only on Unix environment. The source code is available under the GNU GPL, and together with sample data and detailed documentation can be downloaded from http://www.lbgi.fr/VaRank/.
```

## Notes

Varank effectue plusieurs choses :
- Variant calling : filtre les faux positifs.
- Annotation de variant (functional impact, effets sur la protéine, fréquence dans la population, phénotypes...)
- Présence ou absence de variants (homozygote et hétérozygotes) sous forme de barcode.
- Priorisation : attribue un score à chaque variant en accord avec la pathogénicité.

![[Pasted image 20240123135751.png]]




```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```