# JEPA: Predicting Representations—from Images to Genomes

## Contrat
- Journal club pour iCube, Mardi 8 Septembre 2026.
- Audience : laboratoire CSTB familiers avec les transformers (PLM, GLM, ...)
- Expertise dans le self-supervised learning : **incertain**.
- 14 slides, 28 minutes de présentation (2 min de marge) sans prendre en compte les discussions.
- Ce document contient le script à lire (traduit directement de la version anglaise) et des informations techniques sur le PPT.
- Argument central de la présentation : **JEPA l'objectif de prédiction pendant l'entrainement d'un modèle IA. Est-ce que l'espace latent contient encore des informations biologiques ?**

| Slide | Minutes | Cumulative target |
| ----- | ------: | ----------------: |
| 1     |       1 |             01:00 |
| 2     |       2 |             03:00 |
| 3     |       2 |             05:00 |
| 4     |     2.5 |             07:30 |
| 5     |     2.5 |             10:00 |
| 6     |       3 |             13:00 |
| 7     |       2 |             15:00 |
| 8     |       2 |             17:00 |
| 9     |       2 |             19:00 |
| 10    |     2.5 |             21:30 |
| 11    |       2 |             23:30 |
| 12    |     1.5 |             25:00 |
| 13    |       2 |             27:00 |
| 14    |       1 |             28:00 |

### Slide 1 - Que dois prédir un modèle biologique de fondation ?.
---
- *Temps : 1 minute.*
- *Objectif : Connecter l'architecture au laboratoire CSTB.*
- *Sur l'écran : titre + "A technical introduction and critical biological case study" + 3 figures représentatives.*

#### Script.
Examinons la question que cherchent à répondre le modèles que nous utilisons en biologie : PLM pour les protéines, GLM pour la génétiuqe : **dans quel but sont entrainés ses modèles de nos jours ?**
La plupart sont entrainés à reconstruire l'information manquante, à prédire le prochain nucléotide. 
**=> l'architecture JEPA, pour joint-embedding predictive architecture cherche à savoir s'il est possible de faire apprendre les modèles en les entrainant à prédire l'information manquantes à partir des représentations latentes.**

Je commence déjà par expliquer cette idée apportée par Yann Lecun concernant les modèles intelligents. Je poursuivrai par une vue technique de l'entrainement d'un modèle étape par étape par I-JEPA (image). Et ensuite on examinera une application concrète de JEPA en génétique.

Mon objectif est que, d'ici la fin, on peut comprendre ensemble cette nouvelle architecture, comprendre sa fonction de perte, et voir ses limites.

**Transition** : Commençons par comprendre pourquoi la prédiction est importante.

