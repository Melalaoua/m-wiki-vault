---
title: MeepsScribe — Run 1 — Phases 0 to 3 Implementation
date: 2026-03-20
type: experiment
status: evergreen
tags:
  - experiment
  - AI
  - software-development
  - knowledge-management
  - discord-bot
  - LLM-tooling
experiment-id: EXP-001
run: 1
hypothesis: Building a Discord-based AI agent with direct access to GitHub-hosted Obsidian vaults will reduce the friction of knowledge capture enough to make real-time note creation sustainable during active PhD work.
related: []
---

## Objective

I am trying to build and validate MeepsScribe — a Discord bot backed by a Mastra AI agent — capable of reading, searching, and writing notes across my two Obsidian vaults (PhD and Personal) via GitHub integration. This first run covers the full development arc from Phase 0 (Git infrastructure) through Phase 3 (full PhD command set), tracking what was built, what worked, and what required significant iteration. The overarching goal is to determine whether an LLM-assisted bot, operating through a familiar chat interface, can function as a reliable and low-friction extension of my knowledge management system.

## Hypothesis

I predict that structuring the bot in four incremental phases — Git scaffolding, Discord skeleton, LLM-powered note creation, and full PhD command set — will allow me to validate each layer independently before adding complexity, resulting in a working Phase 1–3 system within approximately 20 days of active development (reduced to 1 day using AI). I further predict that the Discord interaction model (slash commands + confirmation buttons) will feel natural enough to use during actual research sessions, not just as a demonstration.

## Setup & Parameters

| Parameter            | Value                                                                                                                                                |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Hardware / Compute   | VPS (bot hosting) + local machine (development)                                                                                                      |
| Framework / Library  | Mastra (`@mastra/core`, `@mastra/anthropic`), Discord.js, simple-git, Zod, TypeScript / tsx                                                          |
| Dataset              | Two Obsidian vaults: `bios-phd` (GitHub) and `bios-personal` (GitHub); data layer not synced between vaults                                          |
| Model / Architecture | Claude Opus 4.6 (planning sessions) + Claude Sonnet 4.6 (implementation sessions), via Anthropic API; Mastra agent with filesystem + sandbox tooling |
| Key hyperparameters  | Obsidian Git auto-sync: 5-min interval; Git commit triggered after every note write; Discord confirmation timeout: not yet fixed                     |
| Random seed          | N/A — no stochastic training involved                                                                                                                |

## Protocol

1. **Phase 0 — Git infrastructure.** Initialize separate Git repositories for `_Personal/` and `_PhD/` vaults. Configure `.gitignore` to exclude Obsidian workspace state files (`.obsidian/workspace.json`, `.obsidian/cache`, `.trash/`, `.DS_Store`). Push both repos to GitHub. Install Obsidian Git plugin in both vaults with 5-minute auto-sync. Copy `AGENT.md` and `TAG-REGISTRY.md` to root of each repo. Convert `AGENT.md` files to `SKILL.md` format by adding Mastra-compatible frontmatter.

2. **Phase 1 — Mastra + Discord skeleton.** Scaffold the `bios-bot` project with `npm init`, install all dependencies (`@mastra/core`, `@mastra/anthropic`, `discord.js`, `simple-git`, `dotenv`, `zod`, and TypeScript dev tools). Build a Discord.js bot responding to `/ping`. Create two Mastra workspaces (PhD + Personal) with filesystem and sandbox access. Clone both GitHub repos on bot startup; pull on `/sync` command. Implement `/read` (filesystem.readFile), `/search` (BM25 workspace search), and `/status` (filesystem.listFiles). **No LLM calls at this stage.** Goal is to validate the workspace-git loop end-to-end before adding intelligence.

3. **Phase 2 — LLM-powered note creation.** Load `SKILL.md` instructions into agent context (the full AGENT.md convention chain). Wire the agent to use filesystem + search tools for context retrieval before generating notes. Implement `/journal` (single-workspace, single-template — used as minimal test case) and `/note` (general-purpose command with workspace routing logic). After every successful note write, trigger a Git commit and push via sandbox. Add a Discord confirmation flow using interactive buttons: bot sends a preview embed → user clicks ✅ Save or ❌ Cancel before the file is committed.

4. **Phase 3 — Full PhD command set.** Implement `/meeting`, `/paper`, `/experiment`, and `/idea` slash commands, each routing to the appropriate template and folder per `CONVENTIONS.md`. Add `/paper` URL and PDF attachment processing: bot fetches paper metadata from URL or extracts text from PDF, then generates a literature note pre-filled with title, authors, venue, and year. Implement `/inbox` to list all notes tagged `#inbox`. Implement `/append` to add timestamped content to an existing note without overwriting. Implement `/tag` to list registered tags from `TAG-REGISTRY.md` and register new ones. Add interactive conversation mode via Discord message collectors for multi-turn note construction.

5. **Throughout all phases.** All design decisions, architecture choices, and implementation blockers were discussed interactively with Claude (Opus for planning, Sonnet for implementation) using the Claude Cowork feature across multiple sessions. Opus generated the initial file structure and the handoff document used to brief subsequent sessions.

## Raw Results

```
Phase 0: COMPLETE
- bios-phd and bios-personal repos initialized and pushed to GitHub
- .gitignore configured for both
- Obsidian Git plugin active, 5-min auto-sync confirmed working
- AGENT.md → SKILL.md conversion done for both vaults

Phase 1: COMPLETE
- /ping responds correctly
- Both Mastra workspaces boot without error
- Git clone on startup: working
- /sync (git pull): working
- /read, /search, /status: working
- No LLM calls introduced yet — skeleton validated

Phase 2: COMPLETE BUT PARTLY TESTED
- SKILL.md loaded into agent context
- /journal: NOT TESTED
- /note: working — routes to PhD or Personal vault based on content classification
- Confirmation button flow (✅/❌): working
- Git commit + push post-write: working

Phase 3: COMPLETE BUT NOT TESTED (core commands)
- /meeting, /idea: NOT TESTED 
- /paper (URL): NOT TESTED
- /paper (PDF): NOT TESTED
- /inbox: working
- /append: NOT TESTED
- /tag: NOT TESTED
- Interactive conversation mode: NOT TESTED

```

## Analysis

The phased approach validated cleanly — each layer built on the previous without requiring retroactive structural changes, which confirms the hypothesis about incremental validation. The Git-first architecture (Phase 0) turned out to be the correct bet: having the vault accessible as a plain filesystem on the VPS simplified every subsequent Mastra tool integration significantly. There was no need to build a custom sync layer.

Opus was most useful for high-level architecture decisions and generating the handoff document; Sonnet handled implementation efficiently. The multi-session nature of development via Cowork introduced continuity challenges — each session required re-briefing, which is part of what MeepsScribe itself is designed to solve long-term.

Phase 3 needs to be more tested.