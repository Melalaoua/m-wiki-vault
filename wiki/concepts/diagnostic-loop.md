---
type: concept
title: "Diagnostic Loop"
aliases: []
tags: [concept, phd]
---

# Diagnostic Loop

The [[wiki/concepts/diagnostic-loop|diagnostic loop]] is the core methodology of [[wiki/concepts/harness-engineering|harness engineering]]. It treats every [[wiki/concepts/ai-agent|agent]] failure as a signal that the [[wiki/concepts/harness|harness]] has a defect, rather than a failing of the model itself. 

The loop consists of a cycle:
1.  **Execute**: Give the agent a task.
2.  **Observe**: Note the failure.
3.  **Attribute**: Map the failure to a specific layer of the harness (e.g., task specification, verification feedback).
4.  **Fix**: Improve that layer to prevent a recurrence of the same failure type.
5.  **Re-execute**: Run the task again and observe the outcome.

By repeatedly applying this process, the harness becomes more robust and agent performance becomes more reliable over time.

Source: [[wiki/sources/walkinglabs2026lecture|Lecture 01. Strong Models Don't Mean Reliable Execution]]