**Sources:** [S01: LeCun, 2022](https://openreview.net/pdf?id=BZ5a1r-kVsf); [S02: I-JEPA](https://arxiv.org/abs/2301.08243); [S06: JEPA-DNA](https://arxiv.org/html/2602.17162v3).

### Slide 2 - Prédire une observation ou prédire une représentation ?
- *Temps : 2 minutes.*
- *Objectif : Etablir la distinction entre les deux sans impliquer que les modèles actuels sont défectueux.*
- *Sur l'écran : Photo oiseau et disctinction entre les deux*

#### Script
Considérons cette partie de l'oiseau masquée. On est capable de prédire que dans ce carré on retrouve l'aile de l'oiseau. Sans être certains de la couleur de chaque plume ou pixel consittuant notre oiseau.

C'est là le coeur du message : un objectif d'entrainement par observation va voulor comparer au pixel près l'erreur de notre modèle. Tandis que par représentation, va tout d'abord envoyer notre image complète à travers un encodeur, et demander à un autre modèle de prédire les features associées à la région cachée. 

[Pointer les deux target spaces]

Notre modèle est entrainé à **potentiellement** retenir les informations prédictibles tout en étant moins sensibles à des détails qu'on ne peut pas prédire et qui ne seront de toute façon pas utile à notre tâche. Le mot "potentiellement" est important ici, un embedding est un vecteur de X dimension, pas une assurance que cette donnée est sémantiquement correcte. Il est possible que le modèle retienne des informations pertinentes, mais aussi du bruit ou juste rien retenir de représentatif.

De plus, les modèles de languages apprennent déjà des représentations riches de nos données (notamment via le mécanisme de self-attention). La distinction avec JEPA se trouve dans la cible à atteindre par le modèle mais aussi comment notre cible est construire (i.e via un encodeur).

En biologie, ca créée une tension immédiate. Certaines séquences seront pertinentes dans un contexte et tantôt inutile dans un autre. Un simple nucléotide changé peut être décisif. C'est donc risqué de translationner cette idée de supprimer des détails à première vue inutile comme pour une image. On doit se poser la question quelles informations conserve la représentation latente de notre modèle, et évaluer sa pertinence dans une tâche biologique.

**Transition** : On est donc capable de positionner JEPA face à plusieurs objectifs.

**Sources:** [S01](https://openreview.net/pdf?id=BZ5a1r-kVsf); [S02, introduction and Figure 2](https://arxiv.org/pdf/2301.08243); [S12: MAE](https://arxiv.org/abs/2111.06377). The bird and single-variant discussion are original teaching examples, not reported experiments.

### Slide 3 - JEPA est une méthode d'entrainement, pas un remplacement des transformers.

- *Temps : 2 minutes.*
- *Objectif : Distinguer le squelette, l'objectif et l'utilisation*
- *A l'écran : Tableau ci-dessous.*

#### Script
Il y a trois niveaux à distinguer dans l'architecture JEPA (pléonasme) : l'objectif d'entrainement, le backbone (squelette), et l'utilisation en aval.

Un transformers est un backbone qui prends en entrée des matrices de tokens. Il peut être entrainé à reconstruire des observations (du texte), aligner des représentations, ou alors prédire des représentations. 

Le premier rang couvre la prédiction d'observation : MLM (masked language modeling), le modèle cherche à prédire les tokens sur des positions masquées. Par exemple un autoencoder va reconstruire l'image au niveau du pixel près.

La seconde ligne couvre l'alignement du modèle à partir de différentes vues d'une même donnée c'est le cas de SimCLR ou BYOL.

Et enfin la troisième ligne se concentre sur le point suivant : considérant le contexte et la position de la cible, prédit la representation latente de la cible. Le contexte et la cible ne sont pas forcément des représentations identiques mais le prédicteur apprends à comprendre la relations entre les deux.

Nos trois catégories d'entrainement ne sont pas clivées, elles vont même se superposer en certains points. Ce qui nous intéresse c'est la vue technique, qu'est ce que chaque partie de l'architecture voit, ce qui est prédit, la fonction de perte appliquée, et comment elle peut s'effondrer.

**Transition:** “Voici le graphique pour I-JEPA.”

**Sources:** [S02, Figure 2](https://arxiv.org/pdf/2301.08243); [S10: BYOL](https://arxiv.org/abs/2006.07733); [S13: SimCLR](https://arxiv.org/abs/2002.05709); [S15: Transformer](https://arxiv.org/abs/1706.03762).

### Slide 4 -- I-JEPA : trois objectif d'entrainement et deux mécanisme de mise à jours des paramètres.
---
- *Temps : 2.5 minutes*
- *Objectif : Description du flux de données et mise à jour des paramètres.*

#### Script.
I-JEPA poursuit 3 objectifs : 
1. Un context encoder prends les données en entrée, un batch d'images, et possède des paramètres theta.
2. Un predicteur prends la features embedding du contexte généré par l'encodeur et son seul but est de prédire les features en sorties, ce dernier a les paramètres notés phi.
3. Un autre encodeur prends notre cible d'entrainement et produit des features cibles. On compare les deux. L'encodeur 2 possède les paramatères theta barre.

L'encodeur de la cible voit l'image en entier. L'encodeur du contexte ne voit que des bout de l'images et le prédicteur est guidé pour lui dire ou prédire, il ne recoit pas l'image en entier. seulement la position et le contexte latent généré par l'encodeur, sinon on tombe dans un objectif de reconstruction au pixel près.

La fonction de perte entraine l'encodeur du contexte et le predicteur par backpropagation. Pour l'encoder cible, on met à jour ses paramètres par moving average.

Deux mécanismes distinct : par gradient en haut, par moving average en bas

**Transition:** “On va se concentrer quelques minutes sur les données en entrée”

**Sources:** [S02, §3 and Figure 3](https://arxiv.org/pdf/2301.08243); [S16: released training code](https://github.com/facebookresearch/ijepa/blob/52c1ae95d05f743e000e8f10a1f3a79b10cff048/src/train.py).

### Slide 5 - Exemple concret : quelles informations entrent dans le système ?
---
- *Temps : 2.5 minutes*
- *Objectif : Montrer que le masking fait partie intégrante de l'entrainement*

#### Script.
Voici un exemple concret avec une image divisée en 16 morceaux. On cache le carré central aux positions 5 6 9 10. L'encodeur du context reçoit que les morceaux de la partie verte (12 morceaux) ainsi que leur position associée.

Supposons que nos features sont de 8 dimensions. Pour une image, l'encodeur reçoit une matrice de 12 x 8. 

Notre encodeur cible lui reçoit les 16 morceaux, fois 8. Mais on s'interesse qu'aux positions du centre, donc nos morceaux cibles seront de dimensions 4 x 8.

Le predicteur va recevoir la matrice de 12 x 8 ainsi que 4 requête de position (prédit position 5, 6, 9, 10). Il produit en sortie une matrice de 4 x8, comparable à ce qu'à produit notre encodeur cible.

Le but de ce simple exercise est de montré qui à accès à quoi. Le vrai I-JEPA est plus complexe. Si une cible est petite, les pixels environnants peuvent suffire à la prédiction. Si la cible est très large et le contexte pas très informatif, la prédiction peut être ambiguë. Le fait de masquer induit un biais dans notre modèle.

Pour un génome, les choix techniques peuvent être la tokenization, la longueur des séquence. Ce n'est pas sûr que la recette appliquée içi soit pertinente pour un génome.


**Transition:** “Une fois qu'on a explicité la différence entre ce qui entre, c'est facile d'établir notre fonction de perte"

**Sources:** [S02, §3, Figure 4, and masking ablations](https://arxiv.org/pdf/2301.08243). The sixteen-patch tensors are an original illustrative construction.

### Slide 6 -- L'objectif et une étape d'entrainement
---
- *Temps : 3 minutes*
- *Objectif : Expliquer les 3 équations centrale à I-JEPA*

#### Script.
Cette première equation décris la prédiction du modèle ains que ça cible. A gauche, $ĥ_{T} = g_{\phi}(f_{\theta}(x_{C}, p_{T}))$  représente la prédiction du modèle des features générées par l'encodeur ainsi que de la position. A droite, l'encodage de l'image entière par l'encodeur cible à la position identique que l'équation de gauche, le tout entouré d'un stop gradient.

La seconde equation c'est la fonction de perte qui consiste en une moyenne de la perte entre la prédiction h_barre et l'encodage de l'image entière pour chaque patch masquée de notre image, divisé par le nombre de patch, et redivisé par le nombre de blocs de patchs.

Cette fonction permet d'update les paramètres de l'encodeur de contexte ainsi que le prédicteur. Mais quid de l'encodeur cible ?

C'est notre troisième équation : Si le paramètre de notre ancien encodeur est 2, le nouveau paramètre de l'encodeur de context est 3, et notre facteur tau est 0.9, le nouveau paramètre de l'encodeur cible est 2.1

Une problématique se pose face à tout ça, si tout nos composants apprennent, pourquoi ne se mettent t'il pas d'accord sur une constante inutile ?

**Transition:** the final sentence opens slide 7.

**Sources:** [S02, §3](https://arxiv.org/pdf/2301.08243); [S16, `forward_target`, `loss_fn`, and momentum update](https://github.com/facebookresearch/ijepa/blob/52c1ae95d05f743e000e8f10a1f3a79b10cff048/src/train.py). Arithmetic is illustrative; it is not a trained-model result.

### Slide 7 -- Effondrement (collapse) : une faible erreur veut peut être dire aucune information.
---
- *Temps : 2 minutes*
- *Objectif : Séparer l'optimisation du modèle de l'apprentissage de répresentation informative*

#### Script.
Supposons deux encodeurs produisant le même résultat de manière constante pour chaque données en entrée. Le prédicteur produit aussi cette constante. L'erreur est de zero. Pourtant la représentation du modèle ne peut pas distinguer une voiture d'un oiseau, ou une séquence ADN d'une autre.
C'est l'effondrement de représentation, ou representation collapse. En voulant réduire l'erreur, en optimisant le modèle, ce n'est pas suffisant pour faire apprendre au modèle des représentations informatives.

I-JEPA utilise un apprentissage asymétrique avec le stop-gradient et l'EMA, et le masking. Ca fonctionne de manière empirique. Mais ca ne veut pas dire que l'EMA et le stop-gradient empêche théoriquement l'effondrement, c'est un pansement.

JEPA-DNA c'est le second papier que je veux vous montrer, qui applique JEPA à la génétique, eux ils ont utilisé des restrictions sur la distribution des représentations latentes du modèle. VICReg inclues un terme qui pénalise le modèle si ces représenations sont trop peu variables de l'une à l'autre.

Mais avant ça, on s'est concentré que sur l'objectif d'entrainement, l'architecture, on a pas encore parlé des utilisations possibles de JEPA.

**Sources:** [S02, §2–3](https://arxiv.org/pdf/2301.08243); [S09: VICReg](https://arxiv.org/abs/2105.04906); [S11: SimSiam](https://arxiv.org/abs/2011.10566). The counterexample and biological confounders are explanatory analysis.

### Slide 8 - Que I-JEPA démontre ?
---
- *Temps : 2 minutes*
- *Objectif : Lire un résultat*

#### Script.
Comment est évaluée la capacité de représentation du modèle ? Ce qu'ont fait les chercheur, c'est du linear probing, on va entrainer un classifieur linéaire sur un encodeur avec ses paramètres gelés en ingérant des données déjà labéllisées dans notre encodeur. On y récupère les espaces latents de ces données pour y entrainer notre classifieur linéaire.

Par exemple sur la diapositive on retrouve 2 architectures : un Masked AutoEncoder (MAE) et JEPA. Les deux ont comme squelette un transformer ViT et son testé sur un benchmark d'images (ImageNet-1K). On remarque que I-JEPA est plus performant de 2% pour  Le papier rapporte 79.3 de précision sur le benchmark IMageNet-1k pour 5x moins d'epochs d'entrainement.

C'est une preuve qualitative que I-JEPA permet d'apprendre des représentations informatives sur les données. C'est pas une évidence de sa supériorité par rapport aux autres architectures cependant : on a aucune info sur le temps de calcul/la puissance nécessaire.

Ils ont aussi fait des études ablatives sur l'architecture en changeant les stratégies, en enlevant le masking, et ces résultat supportent le fait que la tâche sur lequel est entrainé le modèle est importante.

**Transition:** “Useful image features are one milestone. Temporal prediction and planning add further requirements.”

**Sources:** [S02, Table 1, Tables 6–7, Appendix A.1](https://arxiv.org/pdf/2301.08243); [S12: MAE](https://arxiv.org/abs/2111.06377).

### Slide 9 - De la représentation au world model.
---
- *Temps : 2 minutes*
- *Objectif : Connecter JEPA aux world models*

#### Script.
La proposition de Yann Lecun sur JEPA inclue les worlds models capables de prédire à certains niveaux d'abstraction leur entourage, ainsi que leur capacité de plannification.

On a montré que I-JEPA est capable d'apprendre des représentations informatives, mais on est encore loin du système autonome intelligent.

V-JEPA étends la prédiction jusqu'à l'image. C'est la même chose que I-JEPA, mais se rajoute la temporalité dans l'équation. La différence c'est qu'on peut reconstruire l'image avec l'image d'avant, et l'image d'après. Un modèle autorisé à regarder les images futures ne démontre pas les mêmes capacités qu'un modèle qui doit prédire le futur à partir des informations disponibles à l'instant t.

Le twist avec V-JEPA-2, c'est qu'on veut prédire comment évolue notre espace latent quand on rajoute une action dans le mix. La deuxième version rajoute un modèle capable de recevoir une action en plus du contexte. Le modèle reçoit des vidéos + l'état du robot à cet instant (porte la balle, ...). 

Ils ont deployé ce modèle en environnement zero-shot, le modèle evalues les actions possibles à l'instant t à partir du contexte, et d'un objectif, execute son action, recommence.

Cette diapositive sert à faire la distinction entre représentations informatives, prédiction dans le temps, et plannification par l'action.

**Transition:** “We can now ask what carries over when the observations are DNA sequences.”

**Sources:** [S01](https://openreview.net/pdf?id=BZ5a1r-kVsf); [S03: V-JEPA](https://arxiv.org/abs/2404.08471); [S04: V-JEPA 2, §3–4](https://arxiv.org/abs/2506.09985); [S05: V-JEPA 2.1](https://arxiv.org/abs/2603.14482). The clinical distinction is methodological analysis, not a claim of validated treatment simulation.

### Slide 10 - JEPA-DNA un objectif hybridie pour les modèles de language génomique actuels.
---
- *Temps : 2.5 minutes*
- *Objectif : Porter l'explication précédente à la biologie*.

#### Script.
Passons à l'ADN, voici JEPA-DNA, et se base sur des modèles de fondations de génétique, c'est un préprint (3e versoin), et ce n'est pas de l'entrainement from scratch, ils ont réutilisés des modèles de languages de génomique pre-trained.

On conserve l'objectif initial des genetics languages models : prédiction masquée ou prédiction du prochain token (depend de que GFM utilisé). Ils ont rajouté une branche qui cherche à prédire la séquence génomique masquée contre la même séquence non-masquée.

La différence avec I-JEPA est importante : I-JEPA veut prédire des patch d'image masqués, ici, on prédit des séquences globales. JEPA-DNA emprunte l'idée globale du JEPA, prédire des espaces latent à partir de contextes incomplets.

La fonction de perte contient 4 contributions. La capacité de reconstruire la séquence du modèle de language, la perte entre l'élève et l'enseignant. Et enfin deux autres termes : la variance et la covariance qui encourage la diversification du modèles et eviter l'effondrement de ce dernier comme expliqué auparavant.

Ils ont fait des tests sur des modèles de fondations de génétique connus comme DNABERT-2, Nucleotide Transformer 3, HyenaDNA.

Il faut faire attention, la cible utilisée pour l'entrainement JEPA est produite par un modèle déjà pre-entrainé, ce n'est pas une mesure directe de notre séquence. Ils ont continué leur expérience pour mesurer si le modèle était capable de tirer des représentations utiles pour une tâche donnée.

**Transition:** “The key journal club question is therefore: which part of this recipe actually helps?”

**Sources:** [S06, §3–4 and Figure 1](https://arxiv.org/html/2602.17162v3); [S09](https://arxiv.org/abs/2105.04906).

## Slide 11 — Improvements are task-dependent, and controls change the conclusion

**Time:** 2 minutes. **Purpose:** make a concrete, balanced critical argument.

**On screen:** a selected three-task panel for DNABERT-2, labeled “Table 1, linear probing, AUROC”.

| Task | Baseline | JEPA-DNA |
|---|---:|---:|
| TF binding | 0.788 | 0.839 |
| Coding pathogenicity | 0.624 | 0.610 |
| sQTL | 0.585 | 0.577 |

Below: “Table 4: MLM + latent prediction alone underperforms MLM-only continual training on its three displayed tasks.” Footer: “Selected examples, not the complete benchmark; no statistical significance claimed.”

**Visual instructions:** use `assets/dna_results.svg`; label positive and negative changes. Do not average these selected rows or imply that all variant tasks regress. Put the complete component-ablation table in backup B6.

**Spoken script:**

These are selected examples from the DNABERT-two results, not a summary of every task. Transcription-factor binding AUROC improves from zero point seven eight eight to zero point eight three nine. But coding pathogenicity falls from zero point six two four to zero point six one zero, and the sQTL result also decreases.

We cannot conclude that JEPA always helps, or that it always harms variant tasks. We can conclude that the answer depends on the task and the full configuration. These point estimates also do not, by themselves, establish statistical significance.

The component ablation is even more informative. The paper includes continued training with the language objective alone. On its three displayed tasks, adding the latent prediction loss alone performs slightly worse than that continued-training control. The stronger results arise with additional ingredients in the recipe.

The appendix also uses labeled splice-site validation to select checkpoints. So the defensible conclusion is about a combined, selected training pipeline—not a universally beneficial isolated JEPA term.

For our lab, the follow-up would be a matched experiment: same starting checkpoint, data, training budget, and evaluation splits, comparing continued language modeling against the added objectives. That would tell us whether the extra complexity earns its place on our task.

**Transition:** “Protein applications raise a related question: where does the teacher's biological information come from?”

**Sources:** [S06, Tables 1 and 4](https://arxiv.org/html/2602.17162v3). The proposed matched experiment is ours, not a reported completed experiment.

## Slide 12 — Protein representations: inspect the teacher's information

**Time:** 1.5 minutes. **Purpose:** include proteins while preserving the distinction between direct evidence and an analogy.

**On screen:** “ProtJEPA · recent preprint”; schematic “sequence student → predict multimodal teacher representation”; questions: “What information trained the teacher?”, “How are homologs separated?”, “Does the task require residue-level precision?”

**Visual instructions:** show multiple biological information sources entering the teacher side during training, and sequence alone entering the student side. Label “conceptual schematic based on the abstract; full-method audit unavailable for this package”. No numerical performance chart.

**Spoken script:**

A recent protein preprint, ProtJEPA, reports a sequence-based student trained to predict a teacher representation built from multiple biological modalities. That makes it a useful comparison, but it is not simply the I-JEPA image diagram with amino acids substituted for pixels.

The important distinction is the teacher's information. If the teacher has access to richer biological signals during training, we need to account for that when comparing with a sequence-only baseline. Sequence-only inference does not imply sequence-only training information.

For protein evaluation, I would ask how homologous sequences are separated between training and testing, what annotation information the teacher has seen, and whether the representation supports the task we actually care about. Protein-level functional retrieval and single-residue variant effects are different tests.

I am presenting this as an emerging direction rather than a settled performance claim: the accessible abstract supports this high-level description, but I have not established the full experimental controls. The broader lesson is to inspect the source of the target representation before interpreting a gain.

**Transition:** “Let us turn these concerns into a concrete research decision.”

**Sources:** [S07: ProtJEPA abstract](https://www.biorxiv.org/content/10.64898/2026.08.03.742606v1). No protein metric or detailed leakage claim is asserted. The evaluation questions are proposed critical-reading criteria.

## Slide 13 — What would we test in this lab?

**Time:** 2 minutes. **Purpose:** propose a falsifiable next experiment and connect to clinical/phylogenetic interests.

**On screen:** “Hypothesis: latent prediction adds useful task information beyond matched continued pretraining.” Three comparison arms: existing checkpoint; continued language objective; same continuation plus latent objective and separately ablated regularization. Three evaluation requirements: leakage-aware splits; task-relevant metrics; uncertainty across runs.

**Visual instructions:** a simple experiment matrix, labeled “PROPOSED — NOT RUN”. Avoid making biological family/clade splits a one-size-fits-all rule; say the split must match intended deployment. Additional clinical and phylogenetic discussion goes in B8–B9.

**Spoken script:**

My proposed next step would be a bounded comparison on one existing lab task, rather than training a large foundation model immediately.

Start from the same pretrained checkpoint. Retain its original result, continue training with its language objective, and compare that with the additional latent objective. Then separate the effects of regularization and masking instead of attributing every improvement to the architecture name.

Match the data exposure and report computational cost. Choose the evaluation split before examining results. For a genomic task, nearby or related sequences may create leakage. For proteins, homology matters. For clinical records, the same patient must not cross the split, and any future information must be excluded from the inputs.

Measure the task we actually want to improve, report variability across runs, and include failure cases. A low self-supervised loss or an attractive embedding plot is not the endpoint.

For phylogenetics, embedding similarity is not automatically an evolutionary distance. For clinical work, good prediction is not automatically a treatment-effect model. These are interesting applications, but they require their own validation.

The question I would bring back to the lab is: on which task would a better representation help us, and what result would convince us that JEPA added something beyond a well-controlled baseline?

**Transition:** “I will close with three points.”

**Sources:** methodological synthesis informed by [S02](https://arxiv.org/pdf/2301.08243) and [S06](https://arxiv.org/html/2602.17162v3); clinical illustration contextualized by [S08](https://arxiv.org/abs/2605.10840). The proposal has not been run and no power/compute estimate is claimed.

## Slide 14 — Three take-home messages

**Time:** 1 minute. **Purpose:** leave the audience with a precise summary and an opening for discussion.

**On screen:**

1. “Predicting learned representations changes the learning problem.”
2. “Useful targets require more than agreement: inspect collapse, masking, and evaluation.”
3. “Biological value is task-specific and must beat a matched baseline.”

**Visual instructions:** repeat the three icons from slide 1. No new equations or new paper names.

**Spoken script:**

First, JEPA changes the learning target: we predict features generated by an encoder, rather than requiring the latent objective to recover every observation detail.

Second, the training design matters. We need to understand what each branch sees, how the target changes, and why low prediction error does not by itself demonstrate a useful representation.

Third, biology makes the evaluation question especially sharp. A representation that helps one functional task may not preserve the details required by another. The genomic results give us a promising method to investigate, together with reasons to insist on matched controls.

The question for discussion is: what biological distinction would we want this representation to preserve, and how would we test that?

**Sources:** synthesis of the cited main papers. End the scripted talk here; use backup slides only in response to discussion.

## Delivery and editing rules

Keep the 14-slide sequence. The complete narration is intentionally more detailed than the on-screen text. Rehearse with diagrams: do not silently assume that a word-count estimate measures delivery speed. If running late, shorten the optional paper-history sentence in slide 9 and the protein comparison before removing the training walkthrough or the genomic controls. Do not remove the preprint labels, the code-versus-paper loss distinction, the teacher-at-inference correction, or the positive/negative genomic examples.

There are no numerical claims about biological mechanisms, prospective clinical utility, or phylogenetic accuracy in this presentation. A future agent must not add such claims to make the story sound more conclusive.
