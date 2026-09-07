# JEPA journal club: source evidence ledger

Verified through **7 September 2026**, for the 8 September presentation. This is the evidence companion to the teaching script, not an assertion that every cited method has been reproduced. Source identifiers are stable across the handoff package. PDF page numbers below are one-based file pages.

## How to use the evidence

Distinguish four levels of statement: **definition** describes a computation; **reported result** belongs to a particular paper, dataset and evaluation; **interpretation** explains a possible mechanism; **proposal** describes an experiment still to perform. Author language such as “world model,” “semantic,” “grounding” or “understanding” is not an additional measurement. A diagram can explain the mechanism while the accompanying result supports only a narrower claim.

Use the selected numerical extracts below as chart inputs. Retain the dataset, evaluation protocol, backbone and training duration in captions. Never compare a linear-probe score with a fine-tuned score as though only the pretraining objective changed. All values are paper-reported; no training run or statistical reanalysis was performed for this package.

Full-text scrutiny concentrated on [S02] and [S06]. Original PDFs were downloaded and selected pages rendered locally. Other sources support definitions, chronology and brief outlook statements; their benchmarks have not received the same audit. [S07] remains abstract-only. Failure to retrieve a paper does not make its claim false; it limits what this presentation can responsibly explain.

## Source register

### [S01] LeCun: conceptual proposal

