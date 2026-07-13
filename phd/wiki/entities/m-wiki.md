---
type: entity
title: "M-Wiki"
aliases: []
tags: [entity, phd]
updated: 2026-07-13
status: developing
---

# M-Wiki

[[M-Wiki]] (the internal working name for [[Project Meeps]]) is an LLM-maintained second brain designed to replace traditional RAG systems. It ingests URLs, PDFs, and images via a [[Discord]] interface, extracting claims and generating interconnected markdown files in an [[Obsidian]] vault.

Architecturally, it relies on [[Hexagonal Architecture]] to separate transport layers from the core domain. Workflows are orchestrated using [[Mastra]], and state sync is handled entirely via Git, ensuring that human-generated notes and agent-generated notes live in separate directories (`raw/` and `wiki/`) to prevent conflicts.

Source: [[phd/wiki/sources/phd2026mwikiprd|M-WIKI-PRD]]
