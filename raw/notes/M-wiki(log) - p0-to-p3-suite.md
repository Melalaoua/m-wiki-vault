---
title: MeepsScribe — Run 1 — p0 to p3 Suite Battle Test
date: 2026-03-20
type: experiment
status: evergreen
tags:
  - experiment
  - AI
  - automation
  - llm-assisted-dev
  - typescript
experiment-id: EXP-003
run: 1
hypothesis: The p0-to-p3 MeepsScribe pipeline is stable enough for real-world use, but a lot more needs to be done to achieve the goals set.
related: []
---

## Objective

I am evaluating the full MeepsScribe pipeline from Phase 1 through Phase 3 in a continuous suite run — effectively a battle test of the system end-to-end. The goal is to identify both functional failures and design-level friction points before committing to further development. I am specifically looking at robustness under real use conditions, not just controlled inputs.

## Hypothesis

The core pipeline will prove mechanically sound — errors will be rare and, when they appear, will be environmental rather than logic failures. However, the command structure will feel too rigid in practice: the bot will lack the conversational fluidity I originally envisioned, where it instinctively dispatches notes to the correct vault without requiring strict syntax from me.

## Setup & Parameters

| Parameter            | Value                                                            |
| -------------------- | ---------------------------------------------------------------- |
| Hardware / Compute   | Local machine                                                    |
| Framework / Library  | Typescript, LLM API (AI-assisted code generation)                |
| Dataset              | Live personal input — real notes and commands during battle test |
| Model / Architecture | MeepsScribe p0–p3 pipeline                                       |
| Key hyperparameters  | Command parsing logic, vault dispatch rules                      |
| Random seed          | N/A                                                              |

## Protocol

1. Launch the full MeepsScribe and test implementation from p0 to p3
2. Interact with the bot using natural, freeform input — as I would in real daily use, not scripted test cases.
3. Attempt to trigger edge cases: ambiguous commands, mid-session additions, rapid successive inputs.
4. Observe where the bot handles input gracefully and where it breaks or feels unnatural.
5. Record all errors encountered, noting whether they originate in the application logic or in the environment (e.g., GitHub integration).
6. Log subjective friction points separately from hard failures.

## Raw Results

```
- Total hard errors encountered: 2
- Error source: Hallucinations & GitHub integration (not application logic)
- Command parsing failures: 2
- Vault dispatch failures: 0
- Timer behavior: did not reset on new line input — session cut short
- Subjective friction: command syntax felt constraining during freeform interaction
```

## Analysis

The pipeline held up remarkably well under battle testing. The single error I encountered was traced to GitHub — not to any logic I or the LLM designed — which is a strong result for a first real-world run. Command parsing and vault dispatch executed without failure.

==HUMAN UPDATE : Well I noticed some hallucinations on the /experiment command. It tends to hallucinate some informations and extrapolate others. Needs to redesign some prompts. But otherwise for what i said in my interaction with the bot, the fidelity of information is there.==

That said, the hypothesis about rigidity was confirmed. The command structure works, but it does not feel fluid. When I interact with MeepsScribe, I want something closer to a conversation — I should be able to say something naturally and have the bot instinctively infer where it belongs and what to do with it. Right now, the bot requires me to adapt to it, rather than adapting to me. This is the core design tension I need to resolve.

The timer issue is a concrete UX failure worth flagging separately: it did not reset when I added a new line during input, which cut the session shorter than intended. This is a good example of a subtle interaction assumption baked into the code that breaks under real use.

On the development process itself: all code and logic were AI-generated, with my active review of every decision, plan, and implementation. I reviewed and approved each step — I did not blindly accept output. What I cannot deny is the magnitude of the speed gain. What would have taken me days or weeks to develop alone was built in a fraction of the time. This is worth documenting as a methodological observation for the project.

#### Overall
It's not perfect, lot of errors there n there. But the potential is palpable. I'm glad it's giving me the framework to be structured and focus in my processes. For a first batch, it's way above the standards.

## Next Steps

- [ ] Redesign the command interface toward a conversational model — the bot should infer intent from natural language, not require strict command syntax
- [ ] Fix the timer reset behavior: timer should restart whenever a new line or input is added mid-session
- [ ] I need to do a deep dive on the AGENTS.md files to really grasp what the bot receive in its inputs. IT's essential that i master this.
- [x] Investigate and resolve the GitHub integration error (isolate root cause)
- [ ] ~~Define what "instinctive vault dispatch" looks like concretely — draft decision logic for ambiguous inputs~~ NO
- [ ] ~~Consider a small LLM-based intent classifier to replace rigid command parsing~~ NO

## Links

- Code: `../../Data/PhD/Code/MeepsScribe/` No 
- Dataset: N/A — live freeform input
- Related experiment: [[M-wiki(log) - p0-to-p3]]