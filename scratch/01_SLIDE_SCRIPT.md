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

##### Script.
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

##### Script
Considérons cette partie de l'oiseau masquée. On est capable de prédire que dans ce carré on retrouve l'aile de l'oiseau. Sans 

**Sources:** [S01](https://openreview.net/pdf?id=BZ5a1r-kVsf); [S02, introduction and Figure 2](https://arxiv.org/pdf/2301.08243); [S12: MAE](https://arxiv.org/abs/2111.06377). The bird and single-variant discussion are original teaching examples, not reported experiments.

## Slide 3 — JEPA is a learning architecture, not a replacement for transformers

**Time:** 2 minutes. **Purpose:** separate backbone, objective, and downstream use.

**On screen:** a three-row comparison.

| Learning pattern | Compared during training | Example |
|---|---|---|
| Reconstruct/predict observations | Prediction versus pixels or tokens | MAE; masked language modeling |
| Align representations | Compatible views, with a non-collapse mechanism | SimCLR; BYOL |
| Predict representations | Context-conditioned prediction versus target features | I-JEPA |

Footer: “These families overlap; a predictor or EMA teacher alone does not define JEPA.”

**Visual instructions:** align the three small diagrams vertically; use the same encoder icon in every row. Explicitly show that SimCLR is contrastive and BYOL is non-contrastive. No “all joint embeddings require negatives” implication.

**Spoken script:**

There are three levels that we should keep separate: the backbone, the learning objective, and the downstream application.

A transformer is a backbone that processes a sequence of tokens. It can be trained to reconstruct observations, align representations, or predict representations. Saying “JEPA versus transformer” therefore compares different kinds of things.

The first row covers observation prediction. In masked language modeling, the model predicts token identities at masked positions. In a masked autoencoder for images, it reconstructs pixels.

The second row concerns alignment between compatible views. SimCLR uses a contrastive objective with negative examples. BYOL instead uses a predictor and a moving target network without explicit negative pairs. That already tells us that neither a predictor nor a moving teacher was invented by I-JEPA.

In the third row, the emphasis is a conditional relationship: given this context and the location of a target, predict the target's representation. The context and target do not have to become identical representations. The predictor learns the relationship between them.

These categories are useful, but their boundaries overlap. What we should inspect in a paper is the actual computational graph: what each branch sees, what is predicted, where the loss is applied, and how collapse is addressed.

**Transition:** “Here is that graph for I-JEPA.”

**Sources:** [S02, Figure 2](https://arxiv.org/pdf/2301.08243); [S10: BYOL](https://arxiv.org/abs/2006.07733); [S13: SimCLR](https://arxiv.org/abs/2002.05709); [S15: Transformer](https://arxiv.org/abs/1706.03762).

## Slide 4 — I-JEPA has three trainable roles and two update mechanisms

**Time:** 2.5 minutes. **Purpose:** make the data and parameter flows unambiguous.

**On screen:** context encoder `fθ`, predictor `gφ`, target encoder `fθ̄`. Solid arrows are data flow, a dashed arrow is the EMA parameter update. Loss receives predicted and target features. A stop-gradient mark sits on the target feature branch.

**Visual instructions:** use `assets/ijepa_architecture.svg` as a starting diagram or redraw it with native editable shapes. The complete image goes into the target encoder; target positions are selected after encoding. Hidden target patches are removed before context encoding. Put “full image” and “visible patches only” on the correct branches. Never connect the target features to the predictor input.

**Spoken script:**

I-JEPA has three roles. First, a context encoder processes the visible image patches. Its parameters are theta. Second, a predictor takes those context features and tokens specifying the positions to predict. Its parameters are phi. Third, a target encoder produces the features that the prediction will be compared against.

[Trace the upper path, then the lower path.]

The target encoder has the same backbone architecture as the context encoder, but its parameters are maintained separately. We denote them theta bar.

An important detail is that the target encoder sees the complete image. We then select the output representations at the target positions. We do not first crop the hidden region and encode it in isolation. Its features can therefore incorporate the surrounding image through attention.

The context branch sees only the permitted visible patches. The predictor is told where to predict, but it does not receive the target content. Otherwise, we could create an easy copying task.

The prediction loss trains the context encoder and predictor through backpropagation. It does not backpropagate through the target encoder. Instead, we update the target encoder using a moving average of the context encoder's parameters.

There are therefore two distinct mechanisms: gradients improve the predicting branch, and parameter averaging updates the branch that defines the targets. The target is learned and changes over time; it is not an externally supplied biological or semantic label.

**Transition:** “Let us make the patch selection concrete before writing the loss.”

**Sources:** [S02, §3 and Figure 3](https://arxiv.org/pdf/2301.08243); [S16: released training code](https://github.com/facebookresearch/ijepa/blob/52c1ae95d05f743e000e8f10a1f3a79b10cff048/src/train.py).

## Slide 5 — A worked example: what information reaches each branch?

**Time:** 2.5 minutes. **Purpose:** show that masking is part of the task definition.

**On screen:** original 4 × 4 grid labeled 0–15; target positions `{5,6,9,10}`; remaining positions are context in this deliberately simplified example. Three stages: “select input context”, “encode full image for teacher”, “compare matching target positions”.

**Visual instructions:** use `assets/masking_example.svg`. All positions are zero-based. This one-target teaching example is not the published four-target masking recipe. For the paper recipe, add a small text callout: “Multiple sizeable target blocks; broad candidate context; remove target overlap”. Do not represent candidate context size as final visible size.

**Spoken script:**

Here is a deliberately small example with sixteen patches. We hide the central four, at positions five, six, nine, and ten. The context encoder receives the other twelve patches together with their positions.

Suppose each output feature has eight dimensions. For one image, the context features have shape twelve by eight. The target encoder processes all sixteen patches, producing sixteen by eight features. We select the four target positions, leaving a four by eight target tensor.

The predictor receives the twelve context features and four positional queries. Its output is also four by eight, so every predicted feature vector can be compared with its corresponding target vector.

[Point to one position and trace it through both outputs.]

Those numbers are a teaching example, not the model size in the paper. The important feature is the separation of information: target position is available to the predictor; hidden target content is not.

The actual I-JEPA recipe uses multiple target blocks. Their size and the remaining context change the problem the model must solve. If a target is tiny, local texture may suffice. If it is very large and the context uninformative, prediction may become too ambiguous. The masking design is therefore an inductive bias, not just a way to save computation.

For a genome, the analogous decisions would include tokenization, span length, and whether the remaining context contains the regulatory information needed for the task. There is no guarantee that the same masking recipe transfers unchanged.

**Transition:** “Once these tensors are aligned, the training objective is easy to state.”

**Sources:** [S02, §3, Figure 4, and masking ablations](https://arxiv.org/pdf/2301.08243). The sixteen-patch tensors are an original illustrative construction.

## Slide 6 — The objective and one training step

**Time:** 3 minutes. **Purpose:** explain the three central equations with controlled notation.

**On screen:** reveal these equations sequentially, not all at once:

\[
\hat h_{T_k}=g_\phi(f_\theta(x_C),p_{T_k}),\qquad h_{T_k}=\operatorname{sg}(f_{\bar\theta}(x)_{T_k})
\]

\[
\mathcal L_{\rm teach}=\frac1K\sum_{k=1}^{K}\frac1{|T_k|}\sum_{j\in T_k}\|\hat h_j-h_j\|_2^2
\]

\[
\bar\theta\leftarrow\tau\bar\theta+(1-\tau)\theta
\]

**Equation labels:** “Squared-distance teaching form, following the paper; explicit per-block normalization added here.” Footer: “Released implementation: normalized teacher features + Smooth L1 loss.” `sg` = stop-gradient; `p` = position queries; `τ` = EMA coefficient.

**Visual instructions:** keep the architecture thumbnail visible. Gradient arrows illuminate context encoder and predictor; the EMA arrow illuminates separately. Put the full pseudocode in speaker notes or backup B2, not as another dense main-slide panel.

**Spoken script:**

The first line describes the prediction and its target. On the left, we encode the visible context and predict features at specified positions. On the right, we encode the complete image, select those same positions, and stop the gradient.

The second line averages the discrepancy between predicted and target vectors. In this teaching equation, I use squared Euclidean distance and explicitly average over target blocks and patches. The paper presents a squared-distance objective. The released training code instead uses Smooth L1 with normalized teacher features, so this equation explains the paper-level mechanism rather than claiming to reproduce every implementation detail.

Take one target vector equal to one, zero, and a prediction equal to zero point eight, zero point two. Their squared distance is zero point zero eight. The gradient with respect to the prediction points toward reducing that discrepancy. Through the chain rule, that signal updates the predictor and the context encoder.

Stop-gradient means the teacher receives no derivative from this comparison. It does not mean the teacher never changes. After the optimizer step, we update its parameters using the third equation.

For example, if the old teacher parameter is two, the updated context parameter is three, and tau is zero point nine, the new teacher parameter is two point one. That is a toy coefficient chosen for arithmetic; practical schedules use their own settings.

So one iteration is: sample masks, compute the target without gradients, predict from the context, evaluate the loss, update the online parameters, then update the teacher by averaging.

A natural objection follows: since the targets are learned, why do all these networks not agree on a useless constant?

**Transition:** the final sentence opens slide 7.

**Sources:** [S02, §3](https://arxiv.org/pdf/2301.08243); [S16, `forward_target`, `loss_fn`, and momentum update](https://github.com/facebookresearch/ijepa/blob/52c1ae95d05f743e000e8f10a1f3a79b10cff048/src/train.py). Arithmetic is illustrative; it is not a trained-model result.

## Slide 7 — Collapse: low prediction error can mean no information

**Time:** 2 minutes. **Purpose:** separate optimizing agreement from learning useful representations.

**On screen:** three distinct inputs map to the same vector `c`; predictor outputs `c`; loss is zero. Beside this, show a spread of embeddings with label “Variation is necessary, but not sufficient, for usefulness.”

**Visual instructions:** depict constant outputs as identical points. Avoid suggesting that two visibly separated clusters prove biological meaning. List “asymmetry, target updates, masking, optimization” under I-JEPA and “explicit variance/covariance terms” under the genomic extension.

**Spoken script:**

Suppose both encoders output the same constant vector for every input, and the predictor outputs that constant too. The prediction error is zero. Yet the representation cannot distinguish a bird from a car, or one DNA sequence from another.

This is representation collapse. It shows why minimizing prediction error alone is not a sufficient definition of successful learning when the target is also learned.

I-JEPA uses an asymmetric training system, including the predictor, stopped target gradients, and a moving teacher. Together with the masking and optimization recipe, this works empirically. We should not turn that observation into a theorem that EMA or stop-gradient alone makes collapse impossible. Our constant example still exists algebraically.

Another family of methods adds explicit constraints on the embedding distribution. VICReg includes a variance term that penalizes dimensions with too little variation across a batch, and a covariance term that discourages redundant dimensions. We will see these ingredients in JEPA-DNA.

Even then, non-collapse is only a minimum requirement. A model can encode scanner identity, species composition, or batch effects and remain highly variable. Useful biology has to be demonstrated through appropriate downstream tasks and controls.

**Transition:** “That is why we now move from the training loss to the experimental evidence.”

**Sources:** [S02, §2–3](https://arxiv.org/pdf/2301.08243); [S09: VICReg](https://arxiv.org/abs/2105.04906); [S11: SimSiam](https://arxiv.org/abs/2011.10566). The counterexample and biological confounders are explanatory analysis.

## Slide 8 — What does I-JEPA demonstrate?

**Time:** 2 minutes. **Purpose:** read a result under its actual evaluation protocol.

**On screen:** two paired values, “ImageNet-1K linear evaluation, ViT-H/14”: I-JEPA 79.3% at 300 epochs; MAE 77.2% at 1,600 epochs. Show epochs beside values. Footer: “Reported configurations; not a universal compute-controlled comparison.” Add “Masking and prediction-target ablations support design choices.”

**Visual instructions:** use `assets/ijepa_results.svg` or the corresponding CSV. Preserve the benchmark, backbone, metric, and training-duration labels. Do not merge the paper's linear-probe and fine-tuning tables.

**Spoken script:**

The first question is how the representation is evaluated. In linear probing, we freeze the pretrained encoder and train a linear classifier using labeled examples. This asks how easily the task information can be extracted by that restricted readout. It is not label-free evaluation.

For the ViT-Huge configuration shown here, the paper reports seventy-nine point three percent ImageNet top-one accuracy for I-JEPA, compared with seventy-seven point two for MAE. The listed pretraining schedules are three hundred and sixteen hundred epochs respectively.

This is useful evidence that the I-JEPA recipe learns accessible image features. It is not evidence of universal superiority: these are particular recipes, and training epochs are not a complete measure of computational cost.

The paper also changes masking strategies and the space in which targets are predicted. Those ablations support the claim that the learning task itself matters. We should still inspect what else changes between each pair of conditions.

One easily missed detail: the reported I-JEPA evaluation uses the moving-average target encoder and average pooling, without a class token. “Discard the teacher and evaluate the student” is therefore not an accurate universal summary of this paper.

**Transition:** “Useful image features are one milestone. Temporal prediction and planning add further requirements.”

**Sources:** [S02, Table 1, Tables 6–7, Appendix A.1](https://arxiv.org/pdf/2301.08243); [S12: MAE](https://arxiv.org/abs/2111.06377).

## Slide 9 — From representation learning to a world model

**Time:** 2 minutes. **Purpose:** connect the technical example to LeCun's vision without conflating different achievements.

**On screen:** “I-JEPA: image features” → “V-JEPA: video features” → “V-JEPA 2-AC: action-conditioned prediction + planning”. Small inset:

\[
\hat z_{t+1}=F(z_{\le t},a_t)
\]

Label this a **conceptual dynamics equation**, not the exact architecture. Add “V-JEPA 2.1 (2026): further dense-feature developments; details in backup.”

**Visual instructions:** the final arrow must show action/state data entering post-training and a separate planner choosing actions. “Zero-shot” must be qualified as deployment transfer after action-conditioned training.

**Spoken script:**

LeCun's broader proposal includes world models that predict at different levels of abstraction and support planning. I-JEPA is an image representation learner within that research direction; it is not the complete proposed autonomous system.

V-JEPA extends feature prediction to video. But reconstructing masked video features can use context on both sides of a missing region. We should not automatically call every such objective causal forecasting.

For control, the model needs to predict how the state changes under an action. V-JEPA two introduces an action-conditioned model after large-scale visual pretraining. Its robot experiments use additional interaction data containing video and robot state information.

The authors describe deployment in new environments as zero-shot. That does not mean the system learned control without action experience. A planner evaluates candidate actions using the learned dynamics and a goal, then executes and replans.

The distinction matters for my clinical interests. A model that predicts a patient's future record from observed history has not thereby learned what would happen under a different treatment. That requires additional assumptions and evidence about interventions and confounding.

There are subsequent developments, including V-JEPA two point one, but the key distinction for today is between useful representations, temporal predictions, and action-conditioned planning.

**Transition:** “We can now ask what carries over when the observations are DNA sequences.”

**Sources:** [S01](https://openreview.net/pdf?id=BZ5a1r-kVsf); [S03: V-JEPA](https://arxiv.org/abs/2404.08471); [S04: V-JEPA 2, §3–4](https://arxiv.org/abs/2506.09985); [S05: V-JEPA 2.1](https://arxiv.org/abs/2603.14482). The clinical distinction is methodological analysis, not a claim of validated treatment simulation.

## Slide 10 — JEPA-DNA: a hybrid objective for existing genomic models

**Time:** 2.5 minutes. **Purpose:** explain the actual biological adaptation, not a fictional nucleotide version of I-JEPA.

**On screen:** visible label “PREPRINT · version 3 · 11 August 2026”. Starting point: pretrained genomic backbone. Show a masked-sequence context branch, unmasked target branch, predictor and aggregation, alongside a retained language-model objective.

\[
\mathcal L=\lambda_{\rm LM}\mathcal L_{\rm LM}+\lambda_{\rm pred}\mathcal L_{\rm cosine}+\lambda_{\rm var}\mathcal L_{\rm var}+\lambda_{\rm cov}\mathcal L_{\rm cov}
\]

**Visual instructions:** use `assets/dna_objective.svg` as a high-level objective diagram, not a complete implementation graph. Do not depict the genomic latent loss as a residue-by-residue image-style loss: the paper compares aggregated global sequence representations. Label backbone-specific pooling/predictor choices; details in B5.

**Spoken script:**

JEPA-DNA is particularly relevant to this lab because it starts with existing genomic foundation models. The version we are discussing is a preprint, and its setting is continual training rather than learning a new model from scratch.

It retains the model's language objective: masked-token prediction or next-token prediction, depending on the backbone. It adds a branch that predicts an aggregated representation of the unmasked sequence from the masked context.

This is a meaningful difference from the I-JEPA example. There we compared target patch features. Here the latent objective operates on global sequence representations, with aggregation and predictor choices adapted to the backbone.

The equation contains four contributions. The language loss preserves pressure to recover tokens. A cosine loss aligns predicted and teacher sequence representations. Variance and covariance terms encourage a representation that remains diverse rather than collapsing or becoming unnecessarily redundant.

The recipe also includes training stages and a scheduled masking strategy. The paper evaluates three quite different backbones: DNABERT-two, Nucleotide Transformer version three, and HyenaDNA. That illustrates how a learning objective can be added to different architectures.

We should be careful with the paper's language about biological semantics. The target is produced by a learned model; it is not a direct measurement of regulatory function. Downstream experiments test whether these representations are useful for selected tasks. They do not automatically establish a mechanistic model of the genome.

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
