---
type: concept
title: "Harness Engineering"
aliases: []
tags: [concept, phd]
---

# Harness Engineering

Harness engineering is the practice of building and maintaining all the engineering infrastructure that supports an [[wiki/concepts/ai-agent|AI agent]], excluding the model weights themselves. The core principle is that execution reliability is a function of the environment, not just the model's raw capability. When an agent fails, [[wiki/concepts/harness-engineering|harness engineering]] advocates for improving the harness before upgrading the model.

A [[wiki/concepts/harness|harness]] includes:
- **Task Specification**: Clear, unambiguous instructions and a [[wiki/concepts/definition-of-done|Definition of Done]].
- **Context Provision**: Providing relevant information like architectural conventions, often through an [[wiki/entities/agents-md|AGENTS.md]] file.
- **Execution Environment**: A stable and complete development environment with correct dependencies and tool versions.
- **Verification Feedback**: Automated checks like tests and linters that provide clear success/failure signals.
- **State Management**: Persisting knowledge and discoveries across multiple sessions.

The primary methodology is the [[wiki/concepts/diagnostic-loop|diagnostic loop]], an iterative process of identifying and fixing harness defects signaled by agent failures.

Source: [[wiki/sources/walkinglabs2026lecture|Lecture 01. Strong Models Don't Mean Reliable Execution]]
