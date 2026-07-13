---
type: concept
title: "Tool-Selection Routing"
aliases: []
tags: [concept, phd]
updated: 2026-07-13
status: developing
---

# Tool-Selection Routing

Tool-Selection Routing is an interaction paradigm for conversational agents where user intent is determined by the LLM deciding which available tools to invoke, rather than relying on regex or keyword matching. 

In [[M-Wiki]], this allows natural language compound requests to seamlessly trigger operations like `captureSource` or `ingestSource`, guarded by a user-confirmation checkpoint before any mutating filesystem writes occur.

Source: [[phd/wiki/sources/phd2026mwikiprd|M-WIKI-PRD]]
