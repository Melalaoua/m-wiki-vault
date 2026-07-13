---
type: map
title: "OAD Technical Infrastructure and Evaluation"
aliases: []
tags: [map, phd]
updated: 2026-07-13
status: stable
---

# OAD Technical Infrastructure and Evaluation

The [[OAD]] (Outil d'Aide au Diagnostic) is an offline-first mobile health application developed for Android tablets to assist healthcare workers with syndromic clinical diagnostics for non-malarial febrile illnesses in resource-constrained settings like the Central African Republic. During the project's technical evaluation, two primary infrastructure paths were compared for replacing legacy Excel-based tools. [[Open Data Kit]] (ODK) was assessed as a rapid-prototyping data collection suite capable of deploying offline-first forms with built-in GPS, photo support, and server syncing within a month, though it was noted to be limited by rigid UI/UX and relational data constraints on free tiers. Conversely, custom development using [[React Native]] was evaluated as the alternative path. While React Native demands a higher engineering cost and full-stack expertise—requiring approximately four months for a minimum viable product—it provides the complete architectural freedom, interactive functionality, and unrestricted UI/UX design required for the application's diagnostic workflows.

## Pages in this area

- [[phd/wiki/entities/oad|OAD]]
- [[phd/wiki/concepts/open-data-kit|Open Data Kit]]
- [[phd/wiki/concepts/react-native|React Native]]

## From [[phd/wiki/sources/notes2026oadlog|OAD(log) - MVP Sprint]] (2026-07-13)

## MVP Architecture
During the 2026 MVP sprint, the [[OAD]] infrastructure adopted several structural changes:
- **Frontend:** Transitioned to [[Tamagui]] tokens for the UI, with development heavily assisted by AI multi-agent workflows.
- **Authentication & Backend:** Implemented [[JWT]] based authentication alongside a [[Caddy]] reverse proxy.
- **Connectivity:** Addressed [[Expo]] dev client discovery issues over USB by manually tunneling and deep-linking using `adb reverse`.

## Auditability and Synchronization Caveats
Crucial flaws in the data schema were detected and corrected to ensure the viability of the eventual impact study:
- **Ruleset Versioning:** Consultations must snapshot a hash or version of the `pathologies.json` and `treatments.json` files to ensure past diagnostics can be reproduced or audited.
- **Staff Syncing:** Initially, `healthStaff` instances generated device-specific UUIDs that weren't globally synced. This required server-issued staff identities to correctly compute per-clinician socio-economic metrics across devices.
