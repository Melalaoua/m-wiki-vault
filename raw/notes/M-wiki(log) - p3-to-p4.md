---
title: MeepsScribe — Develop — Phase 3 to Phase 4
date: 2026-03-22
type: experiment
status: seedling
tags:
  - experiment
  - MES
  - development
  - prompt-engineering
  - agent-pipeline
experiment-id: EXP-MES-001
run: 1
hypothesis: Systematic prompt testing and an interactive Meeps mode will resolve the hallucination issues observed in the P4 weekly review feature and bring all MeepsScribe features to production-level reliability.
related: []
---

## Objective
I am transitioning MeepsScribe from Phase 3 to Phase 4. Phase 3 encountered Google Services integration issues that are now resolved and nominal. Phase 4 introduced the weekly review feature, but it is producing unreliable outputs — the AI is hallucinating significantly and appears to lack access to the data it needs to synthesize a proper review. The goal of this run is to document the current state of both phases, identify what is broken in P4, and define the test and polish work needed before I can consider the pipeline production-ready.

## Hypothesis
I predict that the weekly review hallucinations are caused by insufficient context being passed to the model at inference time — specifically, the pipeline is either not retrieving the right vault notes or not formatting them correctly before the prompt. Fixing the data ingestion step and tightening the prompt structure will eliminate hallucinations and produce coherent, evidence-grounded weekly reviews. Additionally, adding an interactive mode where I can converse directly with Meeps will dramatically expand the system's utility beyond scheduled automation.

## Setup & Parameters

| Parameter | Value |
|---|---|
| Hardware / Compute | Local machine (background process) |
| Framework / Library | MeepsScribe pipeline (current dev build) |
| Dataset | PhD Obsidian vault — all active notes |
| Model / Architecture | LLM backend (Meeps agent) |
| Key hyperparameters | Prompts under active development — not yet frozen |
| Random seed | N/A |

## Protocol

1. Confirm that all Phase 3 Google Services issues are resolved and log nominal status.
2. Run the P4 weekly review feature end-to-end and observe the hallucination behavior in the output.
3. Inspect the context/data pipeline — verify what notes are actually being passed to the model during weekly review generation.
4. Identify prompt weaknesses: missing data references, under-specified instructions, lack of grounding constraints.
5. Design a systematic feature test checklist covering every MeepsScribe capability (P1 through P4).
6. Run each feature test in sequence, document pass/fail, and log specific failure modes.
7. Polish each failing prompt iteratively until output quality is satisfactory.
8. Begin scoping and implementing the interactive mode — direct conversational interface with Meeps that auto-dispatches actions.
9. Run a full integration test of all features together including interactive mode once implemented.

## Raw Results

```
Phase 3 — Google Services:
  Status: RESOLVED — all integrations nominal as of 2026-03-22

Phase 4 — Weekly Review:
  Status: RUNNING but UNRELIABLE
  Observed behavior: Model generates plausible-sounding but fabricated weekly
  summaries. References events, notes, and action items that do not exist in
  the vault. Output is fluent but factually disconnected from actual vault state.
  Root cause (suspected): Data retrieval step not surfacing correct notes before
  prompt execution. Model filling gaps with hallucinated content.

Development velocity note:
  Pipeline iteration is fast enough to run in background while handling
  parallel tasks. No blocking bottleneck in the dev loop itself.
```

## Analysis

Phase 3 is stable — the Google Services issues were transient and are no longer a concern. The critical problem is in Phase 4. The weekly review hallucination pattern is a classic symptom of a context gap: the model is not refusing to answer when it lacks data, it is confabulating instead. This is a prompt engineering and data pipeline problem, not a model capability problem. I need to audit exactly what gets injected into the prompt context and add explicit grounding instructions (e.g., "only reference notes I have explicitly provided — if data is missing, say so"). The interactive mode is a natural next evolution of the system and the fast development cycle means I can likely implement and test it quickly alongside the prompt polish work. Overall trajectory is positive — the infrastructure is working, the issues are well-scoped and fixable.

## Next Steps

- [ ] Audit the P4 weekly review data pipeline — trace exactly which notes are retrieved and passed as context
- [ ] Add grounding constraint to weekly review prompt: model must cite only provided vault content, not infer missing data
- [ ] Build a systematic feature test checklist for all MeepsScribe features (P1–P4)
- [ ] Run full feature regression — document pass/fail per feature
- [ ] Polish all prompts that fail the regression test
- [ ] Scope and implement interactive Meeps mode (direct conversational interface with auto-action dispatch)
- [ ] Integration test: all features + interactive mode together

## Links

- Code: `../../Data/PhD/Code/MeepsScribe/`