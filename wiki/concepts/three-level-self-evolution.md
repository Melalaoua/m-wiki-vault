---
type: concept
title: "Three-Level Self-Evolution"
aliases: []
tags: [concept, phd]
---

# Three-Level Self-Evolution

Three-Level Self-Evolution is a system optimization architecture, notably implemented in [[vibemed]], that operates simultaneously on three temporal timescales to balance immediate adaptability with long-term stability in agentic systems:

1. **Memory-Level Evolution:** Real-time extraction and structural storage of interaction traces into working, episodic, and graph memory, allowing the agent to adapt immediately without updating parameters.
2. **Model-Level Evolution:** Periodic (e.g., weekly or monthly) parameter updates leveraging [[wiki/concepts/supervised-fine-tuning]] and [[wiki/concepts/direct-preference-optimization]] using distilled reflection datasets.
3. **Code-Level Evolution:** Automated structural optimizations, where the system modifies its own prompt logic, routing behaviors, or generates and tests novel functional code modules in an isolated safety sandbox.

Source: [[wiki/sources/phd2026toward|Toward Vibe Medicine: A Self-Evolving Multi-Agent Framework for Clinical Decision Support]]
