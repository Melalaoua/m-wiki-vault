---
type: concept
title: "Hexagonal Architecture"
aliases: []
tags: [concept, phd]
updated: 2026-07-13
status: developing
---

# Hexagonal Architecture

Hexagonal Architecture (also known as Ports and Adapters) is an architectural pattern that isolates core business logic from outside systems. 

In the context of [[Project Meeps]], it is used to keep the wiki domain logic isolated. The system uses a driving port that accepts a normalized `InboundMessage` (e.g., from a [[Discord]] adapter) and driven ports for outbound side effects (such as Git commits, filesystem writes, and LLM calls via [[Mastra]]).

Source: [[phd/wiki/sources/phd2026mwikiprd|M-WIKI-PRD]]
