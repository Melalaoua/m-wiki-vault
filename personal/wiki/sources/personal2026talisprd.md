---
type: source
title: "TALIS-PRD"
citekey: personal2026talisprd
source_type: pdf
captured: 2026-07-13
site: personal
url: 
aliases: []
tags: [source, personal]
updated: 2026-07-13
status: developing
---

# TALIS-PRD

Original: [[personal/raw/personal/TALIS-PRD.pdf]]

The `TALIS-PRD` document is the foundational Product Requirements Document for [[personal/wiki/concepts/talis-ai-agent|Talis]], a specialized AI agent designed for personal financial automation. The system operates as a private Discord bot that automatically ingests and categorizes financial transactions via a dedicated Gmail inbox. It provides robust capabilities for expense tracking, budget enforcement, computing [[personal/wiki/concepts/fire-financial-independence-retire-early|FIRE]] progress, and acting as an advisor for a [[personal/wiki/concepts/pea-investing|PEA]] portfolio. Structurally, the project employs a [[personal/wiki/concepts/hexagonal-architecture|Hexagonal architecture]] with the [[personal/wiki/concepts/mastra-framework|Mastra framework]] powering its internal intelligence layer. A core tenet of the design is strict safety: Talis never moves money, nor does it connect to third-party bank scraping APIs. It enforces a strict end-to-end testing philosophy, validating only externally observable behaviors. The overall integration of this financial maturity effort is tracked in the [[personal/wiki/maps/personal|Personal]] map.

## Key claims

- Talis centralizes financial data by operating as a private Discord bot that automatically parses emails into categorized transactions. ([[personal/raw/personal/TALIS-PRD.pdf#page=1]]) — "A private Discord bot backed by a database that becomes the single source of truth for my finances. It reads my finance inbox and turns emails into categorized transactions automatically"
- The agent calculates FIRE metrics by determining an FI number based on a rolling twelve-month expense history and a savings rate derived from income and outflows. ([[personal/raw/personal/TALIS-PRD.pdf#page=4]]) — "As a FIRE aspirant, I want my FI number derived from rolling twelve-month expense-flow spending and my withdrawal-rate assumption, so that the target reflects how I actually live."
- Talis functions purely as an advisory system and is completely barred from executing any financial trades. ([[personal/raw/personal/TALIS-PRD.pdf#page=6]]) — "As a PEA investor, I want every recommendation framed as decision support that I execute manually at my broker, so that no system ever moves my money."
- The core application uses a hexagonal architecture embedded with Mastra, ensuring business logic remains decoupled from adapters. ([[personal/raw/personal/TALIS-PRD.pdf#page=7]]) — "Hexagonal architecture: the application core is driven exclusively by three inbound events... no business logic in adapters... Mastra, embedded as a library inside the hexagonal boundary."
- Testing strategies for Talis are strictly end-to-end, evaluating only external inputs and outputs without mocking internal functions. ([[personal/raw/personal/TALIS-PRD.pdf#page=10]]) — "A good test exercises only externally observable behavior... Tests never inspect internal modules, call internal functions, or mock internal collaborators."