Yann LeCun, *A Path Towards Autonomous Machine Intelligence*, version 0.9.2, 27 June 2022. [Primary OpenReview record](https://openreview.net/forum?id=BZ5a1r-kVsf); [primary PDF](https://openreview.net/pdf?id=BZ5a1r-kVsf).

**Status/access:** position paper; primary PDF search indexing was accessible, but direct retrieval encountered browser verification/403. The complete document was not freshly audited. Its contribution is a research programme combining predictive representations, hierarchical models and planning. The document's own positioning separates a proposed route to intelligence from an experimental demonstration. Use it to motivate questions, not to claim a solved general agent architecture. Do not invent a journal volume from malformed bibliography entries that treat its page count as a volume.

### [S02] I-JEPA

Mahmoud Assran et al., *Self-Supervised Learning from Images with a Joint-Embedding Predictive Architecture*. [CVPR 2023 proceedings record](https://openaccess.thecvf.com/content/CVPR2023/html/Assran_Self-Supervised_Learning_From_Images_With_a_Joint-Embedding_Predictive_Architecture_CVPR_2023_paper.html); [audited PDF, arXiv v3](https://arxiv.org/pdf/2301.08243v3). First submitted 19 January 2023; v3 dated 13 April 2023. The proceedings establish CVPR, despite an inconsistent conference comment in the arXiv record.

**Core anchors:** §3 specifies patchwise latent prediction; the teacher processes the complete image before target positions are selected. Appendix A.1 evaluates the EMA teacher, with average pooling and no CLS token. Relevant numerical extracts appear below. The paper's squared-L2 equation differs from released training code [S16].

### [S03] V-JEPA

Adrien Bardes et al., *Revisiting Feature Prediction for Learning Visual Representations from Video*. [arXiv v1](https://arxiv.org/abs/2404.08471v1), dated 15 February 2024; [author's OpenReview publication record](https://openreview.net/profile?id=~Adrien_Bardes1) lists acceptance by TMLR in 2024.

Extends feature prediction to video. Its reported frozen-backbone evaluations test whether learned features support downstream recognition, not whether an autonomous agent can choose interventions. The pretraining objective does not require text, explicit negative pairs or pixel reconstruction. Avoid calling every masked-video prediction a causal future rollout: the context/target sampling and inference task matter. This source provides the bridge from images to time, with limited room for benchmark detail in the main talk.

### [S04] V-JEPA 2

Mido Assran et al., *V-JEPA 2: Self-Supervised Video Models Enable Understanding, Prediction and Planning*. [Primary arXiv record and paper](https://arxiv.org/abs/2506.09985v1), 11 June 2025. The retrieved record has one version; no conference acceptance is asserted here.

The work combines large-scale action-free visual pretraining with action-conditioned post-training for V-JEPA 2-AC. The authors report less than 62 hours of DROID interaction videos for that latter stage, then transfer to Franka arms in two laboratories. “Zero-shot” concerns those deployment environments and tasks; it does not mean that the model learned control without prior robot actions. An image goal and a planner are additional components. Attribute reported robot behaviour to the complete system, not to an image encoder alone.

### [S05] V-JEPA 2.1

Lorenzo Mur-Labadia et al., *V-JEPA 2.1: Unlocking Dense Features in Video Self-Supervised Learning*. [Primary record](https://arxiv.org/abs/2603.14482v3): first submitted 15 March 2026, v3 dated 11 June 2026. Treat the accessed item as a preprint; no peer-reviewed venue was established in this audit.

The abstract describes supervision for both visible and masked tokens, objectives at intermediate layers, and joint image/video training. This supports a brief statement that the family continues to evolve toward dense visual representations. It does not establish that the original I-JEPA implementation has these features. Keep any named performance gain tied to this model version and its evaluation, or omit the number. Its figure license also differs from several earlier family members.

### [S06] JEPA-DNA

Ariel Larey et al., *JEPA-DNA: Grounding Genomic Foundation Models through Joint-Embedding Predictive Architectures*. [Audited v3 PDF](https://arxiv.org/pdf/2602.17162v3); [HTML](https://arxiv.org/html/2602.17162v3). Preprint: first submitted 19 February 2026; v3 dated 11 August 2026.

**Method anchors:** §3.3 combines token loss, latent prediction, variance and covariance penalties. §4.1/A.2 distinguish a tokenwise Transformer predictor from NTv3's MLP on pooled embeddings. §4.4 uses the teacher at inference. Appendix A.2 selects checkpoints using GUE Splice Site validation performance. Tables 1/4 and audit limitations are recorded below. This is continual training, not a verified from-scratch genomic JEPA recipe.

### [S07] ProtJEPA

Vaibhava Lakshmi Ravideshik, Jinha Kim and Manolis Kellis, *ProtJEPA: A Multimodal Joint-Embedding Predictive Architecture for Protein Biological World Modeling with Multi-Teacher Modality-Attentive Fusion*. [Primary bioRxiv v1](https://www.biorxiv.org/content/10.64898/2026.08.03.742606v1), DOI 10.64898/2026.08.03.742606, **posted 9 August 2026**. The date embedded in the DOI is not the posting date.

**Access boundary:** the primary indexed abstract was read; page/PDF retrieval returned 403/429. No full-method or figure audit succeeded. Qualitative claim permitted: authors train a sequence-only student against multimodal protein representations, including structural and functional information. Do not place numerical performance, split-independence or collapse-prevention claims on a main result slide from this audit. Protein annotation and teacher provenance require close reading before comparison with sequence-only self-supervision.

### [S08] Clin-JEPA

Yixuan Yang et al., *Clin-JEPA: A Multi-Phase Co-Training Framework for Joint-Embedding Predictive Pretraining on EHR Patient Trajectories*. [Primary arXiv v4](https://arxiv.org/abs/2605.10840v4): first submitted 11 May 2026; v4 dated 4 July 2026. [PMC record](https://pmc.ncbi.nlm.nih.gov/articles/PMC13193276/) explicitly identifies it as a preprint despite indexing in PMC/PubMed.

The work combines an adapted language-model encoder with a retained latent trajectory predictor and reports MIMIC-IV ICU evaluations. It offers a relevant clinical outlook, particularly for distinguishing representation learning from sequential prediction. Retrospective prediction does not establish counterfactual treatment validity, policy safety, transportability or clinical benefit. Avoid describing its latent rollouts as validated patient digital twins. No clinical recommendation follows from the cited experiment.

### [S09] VICReg

Adrien Bardes, Jean Ponce and Yann LeCun, *VICReg: Variance-Invariance-Covariance Regularization for Self-Supervised Learning*. [Primary record](https://arxiv.org/abs/2105.04906v3): first submitted 11 May 2021, v3 dated 28 January 2022; record confirms ICLR 2022 acceptance.

Separates agreement, variance preservation and decorrelation. The variance term explicitly penalizes inadequate spread; the covariance term discourages redundant dimensions. These are useful geometric constraints, not biological supervision. Zero cross-covariance is not general statistical independence. For the talk, use this source to explain what an additional anti-collapse regularizer measures, then identify which components the biological implementation actually borrows. Do not label I-JEPA itself as VICReg training.

### [S10] BYOL

Jean-Bastien Grill et al., *Bootstrap Your Own Latent: A New Approach to Self-Supervised Learning*. [NeurIPS 2020 proceedings](https://papers.nips.cc/paper/2020/hash/f3ada80d5c4ee70142b17b8192b2958e-Abstract.html).

Learns through prediction between augmented image views, with an online network and a moving-average target network. It establishes that explicit negative samples are not a universal requirement for useful learned representations. It also supplies an important historical predecessor: JEPA did not invent every teacher/student or predictor ingredient. Explain the distinction between view alignment and location-conditioned target prediction instead of presenting a sharp chronological replacement of one entire field by another.

### [S11] SimSiam

Xinlei Chen and Kaiming He, *Exploring Simple Siamese Representation Learning*. [CVPR 2021 paper](https://openaccess.thecvf.com/content/CVPR2021/papers/Chen_Exploring_Simple_Siamese_Representation_Learning_CVPR_2021_paper.pdf); [arXiv v1](https://arxiv.org/abs/2011.10566v1), 20 November 2020.

Reports useful representations without explicit negatives, large batches or an EMA encoder. Its experiments assign an important role to stop-gradient while acknowledging collapsed solutions in the objective and architecture. This is a direct antidote to saying “EMA is required by all noncontrastive methods” or “stop-gradient removes the constant solution mathematically.” It supports a discussion of training dynamics, not a universal guarantee across encoders, optimizers and domains.

### [S12] MAE

Kaiming He et al., *Masked Autoencoders Are Scalable Vision Learners*. [CVPR 2022 proceedings](https://openaccess.thecvf.com/content/CVPR2022/html/He_Masked_Autoencoders_Are_Scalable_Vision_Learners_CVPR_2022_paper.html); [preprint](https://arxiv.org/abs/2111.06377), initially 11 November 2021.

The encoder processes visible patches; a decoder reconstructs masked pixels. The learned encoder still provides a representation useful downstream. Consequently, contrast MAE and I-JEPA by the prediction target and training configuration, not by “MAE has no latent space.” MAE's strong fine-tuning results are a reason to specify the evaluation protocol before claiming superiority of one objective. Its masking ratio should be identified as its experimental recipe, not a general requirement of masked learning.

### [S13] SimCLR

Ting Chen, Simon Kornblith, Mohammad Norouzi and Geoffrey Hinton, *A Simple Framework for Contrastive Learning of Visual Representations*. [ICML 2020 proceedings](https://proceedings.mlr.press/v119/chen20j.html).

A primary reference for positive/negative pairs, augmentation choices and a nonlinear projection head. A negative pair in the learning objective means a sampled contrastive relationship, not necessarily a biological contradiction. When transferring the intuition to proteins, two distinct sequences may share function or evolutionary history; treating them as interchangeable generic negatives becomes a design decision. That biological warning is an interpretation, not an experiment reported by SimCLR.

### [S14] DINO

Mathilde Caron et al., *Emerging Properties in Self-Supervised Vision Transformers*. [ICCV 2021 proceedings](https://openaccess.thecvf.com/content/ICCV2021/html/Caron_Emerging_Properties_in_Self-Supervised_Vision_Transformers_ICCV_2021_paper.html).

Self-distillation supplies another comparison with teacher/student learning and strong visual representations. It helps explain why matching features is not synonymous with JEPA's particular masking and prediction setup. The paper studies representation properties, including attention-related semantic structure; attention visualizations should not be treated as causal explanations of a downstream decision. Use DINO as a conceptual comparator, and do not silently replace its original results with DINOv2 or later models.

### [S15] Transformer

Ashish Vaswani et al., *Attention Is All You Need*. [NIPS 2017 proceedings](https://papers.nips.cc/paper_files/paper/2017/hash/3f5ee243547dee91fbd053c1c4a845aa-Abstract.html); [arXiv](https://arxiv.org/abs/1706.03762).

Provides the architecture-level reference for attention. JEPA describes a learning arrangement/objective family; a Transformer can implement its encoders and predictor. Thus “JEPA versus Transformer” compares different categories. Likewise, a change from token-space to latent-space loss does not automatically eliminate attention complexity. The original Transformer paper concerns machine translation; no protein, genomic or clinical outcome should be attributed to it.

### [S16] Official I-JEPA implementation snapshot

[facebookresearch/ijepa, src/train.py](https://github.com/facebookresearch/ijepa/blob/52c1ae95d05f743e000e8f10a1f3a79b10cff048/src/train.py#L294-L313), commit `52c1ae95d05f743e000e8f10a1f3a79b10cff048`, file-change date 13 June 2023, resolved through GitHub's commits API.

Lines 296/298 compute targets without gradients and normalize over the feature dimension; line 311 uses `F.smooth_l1_loss`. This is a verified difference from the paper equation, not evidence of an author error or of which exact checkpoint used which unpublished recipe. Label teaching pseudocode as simplified, and label an implementation demonstration with its pinned source. No reproduction claim is made. GitHub indicates that the repository was archived in August 2024.

### [S17] BERT: representation learning with MLM

Jacob Devlin et al., *BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding*. [NAACL 2019 proceedings](https://aclanthology.org/N19-1423/), DOI 10.18653/v1/N19-1423.

Supports the essential correction that masked-language objectives already train contextual representations from unlabeled inputs. A token-prediction head does not imply that internal features lack abstraction. JEPA changes where part of the learning signal is applied and how its target is constructed. Whether the resulting features retain what a biological task needs is an empirical question. A genetics audience should be allowed to compare the proposed objective with its existing representation models on those terms.

### [S18] LeJEPA: supplementary outlook only

Randall Balestriero and Yann LeCun, *LeJEPA: Provable and Scalable Self-Supervised Learning Without the Heuristics*. [Primary arXiv v3 record](https://arxiv.org/abs/2511.08544v3): first submitted 11 November 2025, v3 dated 14 November 2025. The primary abstract was checked on 7 September 2026; no venue or proof audit is asserted here.

The abstract introduces SIGReg, a regularizer targeting an isotropic Gaussian embedding distribution, and describes a formulation without the I-JEPA teacher/stop-gradient recipe. This supports the limited outlook in backup B10. Claims of theoretical optimality depend on the paper's assumptions and are not a proof of universal biological usefulness. No LeJEPA benchmark numbers or theorem derivations are included in this package.

## Copyable chart data and provenance

### I-JEPA: accuracy and controls

Source [S02], Table 1, PDF p.5. ImageNet-1K linear evaluation; top-1 is percent. Selected rows, not a complete leaderboard:

```csv
method,backbone,pretraining_epochs,top1_percent
MAE,ViT-L/16,1600,76.0
I-JEPA,ViT-L/16,600,77.5
MAE,ViT-H/14,1600,77.2
I-JEPA,ViT-H/14,300,79.3
I-JEPA,ViT-H/16_at_448px,300,81.1
```

Source [S02], Table 6, p.8: ViT-B/16, 300 epochs, **linear evaluation using 1% labels**. The context fractions differ; this is a recipe ablation.

```csv
mask_strategy,context_fraction_average,top1_percent
multi-block,0.25,54.2
rasterized,0.25,15.5
block,0.40,20.2
random,0.40,17.6
```

Source [S02], Table 7, p.8: ViT-L/16, 1%-label linear evaluation. Different durations must remain visible:

```csv
prediction_target,pretraining_epochs,top1_percent
teacher_embedding,500,66.9
pixels,800,40.7
```

### JEPA-DNA: all DNABERT-2 Table 1 AUROC entries

Source [S06], Table 1, p.7. Frozen-feature linear probing. Differences below are computed subtraction, not paper-reported confidence intervals.

```csv
task,original_DNABERT2,jepa_dna,absolute_AUROC_difference
TF_binding,0.788,0.839,0.051
Promoter,0.884,0.928,0.044
Splice_site,0.653,0.705,0.052
Coding_pathogenicity,0.624,0.610,-0.014
Expression_effect,0.674,0.689,0.015
Common_vs_rare,0.505,0.504,-0.001
meQTL,0.623,0.645,0.022
sQTL,0.585,0.577,-0.008
Causal_eQTL,0.697,0.711,0.014
```

Source [S06], Table 4, p.9. “Expression” here is **BEND Expression Effect**, unlike the Table 1 expression row.

```csv
continued_training_configuration,promoter_AUROC,splice_AUROC,BEND_expression_AUROC
original_checkpoint,0.884,0.653,0.543
MLM,0.929,0.674,0.532
MLM_JEPA,0.927,0.669,0.529
MLM_JEPA_scheduled_masks,0.925,0.687,0.519
MLM_JEPA_VICReg,0.928,0.689,0.565
MLM_JEPA_VICReg_scheduled_masks,0.928,0.705,0.574
```

**Audit limits:** Table 4 is a continued-training control, not established equal FLOPs/wall time for every variant. Table 6's five seeds concern linear probing; independent pretraining uncertainty is not established. Reported “data parity” does not itself prove contamination-free evaluation. Architecture-level exceptions and task-level regressions matter. [S06]

## Figure locator and visual-verification record

“Viewed” means a local PNG rendered from the cited PDF was inspected, not that a finished slide crop has passed QA. Figures need a readable credit; redrawings should identify their source and simplifications.

| Source | Object | PDF page | Verification | Use constraint |
|---|---|---:|---|---|
| S02 | Figure 2 | 2 | Viewed | Architecture taxonomy; distinguish objective from backbone |
| S02 | Figure 3 | 3 | Viewed | Preserve context, teacher and location-conditioned predictor |
| S02 | Figure 4 | 4 | Viewed | Teacher target selection occurs after full-image encoding |
| S02 | Tables 1/2 | 5 | Viewed | Table 2 is not uniformly a frozen linear probe |
| S02 | Figure 5 | 7 | Locator/text checked | Compute comparison needs protocol labels |
| S02 | Figure 6; Tables 6/7 | 8 | Viewed | Figure 6 uses an added generative decoder |
| S06 | Figure 1 | 4 | Viewed | Full hybrid recipe; some branches are backbone-specific |
| S06 | Table 1 | 7 | Viewed | Retain negative as well as positive differences |
| S06 | Table 3 | 8 | Locator/text checked | Zero-shot scores are not diagnostic operating points |
| S06 | Tables 4/5 | 9 | Viewed | Component ablation and predictor ablation differ |
| S06 | Figure 3 | 17 | Viewed | Explicitly the CLS/DNABERT-2 configuration |
| S07 | Any figure | Unknown | Not verified | Do not invent a figure number or redraw unseen details |

## Corrections that must survive slide generation

1. **No semantic guarantee.** A useful embedding must be tested against a defined task; assigning it the symbol `z` provides no biological meaning. [S02, S06, S17]
2. **No universal collapse theorem.** Constant matching embeddings remain a possible zero-prediction-loss configuration. Stop-gradient changes updates; EMA slows target drift. This algebraic observation is distinct from successful training dynamics. [S09-S11]
3. **No universal variance claim.** Inadequate spread and redundant coordinates are different problems; decorrelation is weaker than independence. [S09]
4. **Preserve paper/code identity.** An equation from [S02] is not a verbatim reproduction of [S16].
5. **Preserve training/inference identity.** EMA teachers need not be discarded; both main case papers use teacher representations for evaluation. [S02, S06]
6. **Avoid universal tokenizer claims.** A DNA string, a token sequence and a residue sequence are different objects. The loss target and aggregation operation should be named. [S06, S17]
7. **Do not call pooled prediction reconstruction of each masked nucleotide.** The biological worked example's global representation loss complements token prediction. [S06]
8. **Do not inflate outlook evidence.** Protein multimodal learning is not automatically sequence-only pretraining, and retrospective EHR results are not treatment-effect identification. [S07, S08]
9. **Do not erase action experience.** Robot transfer follows action-conditioned learning. [S04]
10. **Do not mistake a decoder visualization for native JEPA image generation.** A separate decoder is a probe of representations. [S02]

## Claim strength and scientific discussion

**Strong, narrow claims:** the referenced loss definitions; existence of the implemented branches; the transcribed table entries; the actual posting/version dates. These can be stated directly with citations. **Moderate claims:** that the reported recipe improves selected benchmark representations, or that a particular component is useful within the examined ablation. **Unestablished claims:** universal superiority over language models; improved phylogenetic reconstruction; reliable mechanism discovery; variant-level clinical usefulness; guaranteed preservation of rare disease signals. The last group is discussion material, not conclusions.

For a proposed lab experiment, define what information may be discarded before selecting masking or pooling. If the endpoint depends on one nucleotide, invariance to that nucleotide is harmful even when average retrieval improves. That is a task-design argument, not proof that JEPA necessarily discards the nucleotide. A fair experiment would compare original weights, additional native-objective training, and the full new recipe; report both data exposure and compute; separate checkpoint selection from held-out testing; and measure variation across training runs. Homology-aware or locus-aware splits would be chosen according to the biological unit of generalization. These are proposed controls, not claims that the cited authors performed or omitted a particular leakage analysis.

## Reuse, provenance and remaining limits

Licenses were inspected on source records or repository license files, not inferred from open access. [S03], [S04], [S06] and [S08] arXiv records link **CC BY 4.0**. [S05] links **CC BY-NC-ND 4.0**. [S02]'s arXiv version uses the **arXiv nonexclusive distribution license**; its code separately uses [CC BY-NC 4.0](https://github.com/facebookresearch/ijepa/blob/main/LICENSE). [S06]'s code separately uses [Apache 2.0](https://github.com/NVIDIA-Digital-Bio/JEPA-DNA/blob/main/LICENSE). Other figure licenses were not audited. Paper, repository and model-weight licenses must not be conflated. This record is provenance, not a blanket legal clearance for all reuse.

Downloaded audit PDFs were fingerprinted:

```text
S02 arXiv2301.08243v3 SHA256 eddbdc093eb4d48662bcf4fbd1c6735ccd606205cc9070977ce317d68aff3941
S06 arXiv2602.17162v3 SHA256 47e96c602b636ffc558f0381550c512d101a5ed527bc640b3c3f6eae2ef2b643
```

The literature search was bounded, not systematic. No primary JEPA-specific phylogenetic reconstruction study was established. This is not evidence that none exists. No source metrics beyond the audited extracts should be added to charts without a fresh check of their table, denominator and protocol. No private biological or clinical data were accessed.
