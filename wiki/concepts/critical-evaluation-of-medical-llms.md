---
type: concept
title: "Critical Evaluation of Medical LLMs"
aliases: []
tags: [concept, phd, chat]
---

# Critical Evaluation of Medical LLMs

Evaluating the viability of LLMs and multi-agent systems in [[wiki/concepts/clinical-decision-support]] requires looking past the algorithmic novelty (such as the self-evolving loops in [[wiki/entities/vibemed]]) and scrutinizing safety, bias, and evaluation rigor. For a system to transition from a computer science experiment to a viable Software as a Medical Device (SaMD), three major critical lenses must be applied:

### 1. The Dangers of Implicit Feedback Loops
Systems that update their weights (via [[wiki/concepts/supervised-fine-tuning|SFT]] or [[wiki/concepts/direct-preference-optimization|DPO]]) based on clinician acceptance/rejection face severe bias risks:
* **Automation Bias:** In high-stress or fatiguing environments, clinicians may accept AI outputs that are merely "plausible enough." The AI registers this as a success, progressively learning to optimize for *convincing* the doctor rather than providing the most *medically accurate* recommendation.
* **Practice Bias (Echo Chambers):** If the AI learns continuously from a specific hospital's data, it risks encoding local, potentially flawed practices (e.g., over-prescribing antibiotics) into its weights, rather than adhering to objective medical guidelines.

### 2. The Unviability of Self-Modifying Code in SaMD
Frameworks proposing "code-level evolution" (where an AI rewrites its own prompts, routing logic, or functional modules) conflict fundamentally with medical regulatory frameworks (like FDA or EU MDR). 
* **Regulatory Lock:** Medical software approval relies on evaluating a static, "locked" algorithm. If the code mutates autonomously, the system running today is legally and functionally distinct from the one tested yesterday, voiding its safety guarantees.
* **Silent Failures:** Relying on isolated sandboxes and automated unit tests is insufficient. Tests only catch anticipated failures. Self-modifying code can introduce silent edge cases (e.g., dropping patient allergy data during a complex data transformation) that require human IT and clinical oversight to detect.

### 3. The Flaws of LLM-as-a-Judge in Medicine
Benchmarking clinical AI using another LLM as a judge evaluates *fluency and plausibility*, not clinical truth. 
* **Shared Blind Spots:** Two LLMs trained on similar corpora are likely to suffer from the same knowledge gaps. If the generating LLM hallucinates a confident but dangerous drug interaction, the judging LLM is highly likely to rate it as correct.
* **Rigorous Clinical Evaluation:** True clinical validity cannot be established with simulated cases graded by AI. It requires:
  1. **Retrospective Human Evaluation:** Panels of human specialists blindly grading AI outputs against historical patient records.
  2. **Prospective Clinical Trials:** Deploying the AI in a "shadow" mode in a real clinical setting to measure actual impact on patient outcomes.

Filed from chat (2026-06-24).
