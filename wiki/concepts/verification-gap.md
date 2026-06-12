---
type: concept
title: "Verification Gap"
aliases: []
tags: [concept, phd]
---

# Verification Gap

The [[wiki/concepts/verification-gap|verification gap]] is the difference between an [[wiki/concepts/ai-agent|AI agent]]'s confidence in its own work and the actual correctness of that work. It is considered the most common failure mode, where an agent declares a task "done" when, in reality, the code is broken, tests fail, or the requirements have not been met.

A large verification gap indicates a weak [[wiki/concepts/harness|harness]], specifically in the verification feedback layer. Closing this gap requires providing the agent with a clear, machine-verifiable [[wiki/concepts/definition-of-done|Definition of Done]], such as a suite of passing tests or a successful linting command.

Source: [[wiki/sources/walkinglabs2026lecture|Lecture 01. Strong Models Don't Mean Reliable Execution]]
