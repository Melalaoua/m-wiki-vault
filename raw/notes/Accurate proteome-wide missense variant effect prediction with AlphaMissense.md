**authors**:: Jun Cheng*, Guido Novati, Joshua Pan†, Clare Bycroft†, Akvile ̇Žemgulyte ̇†, Taylor Applebaum†,Alexander Pritzel, Lai Hong Wong, Michal Zielinski, Tobias Sargeant, Rosalia G. Schneider,Andrew W. Senior, John Jumper, Demis Hassabis, Pushmeet Kohli*,Žiga Avsec*
**date**::   ```2024-02-23 14:59 ```
**tags**:: #papiers/stageS2 
**groupe**:: Biology
**sous-groupe**:: #biology/AI 
**pertinence**:: 10
**links**:: https://www.science.org/doi/10.1126/science.adg7492
**modification date**:: ```Friday 23rd February 2024 14:59:56 ```

```ad-abstract
Genome sequencing has revealed extensive genetic variation in human populations. Missense variants are genetic variants that alter the amino acid sequence of proteins. Pathogenic missense variants disrupt protein function and reduce organismal fitness, while benign missense variants have limited effect.

### RATIONALE

Classifying these variants is an important ongoing challenge in human genetics. Of more than 4 million observed missense variants, only an estimated 2% have been clinically classified as pathogenic or benign, while the vast majority of them are of unknown clinical significance. This limits the diagnosis of rare diseases, as well as the development or application of clinical treatments that target the underlying genetic cause. Machine learning approaches could close the variant interpretation gap by exploiting patterns in biological data to predict the pathogenicity of unannotated variants. Specifically, AlphaFold, which accurately predicts protein structure from protein sequence, may be used as a foundation to predict the pathogenicity of variants on proteins.

### RESULTS

We developed AlphaMissense to leverage advances on multiple fronts: (i) unsupervised protein language modeling to learn amino acid distributions conditioned on sequence context; (ii) incorporating structural context by using an AlphaFold-derived system; and (iii) fine-tuning on weak labels from population frequency data, thereby avoiding bias from human-curated annotations. AlphaMissense achieves state-of-the-art missense pathogenicity predictions in clinical annotation, de novo disease variants, and experimental assay benchmarks without explicitly training on such data. As a resource to the community, we provide a database of predictions for all possible single amino acid substitutions in the human proteome. We classify 32% of all missense variants as likely pathogenic and 57% as likely benign using a cutoff yielding 90% precision on the ClinVar dataset, thereby providing a confident prediction for most human missense variants.
```

## Notes

 

```ad-warning
title: Conseils
- Pas de surlignage/highlight à outrance
- Ne paraphrase pas
- Pas de copier-coller à outrance (essaie de formuler avec tes propres mots)
```