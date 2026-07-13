---
type: source
title: "M-WIKI-PRD"
citekey: phd2026mwikiprd
source_type: pdf
captured: 2026-07-13
site: phd
url: 
aliases: []
tags: [source, phd]
updated: 2026-07-13
status: developing
---

# M-WIKI-PRD

Original: [[phd/raw/phd/M-WIKI-PRD.pdf]]

This document is the foundational Product Requirements Document (PRD) for [[M-Wiki]] (also known as [[Project Meeps]]), a system designed to automate the bookkeeping of a researcher's second brain. Instead of relying on raw document retrieval (RAG) at query time, M-Wiki employs an LLM agent to incrementally ingest sources into a heavily interlinked [[Obsidian]] markdown vault.

### Core Architecture
The system is built on [[Hexagonal Architecture]], isolating the core wiki domain from its interfaces. It uses a single driving port (primarily a [[Discord]] adapter) and multiple driven ports ([[Mastra]] for LLM interactions, Git for syncing, and local file system access). Intent is resolved via [[Tool-Selection Routing]] rather than keyword matching, allowing the agent to dynamically compose operations like `captureSource`, `ingestSource`, `queryWiki`, and `runLint`.

### Data Model and Sync
Rather than splitting life areas into different vaults, the system uses a single unified vault to encourage cross-pollination between personal notes and [[PhD]] research. Domain boundaries are handled entirely via frontmatter tags (e.g., `tags: [phd]`). Data taxonomy is split into four primary page types: Source, Entity, Concept, and Map. The canonical state is stored on a cloud VPS and synced to end-user devices (laptop, phone) using Git, with a strict ownership invariant: the agent only writes to `wiki/` and the user only writes to `raw/`, avoiding merge conflicts.

### Testing Strategy
The PRD dictates that testing should verify external, observable behaviors rather than internal function calls. By stubbing only the LLM and the network/Discord boundaries, tests can run end-to-end assertions against a real temporary filesystem and Git repository.

## Key claims

- The system replaces RAG with an incremental compilation model that writes directly to structured markdown files. ([[phd/raw/phd/M-WIKI-PRD.pdf#page=1]]) — "Instead of retrieving from raw documents at query time (RAG), the agent incrementally compiles my sources into a structured, interlinked wiki of markdown files and then keeps it current."
- The core application logic uses a hexagonal architecture where Discord is merely a driving adapter. ([[phd/raw/phd/M-WIKI-PRD.pdf#page=6]]) — "Overall architecture — hexagonal (ports & adapters). The wiki domain (the four operations plus their Mastra workflows) is the core. It is reached only through a driving port and reaches the outside world only through driven ports."
- Agent routing abandons keyword triggers in favor of LLM tool selection. ([[phd/raw/phd/M-WIKI-PRD.pdf#page=7]]) — "Intent routing via tool selection (revises the earlier keyword-trigger decision). The core's conversational agent is given the operations as tools [...] and routes by *choosing which tool(s) to call* from the InboundMessage."
- Domain separation between personal and PhD knowledge relies on metadata tags rather than separate directories. ([[phd/raw/phd/M-WIKI-PRD.pdf#page=9]]) — "Domain (personal vs phd) is a frontmatter tag, not a folder, so cross-domain pages need not pick a home."
- Tests validate side-effects against a real file system and git repository rather than mocking storage. ([[phd/raw/phd/M-WIKI-PRD.pdf#page=11]]) — "Everything else — Vault filesystem, VCS git, Search BM25 — runs for real against a temp fixture vault in each test, because those are exactly the effects we care about."
