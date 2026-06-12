---
type: map
title: "AI Agent Failure Modes"
aliases: []
tags: [map, phd]
---

# AI Agent Failure Modes

When an [[wiki/concepts/ai-agent|AI agent]] fails, it is often due to a [[wiki/concepts/harness-induced-failure|harness-induced failure]]. These failures can typically be attributed to one of five layers:

1.  **Task Specification**: Vague or ambiguous requirements force the agent to guess, leading to incorrect implementations.
2.  **Context Provision**: Implicit or undocumented project conventions (e.g., coding style, architectural patterns) are invisible to the agent.
3.  **Execution Environment**: Incomplete or misconfigured development environments cause the agent to waste time on setup issues rather than the task itself.
4.  **Verification Feedback**: The absence of clear, automated verification methods leads to a [[wiki/concepts/verification-gap|verification gap]], where the agent believes it is done but the work is incorrect.
5.  **State Management**: The loss of discovered information between sessions forces the agent to re-learn the codebase repeatedly, reducing efficiency on longer tasks.

Source: [[wiki/sources/walkinglabs2026lecture|Lecture 01. Strong Models Don't Mean Reliable Execution]]
