# Technical study guide — JEPA for a biological AI journal club

Prepared 7 September 2026. Read alongside `01_SLIDE_SCRIPT.md`. This guide supplies material to understand and answer questions; it is not additional narration to squeeze into 30 minutes. Equations and toy examples below are original teaching constructions unless explicitly attributed. Paper-specific results and implementation statements link to primary sources; the evidence ledger records access and limitations.

## 1. The answer you should be able to give in 30 seconds

A joint-embedding predictive architecture learns a relationship between representations. A context encoder embeds what is available; a predictor uses that representation and relevant conditioning information to predict a target representation; a target encoder defines what is to be predicted. In I-JEPA, the target consists of features at selected image-patch locations, computed from the complete image. The context branch does not see those image patches. Backpropagation updates the context encoder and predictor, while an exponential moving average updates the teacher. Downstream evaluation determines whether the learned representation is useful. Other JEPA implementations change the targets, losses, regularizers, and training or inference roles. [I-JEPA §2–3](https://arxiv.org/pdf/2301.08243)

Do not reduce this to “a transformer that understands instead of generates.” That confuses an architectural building block with a learning objective and replaces measurable behavior with an undefined claim.

## 2. Prerequisites, explained from the ground up

### Representation, embedding, and latent space

A representation is an internal description of an input. In neural networks this is often a vector or array of real numbers. An embedding is a learned mapping into such a vector space, or the resulting vector. “Latent” means this representation is internal rather than directly observed as the raw input.

A DNA string might become an array `H ∈ R^(N×D)`, with `N` tokens and `D` features per token. A pooling operation can turn this into one vector in `R^D`. A vector's coordinates need not have individually interpretable biological meanings. A change of basis can preserve much of its useful information while changing every coordinate.

Representation learning chooses features through a training objective rather than requiring a human to hand-code every feature. Both generative and non-generative methods can learn useful representations. A latent space is not necessarily lower-dimensional than the raw signal, nor is it necessarily a sufficient statistic for a downstream task.

### Self-supervision is a source of training targets

Supervised learning uses target annotations such as assay labels. Self-supervised learning constructs a learning task from the data: hide tokens, predict another view, or predict the features of a held-out region. It can use unannotated observations for its main loss while still depending on labeled validation for model selection or downstream evaluation.

This distinction matters here: a model can have a self-supervised objective without the entire study being label-free. JEPA-DNA's appendix reports checkpoint selection using a labeled splice-site validation task; keep that separate from the nature of the pretraining loss. [JEPA-DNA Appendix A.2](https://arxiv.org/html/2602.17162v3)

### Transformer essentials

Tokens are mapped into vectors, supplemented with positional information, and transformed by attention and feed-forward layers. In one attention head,

\[
Q=HW_Q,\quad K=HW_K,\quad V=HW_V,\qquad
\operatorname{Attention}(Q,K,V)=\operatorname{softmax}\!\left(\frac{QK^\top}{\sqrt{d_k}}+M\right)V.
\]

The matrix `M` can prohibit information flow, for example from future to past in a causal language model. Each row of the softmax gives weights for combining value vectors. Attention lets a patch or nucleotide token incorporate information from other permitted positions; it does not itself establish a causal biological relationship. [Transformer](https://arxiv.org/abs/1706.03762)

For a vision transformer, split an image into patches and map each patch to a token. An image of 224 × 224 pixels with 16 × 16 patches has `(224/16)^2 = 196` patches. With three color channels, each flattened raw patch has `16×16×3 = 768` values before projection; this equality with a possible model dimension is incidental. [Vision Transformer](https://arxiv.org/abs/2010.11929)

### Loss, gradients, and optimization

A loss measures how well the current output meets the training objective. Backpropagation computes derivatives through the computation graph. An optimizer uses those derivatives to update parameters. For plain gradient descent, `θ_new = θ_old − η ∇θ L`. Actual training commonly uses adaptive optimizers and schedules, but the direction of the information flow remains the central point.

Low training loss is evidence that an optimization objective is being met. It is not automatically evidence of generalization, useful biology, or a well-designed objective.

## 3. Why moving the target into representation space is attractive—and risky

Consider an observed target `Y = (S,U)` where `S` is predictable structure and `U` is detail that remains uncertain given context `X`. Reconstructing every coordinate of `Y` may spend capacity on predicting `U`. A representation `r(Y)` might discard some variation in `U` and retain useful structure in `S`.

This is a motivating model, not a theorem that learned embeddings discover the intended `S`. If a downstream label depends on `U`, discarding it damages that task. A neutral variant for one phenotype can matter for another. Similarly, a change that barely affects a global sequence embedding can have a large local functional effect.

For fixed targets and an unrestricted predictor under squared error, the population optimum is the conditional mean:

\[
g^*(x)=\mathbb E[r(Y)\mid X=x].
\]

To see why, set `m = E[r(Y)|x]`, expand `E[||r(Y)−a||²|x]`, and use the vanishing cross term:

\[
\mathbb E[\|r(Y)-a\|^2\mid x]
=\mathbb E[\|r(Y)-m\|^2\mid x]+\|m-a\|^2.
\]

The second term is minimized at `a=m`. This derivation assumes a fixed representation and squared loss. It does not describe the complete optimization of two jointly changing neural encoders, nor the released Smooth L1 objective. Its lesson is that ambiguity does not disappear just because the target is latent: a deterministic predictor can still average incompatible possibilities.

LeCun's broader proposal considers additional latent variables and hierarchical predictions to represent uncertainty and abstraction. The positional queries in I-JEPA are a concrete conditioning mechanism; they are not automatically a learned distribution over possible futures. [LeCun 2022](https://openreview.net/pdf?id=BZ5a1r-kVsf)

## 4. Architectural anatomy and notation

| Symbol | Meaning | Common confusion to avoid |
|---|---|---|
| `x` | Complete input after the chosen preprocessing | The teacher's complete input is not the context-only input |
| `C` | Set of permitted context positions | A candidate context crop is not the final visible set |
| `T_k` | Positions in target block `k` | Different target blocks may overlap each other |
| `fθ` | Context/online encoder | “Online” refers to updates, not internet access |
| `fθ̄` | Target/teacher encoder | It changes by EMA despite having no loss gradient |
| `gφ` | Predictor | It is trained; it is not a fixed distance function |
| `p_T` | Target-location queries | They reveal location, not hidden content |
| `sg` | Stop-gradient | Same forward value, no backward derivative through this path |
| `τ` | EMA coefficient | It averages parameters, not predicted vectors |
| `D` | Feature dimension | Not necessarily an interpretable biological dimension |

The I-JEPA teacher processes all patches before output selection. Context patches are selected before context self-attention, so target content cannot influence the context encoder through attention. This ordering is fundamental: encoding the full image first and then hiding its context-branch outputs can leak the target through contextualization. [I-JEPA §3](https://arxiv.org/pdf/2301.08243)

The target is contextualized by the full image. This is intentional, not training-test leakage by itself: a training target is allowed to contain what the model is trying to predict. Leakage arises if prohibited target content reaches the predicting inputs, or if evaluation information enters training or selection contrary to the evaluation protocol.

### Worked tensor path

Use this small, original example when rehearsing. Dimensions are illustrative, not published hyperparameters.

| Stage | Shape for batch size 2 | Information |
|---|---|---|
| Complete patch tokens | `2 × 16 × 8` | All sixteen positions |
| Context encoder output | `2 × 12 × 8` | Positions outside `{5,6,9,10}` |
| Teacher output before selection | `2 × 16 × 8` | Full-image contextual features |
| Selected teacher targets | `2 × 4 × 8` | Four target positions |
| Context projected to predictor width | `2 × 12 × 4` | Same visible information, narrower features |
| Predictor target queries | `2 × 4 × 4` | Shared learned mask token plus positional information |
| Predictor output projected back | `2 × 4 × 8` | Predictions aligned with targets |

The predictor can process context tokens and target queries jointly, then return target-position outputs. For multiple target blocks, bookkeeping must preserve the image, block, and patch correspondence. If blocks overlap, the normalization convention determines how repeated target positions contribute to the loss.

The paper's typical multi-block recipe uses four targets with area scale 0.15–0.20 and a candidate context of scale 0.85–1.0, removing overlaps with target blocks. These ranges are not a statement that 85–100% of the patches remain visible to the context encoder. [I-JEPA Figure 4](https://arxiv.org/pdf/2301.08243)

## 5. The loss, gradients, and teacher update

### Teaching objective

For a batch of `B` examples and `K` target blocks per example, an explicitly normalized squared-distance teaching form is

\[
\mathcal L_{\rm teach}=\frac1B\sum_{b=1}^{B}\frac1K\sum_{k=1}^{K}\frac1{|T_{bk}|}
\sum_{j\in T_{bk}}\|g_\phi(f_\theta(x_{b,C}),p_{T_{bk}})_j-\operatorname{sg}(f_{\bar\theta}(x_b)_j)\|_2^2.
\]

This follows the paper-level squared-distance idea, adding explicit batch and per-block means for clarity. The paper's displayed formula sums over positions inside a block. Loss normalization affects scale and, with unequal target sizes, relative weighting; do not claim these formulas are literally identical in all settings.

Write a target as `t` and its prediction as `q`. Then for `ℓ=||q−t||²`, `∂ℓ/∂q=2(q−t)`. With `q=(0.8,0.2)` and `t=(1,0)`, `ℓ=0.08` and `∇qℓ=(−0.4,0.4)`. A toy gradient step with learning rate 0.1 on `q` itself gives `(0.84,0.16)` and loss `0.0512`. A real neural network updates parameters, not this isolated vector directly.

The teacher receives no gradient from this loss path:

\[
\nabla_{\bar\theta}\mathcal L=0,\quad
\nabla_\phi\mathcal L\ne0,\quad
\nabla_\theta\mathcal L\ne0
\]

where the latter two derivatives may of course be zero at particular parameter values. Stop-gradient changes backward computation without changing the forward target values.

### Paper versus released implementation

The released I-JEPA training code normalizes teacher features along the feature dimension and uses `smooth_l1_loss`. For residual `r` and parameter `β`, the elementwise Smooth L1 loss is

\[
\ell_\beta(r)=\begin{cases}r^2/(2\beta),&|r|<\beta,\\|r|-\beta/2,&\text{otherwise}.\end{cases}
\]

For the residuals `(−0.2,0.2)` and `β=1`, the mean over two coordinates is `0.02`, distinct from the summed squared distance `0.08`. This is a convention and objective difference, not a numerical inconsistency in the toy arithmetic. [Pinned official code, lines 294–313](https://github.com/facebookresearch/ijepa/blob/52c1ae95d05f743e000e8f10a1f3a79b10cff048/src/train.py#L294-L313)

Layer normalization is not the same operation as normalizing every vector to unit Euclidean norm, and neither is the same as enforcing variance across different samples. Always specify the axis being normalized.

### EMA: smoothing a changing target

After the online optimizer step,

\[
\bar\theta_t=\tau_t\bar\theta_{t-1}+(1-\tau_t)\theta_t.
\]

If `τ` is constant, expansion gives

\[
\bar\theta_t=\tau^t\bar\theta_0+(1-\tau)\sum_{i=1}^{t}\tau^{t-i}\theta_i.
\]

Older online parameters have geometrically decaying influence. For `τ=0.9`, an old teacher value of 2 and a new online value of 3 yield 2.1. A large `τ` provides slowly changing targets but can also make the teacher lag. The paper and code use their actual schedules; 0.9 is only an arithmetic example.

### Educational pseudocode

This is original pseudocode reflecting the released loss choice. It omits distributed training, variable-length batching, optimizer schedules, checkpointing, and production mask construction. It is not a drop-in reproduction.

```python
teacher = copy_parameters_and_architecture(context_encoder)
disable_gradients(teacher)
optimizer = make_optimizer(context_encoder, predictor)

for image_batch in training_data:
    context_positions, target_blocks = sample_valid_masks(image_batch)
    # No target image content may enter context self-attention.
    with no_gradient_recording():
        all_targets = teacher(image_batch)
        all_targets = layer_norm_last_dimension(all_targets)
        target_features = select_and_align(all_targets, target_blocks)

    context_features = context_encoder(image_batch, context_positions)
    predicted_features = predictor(
        context_features, context_positions, target_blocks
    )
    loss = mean_smooth_l1(predicted_features, target_features)
    optimizer.clear_gradients()
    loss.backward()  # context encoder and predictor only
    optimizer.step()

    with no_gradient_recording():
        for target_p, context_p in corresponding_parameters():
            target_p.assign(tau * target_p + (1 - tau) * context_p)
```

In an actual implementation, verify checkpoint initialization, frozen teacher parameters, positional alignment, and which optimizer owns which parameters. “No gradients” does not by itself switch dropout or normalization modules into evaluation mode; mode behavior must match the implementation rather than an assumed generic teacher recipe.

## 6. Collapse, covariance, and what they do not guarantee

### A counterexample to an overconfident explanation

Let `fθ(x)=fθ̄(x)=c` for every input and let `gφ(c,p)=c` for every query. The predictive loss is zero. The teacher can stay constant under EMA. Thus “EMA mathematically rules out collapse” is false without additional assumptions.

Architectural asymmetry and update rules can change optimization dynamics, so the existence of a collapsed solution does not mean training must find it. Conversely, successful experiments do not prove that no failed setting exists. BYOL, SimSiam, and I-JEPA illustrate related but different recipes; a general proof should not be inferred from a single component. [BYOL](https://arxiv.org/abs/2006.07733), [SimSiam](https://arxiv.org/abs/2011.10566), [I-JEPA](https://arxiv.org/pdf/2301.08243)

### Explicit variance and covariance constraints

For a batch representation matrix `U ∈ R^(B×D)`, one variance penalty is

\[
v(U)=\frac1D\sum_{j=1}^{D}\max(0,\gamma-\sqrt{\operatorname{Var}(U_{:,j})+\epsilon}).
\]

For sample covariance

\[
C=\frac{(U-\bar U)^\top(U-\bar U)}{B-1},\qquad
c(U)=\frac1D\sum_{i\ne j} C_{ij}^2.
\]

The variance term penalizes dimensions with too little across-sample spread. The covariance term penalizes linear redundancy between dimensions. It does **not** imply statistical independence: a symmetric variable `X` and `X²` can have zero covariance while remaining dependent. These are explanatory forms; consult the implementation for which branches are regularized and how terms are aggregated. [VICReg](https://arxiv.org/abs/2105.04906)

For a toy batch `U=[(1,0),(0,1),(−1,0),(0,−1)]`, each dimension has sample variance `2/3`, standard deviation approximately `0.8165`, and off-diagonal covariance zero. With `γ=1` and `ε=0` purely for arithmetic, the variance penalty is about `0.1835`; the covariance penalty is zero. A constant batch has variance penalty 1. Real numerical code should include its defined stabilizer.

### Diagnostics

Monitor per-dimension standard deviations, feature norms, covariance eigenvalues, and a held-out task. Complete collapse is not the only failure: information may occupy a very small subspace. The participation ratio `(Σλ_i)²/Σλ_i²` of nonnegative covariance eigenvalues is one descriptive measure of effective dimensionality when the denominator is nonzero. It is a diagnostic, not a task-performance metric.

High variance may encode nuisance factors. Good linear probing on a leaky split may reward memorization. Both representation diagnostics and evaluation design are necessary.

## 7. Comparison with nearby methods

| Method | Essential teaching distinction | Do not say |
|---|---|---|
| MLM / next-token prediction | Token identity or conditional token distribution is the target | “They do not learn semantics or embeddings” |
| MAE | Reconstructs masked image pixels using an encoder/decoder | “It has no latent representation” |
| SimCLR | Aligns augmented positives relative to other examples using a contrastive loss | “Every SSL method needs negatives” |
| BYOL | Predicts a moving teacher's other-view representation, without explicit negatives | “I-JEPA invented moving teachers” |
| SimSiam | Uses asymmetric stopped gradients without a momentum teacher | “EMA is necessary for every non-contrastive learner” |
| DINO | Self-distills teacher distributions with its own centering/sharpening recipe | “DINO and I-JEPA have identical targets” |
| I-JEPA | Context-conditioned prediction of selected teacher patch features | “It is a complete general-purpose world simulator” |
| JEPA-DNA | Adds a global latent objective and regularization to continued genomic LM training | “It removes the language-model loss” |

Primary references: [MAE](https://arxiv.org/abs/2111.06377), [SimCLR](https://arxiv.org/abs/2002.05709), [BYOL](https://arxiv.org/abs/2006.07733), [SimSiam](https://arxiv.org/abs/2011.10566), [DINO](https://arxiv.org/abs/2104.14294).

For deeper discussion, the SimCLR-style loss for an anchor `i` and positive `j` has the form

\[
\ell_{i,j}=-\log\frac{\exp(\operatorname{sim}(z_i,z_j)/T)}{\sum_{k\ne i}\exp(\operatorname{sim}(z_i,z_k)/T)}.
\]

Here `T` is a temperature, not a target-position set. The denominator compares the positive with alternatives; a representation-prediction regression loss has a different structure. In biology, deciding what constitutes a valid positive or negative can itself require domain knowledge.

## 8. Evaluation: readouts, supervision, compute, and inference

**Linear probing:** freeze the representation model; fit a linear supervised head. This tests accessible information for the chosen task and readout. It cannot establish the absence of information a nonlinear head might recover.

**Fine-tuning:** update some or all representation-model parameters using downstream training data. This tests adaptability under that procedure, not the untouched embedding alone.

**Zero-shot:** no task-specific parameter fitting under a particular protocol. The scoring rule may still use prior training, task design choices, or model selection. Always state “zero-shot with respect to what?”

**Compute:** epochs, steps, tokens, wall time, and FLOPs measure different things. Two objectives can see the same data but perform different numbers of encoder passes. The choice between equal data exposure and equal computational budget depends on the experimental question; report both where feasible.

**Inference:** I-JEPA Appendix A.1 reports evaluating the EMA target encoder with average pooling and no CLS token. The predictor is not needed for that linear-probe representation extraction. By contrast, an action-conditioned world model needs a predictor during planning. Do not write one universal “discard these branches” rule for the family. [I-JEPA](https://arxiv.org/pdf/2301.08243), [V-JEPA 2](https://arxiv.org/abs/2506.09985)

Decoded I-JEPA image illustrations use a separately trained generative visualization model. The fact that the paper shows image samples does not mean pixel reconstruction was the I-JEPA pretraining loss. [I-JEPA §8](https://arxiv.org/pdf/2301.08243)

## 9. The genomic case in detail

### What is actually being added?

JEPA-DNA v3 starts from pretrained genomic backbones and continues training with a composite objective. It evaluates DNABERT-2, NTv3, and HyenaDNA. The learned targets are global sequence representations rather than experimentally measured biological function. [Methods](https://arxiv.org/html/2602.17162v3)

The predictor/aggregation route depends on the backbone. DNABERT-2 uses a CLS-based configuration; HyenaDNA uses a last-token representation. The paper describes a transformer predictor for those token-based configurations. NTv3 uses mean pooling and a three-layer MLP on a pooled representation. Do not impose a token-level transformer predictor and remasking diagram on every backbone.

The token-level configuration uses initial span masking and a remasking step in representation space before prediction. The paper also describes a masking schedule and two stages: initially train the attached predictor with the backbone frozen, then update the backbone and predictor jointly. Extra language-model and variance-regularization passes make the complete computational graph more involved than the main-slide diagram. [§3 and Appendix A.2](https://arxiv.org/html/2602.17162v3)

### Objective

\[
\mathcal L=\lambda_1\mathcal L_{\rm LM}+\lambda_2(1-\cos(\hat z,z))+\lambda_3\mathcal L_{\rm var}+\lambda_4\mathcal L_{\rm cov}.
\]

All coefficients represent tunable weights; the equation does not prescribe universal values. Cosine similarity measures angle and is insensitive to positive rescaling of one nonzero vector. The variance terms therefore serve a different purpose from angular agreement.

For the earlier toy vectors `(0.8,0.2)` and `(1,0)`, cosine loss is `1−0.8/√0.68 ≈ 0.02986`. This is a comparison of loss geometry, not a reason to compare raw loss magnitudes across trained models.

### Critical claims to keep separate

1. Some selected representation scores improve after the combined recipe.
2. The recipe improves every task or backbone.
3. The latent loss alone causes the improvements.
4. The model learns a mechanistically correct regulatory system.
5. The model is clinically useful for interpreting patient variants.

The first statement can be supported by particular reported results. The others require further evidence and are not established by that statement. Table 1 includes task-specific regressions; Table 4 includes continued-MLM controls that change the interpretation of the latent term.

Reported variability over linear-probe seeds does not necessarily quantify variability over independent pretraining runs. Early stopping on splice-site validation is a form of label-informed selection. Access to a preprint through an indexing service does not make it peer reviewed. See `04_SOURCE_EVIDENCE.md` for the exact tables, versions, and audit limitations.

## 10. Protein, phylogenetic, and clinical connections

**Proteins — direct emerging work:** ProtJEPA's accessible abstract describes sequence-based learning from multimodal teacher representations. The main talk uses that qualitative observation only. Without full-method verification, we should not assert a particular improvement, a homology-safe split, or absence of annotation leakage. [ProtJEPA](https://www.biorxiv.org/content/10.64898/2026.08.03.742606v1)

**Proteins — a proposed experiment:** choose a well-defined task, such as a measured functional assay, and compare a sequence-only continued-training baseline with a latent-objective extension. Evaluate both protein-level performance and mutation-sensitive behavior if variants are the intended use. Use sequence-cluster or other appropriate splits based on the generalization claim. These are design suggestions, not published ProtJEPA results.

**Phylogenetics — proposed, not demonstrated here:** a representation might be useful as a feature for a downstream phylogenetic method, but embedding proximity is not automatically an estimate of substitutions per site or evolutionary time. Test on known or simulated trees, state assumptions, and compare with appropriate sequence-based methods. Consider clade holdouts, convergent function, horizontal transfer, and dataset composition. No direct JEPA phylogenetic reconstruction paper was established in the bounded source search; that is not proof none exists.

**Clinical — emerging retrospective work:** Clin-JEPA reports an application to clinical trajectories. This supports discussing the family beyond vision, not claiming prospective diagnostic utility or causal treatment simulation. For a forecasting study, define a prediction time and horizon, exclude future measurements, split at the patient level, and test the intended deployment setting. For intervention decisions, observational prediction alone does not identify counterfactual treatment effects. [Clin-JEPA](https://arxiv.org/abs/2605.10840)

## 11. Hierarchy, energy, and planning: enough to answer the broader questions

An energy function is a compatibility score; lower energy indicates that a prediction and target fit under the model. Writing `E(x,y)=D(g(f(x)),h(y))` does not automatically produce a normalized probability distribution over `y`. A partition function and further assumptions would be needed for such a probabilistic interpretation.

In a hierarchical proposal, one level can represent relatively local or short-timescale structure and another can predict more abstract, longer-timescale changes. I-JEPA's image-patch experiment does not by itself demonstrate such a hierarchy. [LeCun proposal](https://openreview.net/pdf?id=BZ5a1r-kVsf)

A simple conceptual action-conditioned dynamics model is `z_(t+1)=F(z_(≤t),a_t)`. Planning requires more than this predictor: an objective, candidate actions, constraints, and a procedure for evaluating and selecting actions. For an image goal, one can conceptually choose actions whose predicted future representation is close to the goal representation. Receding-horizon control executes part of a plan, observes the result, and replans. This is a teaching description, not the exact V-JEPA 2 planner specification. [V-JEPA 2 §3–4](https://arxiv.org/abs/2506.09985)

Two further risks follow from the mathematics: prediction errors can accumulate across rollouts, and optimization can exploit errors in the learned model. Accurate one-step prediction does not guarantee reliable long-horizon control. In clinical settings, the challenge also includes whether observed actions identify causal effects.

## 12. Mastery checklist

You are ready for the technical discussion when you can do all of the following without reading the answer:

- Draw the two encoder branches and predictor; mark visible information, gradient paths, and EMA updates.
- Explain why the teacher sees the complete image while the context encoder must not.
- Calculate the toy squared loss, its gradient, and the EMA update.
- Give a constant-output counterexample to an overly strong non-collapse claim.
- Explain why variance across samples differs from normalization across features.
- Distinguish the I-JEPA paper equation from the released implementation's loss.
- State which I-JEPA encoder is evaluated and what a linear probe measures.
- Explain the global latent objective and retained language loss in JEPA-DNA.
- Read the genomic positive and negative examples without claiming statistical significance.
- Explain why the continued-MLM control is necessary and why the full recipe does not isolate one loss term.
- Distinguish a masked video representation objective, causal forecasting, and action-conditioned planning.
- Propose a biological test that could falsify the claim that the new representation is useful.

If an answer depends on an unverified detail, use: “The paper reports X under this protocol. I have not established Y, so I would treat it as an open question.”
