# Backup slides, difficult questions, and rehearsal

These ten backup slides are optional discussion material after the fourteen-slide talk. They are not part of the 28-minute scripted sequence. Each has a short speaking answer that can be expanded using `02_TECHNICAL_GUIDE.md`. Source IDs resolve in `04_SOURCE_EVIDENCE.md`.

## B1 — Tensor shapes and target visibility

**Use when asked:** “What exactly enters the predictor?”

**On screen / visual:** the 4 × 4 toy grid from slide 5 plus the tensor table from guide §4. Color the four selected target locations consistently. Context: `B×12×8`; teacher before selection: `B×16×8`; prediction and selected target: `B×4×8`. Label every dimension illustrative.

**Speaking answer:** “The predictor receives the visible context features and queries identifying the target positions. It does not receive the teacher's target vectors. In this example the teacher encodes sixteen positions, while the context encoder only processes twelve. We select four teacher output positions, then align four predictor outputs with them. The order matters: hiding context outputs after full-image attention would already let target information influence the input representation. The teacher's complete view is allowed because it defines the training target; the predictor's complete view would change the task.”

**Source:** [S02 §3](https://arxiv.org/pdf/2301.08243). Toy geometry is original.

## B2 — Paper equation versus code

**Use when asked:** “Is that the exact implementation?”

**On screen / visual:** two labeled panels: paper-level squared distance and released-code Smooth L1, with teacher feature normalization. Show the six-step loop: masks → teacher → context/predictor → loss → online optimizer → EMA. Copy the educational pseudocode from guide §5 into notes, not as a full-page screenshot.

**Speaking answer:** “No, the main equation is a teaching form following the paper. It adds explicit averaging for clarity. The released code normalizes teacher features and uses Smooth L1. Those losses have different behavior for large residuals and different reduction conventions. I pinned the code reference so we can distinguish the source implementation from an illustrative explanation. This package is an explanation and source audit; it is not a reproduction of the published training runs.”

**Source:** [S02](https://arxiv.org/pdf/2301.08243); [S16 pinned implementation](https://github.com/facebookresearch/ijepa/blob/52c1ae95d05f743e000e8f10a1f3a79b10cff048/src/train.py#L294-L313).

## B3 — Does stop-gradient prove non-collapse?

**Use when asked:** “Why cannot the teacher and student agree on a constant?”

**On screen / visual:** `f(x)=c`, `g(c,p)=c`, `L=0`; below this, the variance and covariance penalties from guide §6. Separate captions: “A possible solution” and “What training tends to find”.

**Speaking answer:** “They can agree on a constant algebraically. Stop-gradient and EMA change the update dynamics; they do not delete that constant solution. The empirical question is whether the full recipe avoids it in practice. Explicit distribution regularization provides another way to discourage collapse. But a varied representation can still encode irrelevant information. I would therefore inspect feature statistics and held-out task performance, rather than infer useful learning from prediction loss alone.”

**Source:** [S09 VICReg](https://arxiv.org/abs/2105.04906); [S11 SimSiam](https://arxiv.org/abs/2011.10566). Counterexample is original analysis.

## B4 — I-JEPA ablations and evaluation boundaries

**Use when asked:** “Is the target space or the mask doing the work?”

**On screen / visual:** two small tables, never pooled into one axis:

| Target ablation: ViT-L/16, 1%-label linear evaluation | Epochs | Top-1 |
|---|---:|---:|
| Teacher representation | 500 | 66.9% |
| Pixels | 800 | 40.7% |

| Mask ablation: ViT-B/16, 300 epochs, 1%-label linear evaluation | Average context fraction | Top-1 |
|---|---:|---:|
| Multi-block | 0.25 | 54.2% |
| Rasterized | 0.25 | 15.5% |
| Single block | 0.40 | 20.2% |
| Random | 0.40 | 17.6% |

**Speaking answer:** “The paper supplies evidence for both choices, but we should preserve the conditions. The target comparison changes training duration as well as target type. The masking comparison uses the same backbone and epochs but differs in the amount and arrangement of context. These tables support the proposed recipe under those conditions. They do not prove that target space alone explains every cross-method difference, or that the best image mask is the best genomic mask.”

**Source:** [S02 Tables 6–7](https://arxiv.org/pdf/2301.08243). No error bars were inferred for these point estimates.

## B5 — JEPA-DNA is backbone-specific

**Use when asked:** “How do you turn all the DNA token vectors into the latent target?”

**On screen / visual:** three rows: DNABERT-2 → CLS; NTv3 → mean pooling; HyenaDNA → last token. Distinguish token-level transformer prediction from the pooled MLP route. Caption “Architecture simplification; consult §3 and Appendix A.2 for complete branches.”

**Speaking answer:** “The genomic latent loss compares aggregated sequence representations, and the path to that representation depends on the backbone. For the CLS and last-token configurations the paper uses a transformer predictor. For NTv3 it describes a three-layer MLP on a mean-pooled representation. So the token-remasking diagram should not be imposed unchanged on NTv3. The model also retains token prediction, and the complete recipe contains additional forward passes and regularization. It is a hybrid continued-training framework, not a single interchangeable image-patch implementation.”

**Source:** [S06 §3, §4.1, Appendix A.2 and Figure 3](https://arxiv.org/html/2602.17162v3).

## B6 — The genomic component controls

**Use when asked:** “What is the incremental benefit over just continuing the language model?”

**On screen / visual:** use the complete Table 4 extract below or `data/dna_ablation.csv`. Preserve all rows, mark preprint status, and explain that the last column is a different task/protocol from the Table 1 expression row.

| Continued-training condition | Promoter AUROC | Splice AUROC | BEND expression AUROC |
|---|---:|---:|---:|
| Original checkpoint | 0.884 | 0.653 | 0.543 |
| MLM | 0.929 | 0.674 | 0.532 |
| MLM + JEPA | 0.927 | 0.669 | 0.529 |
| MLM + JEPA + scheduled masking | 0.925 | 0.687 | 0.519 |
| MLM + JEPA + VICReg | 0.928 | 0.689 | 0.565 |
| MLM + JEPA + VICReg + scheduled masking | 0.928 | 0.705 | 0.574 |

**Speaking answer:** “The continued-MLM row is the crucial baseline. Adding JEPA alone is slightly worse on each displayed endpoint. The full recipe improves the splice and BEND expression point estimates relative to MLM, while promoter is essentially unchanged and slightly lower. This is not a clean proof of one universally useful term. The table does not establish equal computational cost for every condition. Also, the appendix uses splice-site validation for checkpoint selection, and reported probe-seed variability should not be mistaken for independent pretraining replication.”

**Source:** [S06 Table 4 and Appendix A.2](https://arxiv.org/html/2602.17162v3). Promoter/splice use task readouts; BEND expression here is the zero-shot expression-effect endpoint from Table 3. Do not average heterogeneous endpoints as a clinical utility score.

## B7 — Protein teacher provenance

**Use when asked:** “Does the protein case show JEPA beats protein language models?”

**On screen / visual:** a training-information matrix with rows “student inputs”, “teacher inputs”, “pretraining labels/annotations”, “inference inputs”, “evaluation split”. Fill only the abstract-supported entries; mark unaudited details “not established here”.

**Speaking answer:** “The accessible ProtJEPA abstract supports the high-level multimodal-teacher comparison. It does not allow me to defend a full benchmark or leakage analysis. If the teacher has extra structural or functional information, we need to count that as training information when choosing the baseline. I would want the full methods, homology-aware evaluation appropriate to the task, and an information-matched comparison before concluding that the predictive objective is responsible for a gain.”

**Source:** [S07 abstract](https://www.biorxiv.org/content/10.64898/2026.08.03.742606v1). No numerical claim is authorized by this package.

## B8 — A phylogenetic application is a research proposal

**Use when asked:** “Could this infer phylogenetic trees?”

**On screen / visual:** sequence → embedding → proposed phylogenetic procedure → tree evaluation. Label the whole path “PROPOSAL — NOT A REPORTED JEPA RESULT”. Next to it: “functional similarity ≠ evolutionary distance”.

**Speaking answer:** “Potentially, as a representation feeding a downstream method, but embedding distances do not automatically have evolutionary meaning. Convergent function could make distant lineages look similar, while training composition could encode taxonomic shortcuts. I would start with known or simulated trees, define the evolutionary conditions, and compare the proposed pipeline with established sequence-based alternatives. The source search for this talk did not establish a direct JEPA phylogenetic reconstruction study; that limits my claim, but does not prove no such work exists.”

**Source:** original proposed experiment; bounded-search status documented in `04_SOURCE_EVIDENCE.md`.

## B9 — Clinical forecasting is not an intervention model

**Use when asked:** “Could you use it for diagnosis or patient digital twins?”

**On screen / visual:** two separate questions: “Predict Y given observed history” and “Predict Y under an intervention”. A line separates retrospective performance, external validation, and prospective utility. Do not depict them as completed milestones.

**Speaking answer:** “A latent representation could be useful for diagnosis or forecasting, and Clin-JEPA provides a recent retrospective clinical example. But forecasting observed trajectories is different from identifying what would happen if treatment changed. Treatment choice is associated with severity and other confounders. Before making a diagnostic or intervention claim I would define the intended population, prediction time, outcome, comparison, and validation setting. A retrospective discrimination score alone does not establish calibration, transportability, or improved care.”

**Source:** [S08 Clin-JEPA](https://arxiv.org/abs/2605.10840v4); the validation distinctions are methodological analysis, not clinical advice.

## B10 — Newer JEPA variants and the scope of this talk

**Use when asked:** “Why emphasize I-JEPA when there are newer formulations?”

**On screen / visual:** three cards: “I-JEPA: inspect one complete recipe”; “V-JEPA 2.1: dense visual features”; “LeJEPA: alternative distribution regularization”. Avoid a ranking arrow that implies universal superiority.

**Speaking answer:** “I chose I-JEPA because its information flow is a clear entry point. The family has evolved. V-JEPA two point one adds denser and intermediate feature supervision. LeJEPA studies an alternative regularization approach, SIGReg, targeting an isotropic Gaussian embedding distribution without the same teacher and stop-gradient recipe. That reinforces the distinction between JEPA's broad learning idea and I-JEPA's particular implementation. Theoretical claims depend on their assumptions; I am not claiming that a theorem for one formulation proves biological usefulness or validates the I-JEPA recipe.”

**Sources:** [S05 V-JEPA 2.1](https://arxiv.org/abs/2603.14482); [S18 LeJEPA](https://arxiv.org/abs/2511.08544). This is an abstract-level outlook, not a mathematical audit of LeJEPA's theorems.

## Difficult audience questions: concise answers

### 1. Why should a learned target contain anything useful?

It is not guaranteed. Architecture, data, masking, and regularization shape the representation. The empirical case is downstream performance under an appropriate protocol. A target encoder gives a target construction, not an external semantic oracle. See slides 7–8.

### 2. Is the teacher pretrained or initialized from a separate expert?

In the I-JEPA recipe it starts as a copy of the context encoder and evolves by EMA. That differs from approaches distilling a separately pretrained multimodal teacher. JEPA-DNA starts from already pretrained genomic backbones. Do not merge those starting conditions. [S02, S06, S16]

### 3. If the teacher sees the hidden region, is that cheating?

The target is allowed to contain information unavailable to the predictor: that is what prediction means. The information boundary to audit is the predicting input, including attention, preprocessing, and evaluation contamination. See B1.

### 4. Why not simply align the context with the target?

Context and target may represent different parts of an observation. A conditional predictor can model their relationship without requiring identical embeddings. A predictor alone is not unique to JEPA; BYOL also uses one. [S02, S10]

### 5. Why use an EMA teacher instead of freezing it forever?

A frozen random teacher would define a different target-learning problem. EMA lets targets evolve with learning while smoothing updates. That motivates the mechanism; it is not proof that every fixed-teacher approach fails. [S02, S16]

### 6. Does removing gradients from the teacher avoid all collapse?

No. The constant-output counterexample still exists. Update dynamics and other parts of the recipe matter. See B3; do not assert a universal theorem.

### 7. How is variance regularization different from LayerNorm?

The relevant variance penalty compares different samples along each feature dimension. LayerNorm normalizes across the feature dimensions within a sample/token. They operate along different axes and do not impose the same constraint. [S09, S16]

### 8. Does zero covariance imply independent dimensions?

No. It excludes a form of linear dependence, not all nonlinear dependence. A symmetric random variable and its square provide a simple counterexample. See guide §6.

### 9. Is JEPA a probabilistic generative model?

The latent regression objective here does not provide a normalized distribution over original observations. Generative components can be attached or combined with representation learning, but they add machinery and objectives. The answer must name the actual variant rather than treating all uses of “JEPA” as identical.

### 10. If the future is multimodal, what does a deterministic predictor output?

For fixed targets and squared loss, the optimal unconstrained predictor is the conditional mean. That can average incompatible possibilities. Latent prediction may change which variation matters; it does not automatically represent all possible futures. See guide §3.

### 11. Is a high-dimensional embedding really a compression?

Not necessarily in dimension or information. “Latent” means internal representation. Whether details are discarded is an empirical or information-theoretic question, not a consequence of the word embedding.

### 12. Does it reduce the quadratic cost of attention?

Not inherently. The context encoder can save work by processing fewer visible patches, but there is also a teacher pass and predictor. The backbone, resolution, token count, training schedule, and hardware determine cost. [S02, S15]

### 13. Does I-JEPA use no augmentation at all?

Avoid that absolute wording. The paper's claim concerns avoiding the elaborate hand-crafted view-augmentation pipelines used by comparison methods. It still has preprocessing and a deliberately designed masking task. “No inductive bias” would be false. [S02, S16]

### 14. Why not compare with fine-tuned MAE?

That answers another question: how well the representation adapts under fine-tuning. It is useful but should not be merged with frozen linear probing. Report each protocol explicitly. [S02, S12]

### 15. Does good linear probing mean the representation understands the task?

It means the chosen readout can extract predictive information under that split. It does not establish mechanism, causality, or robustness to a changed distribution. “Understands” needs an operational definition.

### 16. What happens to the predictor at inference?

For I-JEPA linear evaluation, use the reported target-encoder representation; the predictor is not needed for that readout. For action-conditioned planning, prediction remains essential. Follow the task-specific inference path. [S02, S04]

### 17. Why keep the language-model loss in JEPA-DNA?

It preserves token-level training pressure while the global latent objective emphasizes a different comparison. The hybrid recipe is the actual evaluated method; removing the language objective would be another experiment. [S06]

### 18. Could global pooling hide a pathogenic nucleotide change?

It could make some changes hard for a readout to distinguish, but pooling alone does not prove information loss for every variant. Test the relevant paired variants and endpoints. Do not attribute the observed regressions to one unmeasured mechanism.

### 19. Do the DNA results prove that JEPA causes the improvement?

The strongest supported claim concerns particular combined training conditions. Continued-MLM controls, regularization, masking, optimization, and model selection must be considered. See B6.

### 20. Is 0.051 AUROC improvement “5.1 percent better”?

It is an absolute increase of 0.051, or 5.1 percentage points on a 0–100 AUROC scale. Relative to 0.788 it is approximately 6.47%. These are different quantities; neither alone describes clinical impact. The charts use raw AUROC values and explicitly labeled differences.

### 21. Why not show only the strongest biological result?

Because the research question concerns usefulness across tasks relevant to us. Positive and negative examples show the boundary of the claim. The selected slide is clearly labeled; all nine DNABERT-2 AUROC rows are available in the source ledger and CSV.

### 22. Are the reported differences statistically significant?

This package does not establish that for the selected main-slide comparisons. Point estimates and variation over linear-probe seeds are not a substitute for the appropriate uncertainty over the full training and evaluation procedure. Do not invent confidence intervals.

### 23. Is the protein case self-supervised if annotations train the teacher?

Describe the actual sources of information. A student's target may be automatically produced while the teacher incorporates annotations or other modalities. “Self-supervised” should not conceal that provenance. Full ProtJEPA details remain unaudited here. [S07]

### 24. Why is clinical prediction not a treatment simulator?

Observed treatment decisions correlate with patient state and other factors. Predicting an observed outcome does not identify the outcome under a different intervention without further assumptions and evidence. See B9.

### 25. Can we implement it this week?

A small objective-level prototype may be possible, but this package has not measured the lab's compute, data readiness, or training cost. Start with a fixed checkpoint, one task, and clear baselines. Do not promise reproduction of a large pretrained model on an unmeasured budget.

### 26. What about LeJEPA and its theoretical guarantees?

It is a distinct formulation with SIGReg and its own assumptions. Its existence is another reason not to define the whole family by I-JEPA's EMA teacher. I can explain that distinction, but have not audited its proofs in this presentation. [S18]

## A concrete proposed pilot, ready for discussion

**Status:** proposed; no data accessed, model trained, or compute measured.

**Question:** does the full objective improve one lab-owned genomic task beyond continued native-objective training, without an unacceptable loss on a relevant variant-sensitive endpoint?

**Starting point:** a genomic checkpoint already usable by the lab. DNABERT-2 is a paper-aligned illustration, not a mandate or an assertion of local availability.

| Arm | Purpose |
|---|---|
| A: untouched checkpoint | Quantify the starting representation |
| B: native-objective continuation | Measure the effect of more training |
| C: B + latent prediction | Test the isolated addition under the chosen settings |
| D: C + variance/covariance penalties | Test distribution regularization in combination |
| E: D + scheduled masking | Test the complete proposed recipe |
| F: B + regularization + scheduled masking, without latent prediction | Ask whether supporting ingredients explain the benefit without the latent objective |

Specify the primary endpoint, unit of split, and checkpoint-selection rule before training. Match data exposure for the primary comparison, report extra compute, and add a compute-matched comparison if feasibility permits. Reuse the same train/validation/test partitions across arms, with biological grouping chosen for the intended generalization claim. Keep the held-out test set out of early stopping.

Measure the chosen task with appropriate discrimination or regression metrics. For rare positives, accompany AUROC with precision-recall information and the class prevalence. If a calibrated decision is the intended use, assess calibration and relevant operating points separately. Repeat the training procedure, not only the linear probe, when estimating variation across model learning. The number of runs and detectable effect must be chosen from feasibility and precision needs; this document makes no power claim.

An improvement in E alone would justify investigating the recipe. A comparison with F is needed to help attribute any benefit specifically to the latent term. Worse variant-sensitive behavior may be a reason to reject or redesign the method even if another task improves. This is an experimental decision, not a claim that JEPA must preserve or discard any particular biological signal.

## Two learning sessions and one rehearsal

### Session 1 — Understand the mechanism (suggested 60–75 minutes)

Read guide §§1–6 and slides 1–7. Close the files and draw the architecture. Annotate what each branch sees and how it updates. Calculate the squared-loss and EMA examples. Explain collapse aloud without saying that EMA guarantees prevention. Use B1–B3 only after attempting your own answer.

**Exit criterion:** a five-minute explanation with the correct diagram, tensor alignment, and update paths. A correct drawing is more useful than memorizing a slogan.

### Session 2 — Own the evidence (suggested 60–75 minutes)

Read slides 8–14, guide §§8–11, and the numerical evidence blocks. Practice explaining why the continued-MLM control changes the conclusion. Review the ProtJEPA access limit and clinical/phylogenetic distinctions. Answer questions 14–26 aloud.

**Exit criterion:** explain one positive result, one regression, one attribution limit, and one proposed falsifying experiment without overclaiming.

### Timed rehearsal (suggested 40–50 minutes including correction)

Deliver the main script with diagrams, using the cumulative targets in `01_SLIDE_SCRIPT.md`. Read the full narration once; on the next pass use the slide titles and transitions as cues. Time spent pointing at equations counts as presentation time. Stop at 30 minutes and record where you were; do not extrapolate from word count alone.

If too long, shorten optional history and outlook before deleting the architectural walkthrough or genomic controls. If too short, slow down on the information-flow and loss explanations; do not add more papers just to fill time. Finish with a five-question mock discussion: teacher visibility, collapse, paper/code loss, continued-training controls, and one biological application.

The proposed session lengths are preparation suggestions, not a claim that mastery can be guaranteed within them.

## Retrieval cards for the lectern

| If you lose the thread on… | Say this next |
|---|---|
| Architecture | “Let me trace what the context branch sees, then what defines the target.” |
| Mathematics | “The prediction is compared with a stopped teacher target; gradients update the predicting branch.” |
| Collapse | “Agreement is necessary for this objective, but agreement on a constant is useless.” |
| Results | “This number belongs to this backbone, dataset, and readout.” |
| Biology | “The relevant question is which biological distinction the representation preserves.” |
| An unaudited detail | “I have not verified that detail, so I would not use it to support the conclusion.” |

## Glossary for speaking

JEPA: joint-embedding predictive architecture. EMA: exponential moving average. MLM: masked language modeling. NTP: next-token prediction. ViT: vision transformer. CLS: a designated classification/global-summary token in some models. AUROC: area under the receiver operating characteristic curve. AUPRC: area under the precision-recall curve. sQTL: splicing quantitative trait locus. eQTL: expression quantitative trait locus. meQTL: methylation quantitative trait locus. EHR: electronic health record. VICReg: variance-invariance-covariance regularization. SIGReg: sketched isotropic Gaussian regularization.

Expand a biological acronym once when speaking to a mixed audience. Avoid pronouncing mathematical symbols faster than the audience can locate them.
