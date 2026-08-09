---
type: concept
title: "Retyping Meeps and Talis to pay down cognitive debt"
aliases: []
tags: [concept, personal, chat]
updated: 2026-08-09
status: developing
---

# Retyping Meeps and Talis to pay down cognitive debt

## Context

[[cognitive-debt]], as described by [[ankur-sethi]] in [[ankursethi2026prevent]], is what accrues when an LLM writes code that a developer never truly internalizes — fast in the moment, but leaving a codebase the human can't reason about unaided. Sethi's countermeasure: never let the assistant touch files directly, only propose changes in chat, then manually retype every line to force comprehension and build a "spatial map" of the codebase.

## The connection

.speeps flagged that [[project-meeps]] and [[financial-maturity-via-talis]] are both 100% LLM-crafted codebases — the maximal case of what Sethi is warning about. Stated intent: "I'll probably one day start rewriting my Meeps & Talis project by hand to really understand the codebase."

This isn't idle — both projects already share near-identical architectural DNA (hexagonal architecture, Mastra, Discord-driven, strict E2E testing per the project pages), which means a manual retyping pass on one likely transfers understanding to the other directly.

## Open question

Whether to apply Sethi's stricter workflow (agent proposes in chat only, human types every edit) prospectively on future work on these two projects, rather than only retroactively rewriting existing code — that would stop the debt from growing further while the backlog gets paid down.

Filed from chat (2026-08-09).
