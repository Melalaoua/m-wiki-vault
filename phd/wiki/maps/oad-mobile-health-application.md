---
type: map
title: "OAD Mobile Health Application"
aliases: []
tags: [map, phd]
updated: 2025-09-12
status: stable
---

# OAD Mobile Health Application

The [[OAD]] (Outil d'Aide au Diagnostic), formally managed as the [[phd/wiki/entities/oad|OAD]] project ([[phd/wiki/sources/notes2026oad|OAD — Project Hub]]), is a [[phd/wiki/concepts/react-native|React Native]] Android tablet application designed to assist healthcare workers in the Central African Republic and other resource-limited sub-Saharan settings. Operating as a [[phd/wiki/concepts/syndromic-approach|syndromic diagnostic aid tool]] grounded in a clinical [[Syndromic Approach]], it enables the diagnosis and treatment of non-malarial febrile illnesses based on observed clinical syndromes rather than laboratory confirmation. This aims to reduce unnecessary prescriptions, integrate AI decision support, and demonstrate economic viability. Replacing legacy Excel-based systems, the [[phd/wiki/entities/oad|OAD]] mobile application utilizes an [[Offline-First Architecture]]. This [[phd/wiki/concepts/offline-first-architecture|offline-first architecture]] guarantees uninterrupted functionality in remote areas by reading and writing to a local device database, then syncing with remote servers when connectivity is restored. Early technical scoping ([[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - React Native ou ODK]]) compared [[phd/wiki/concepts/react-native|React Native]] against [[phd/wiki/concepts/open-data-kit|Open Data Kit]] (commonly referred to as [[phd/wiki/concepts/open-data-kit|ODK]]). While the ODK route offered a fast one-month build with built-in offline synchronization, it yielded a static UI and limited dynamic capabilities without paid tier entity management. Consequently, the chosen [[phd/wiki/concepts/react-native|React Native]] approach prioritized custom UX, interactive functionality, and design flexibility, necessitating a four-month full-stack engineering investment encompassing app, server, infrastructure, and security development. The project is spearheaded by Project Lead [[phd/wiki/entities/romaric-nzoumbou-boko|Pr Romaric Nzoumbou-Boko]] (noted in coordination logistics as [[phd/wiki/entities/romaric|Romaric]]), Project Manager [[phd/wiki/entities/aboubacar-soumah|Dr Aboubacar Soumah]] ([[phd/wiki/entities/souma|Souma]]), [[phd/wiki/entities/didier-menard|Pr Didier Ménard]], and [[phd/wiki/entities/jean-de-dieu-longo|Pr Jean-de-Dieu Longo]]. The system's diagnostic workflow was designed by [[phd/wiki/entities/patrice-piola|Dr Patrice Piola]], while [[phd/wiki/entities/mehdi-el-alaoua|Mehdi El Alaoua]] serves as the primary developer and designer. Field deployment records ([[phd/wiki/sources/notes2026oadlog|OAD(log) - Beta-Bangui]]) outline a hardware strategy utilizing tablets budgeted at ~300€ each, which requires explicit theft mitigation. The implementation timeline targets equipping these tablets for internal testing in Bangui by June 21st, ahead of a version 1.2.0 public launch in September to integrate beta feedback, ultimately scaling toward mid-October logistical targets.

## Pages in this area

- [[phd/wiki/entities/oad|OAD]]
- [[phd/wiki/concepts/syndromic-approach|Syndromic Approach]]
- [[phd/wiki/concepts/offline-first-architecture|Offline-First Architecture]]

## From [[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - product requirements document]] (2025-09-12)

The development of the [[phd/wiki/entities/oad|OAD]] application focuses on translating clinical algorithms—originally managed in Excel—into an accessible, interactive tablet UI. Core product requirements emphasize an [[phd/wiki/concepts/offline-first-architecture|offline-first architecture]] with local and remote database syncing, tailored for *Agents de Santé* and *Agents de santé communautaire*. The technical stack relies on [[phd/wiki/concepts/react-native|React Native]] for Android and PostHog for deployment monitoring.

## From [[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - product requirements document]] (2025-09-12)

The **OAD Mobile Health Application** translates a diagnostic [[phd/wiki/concepts/syndromic-approach|Syndromic Approach]] into a functional software tool for Android tablets. 

### Technical and Product Requirements
- **Framework:** Coded in [[phd/wiki/concepts/react-native|React Native]].
- **Offline Functionality:** Requires an [[phd/wiki/concepts/offline-first-architecture|Offline-First Architecture]] featuring local database syncing to distant servers when connectivity allows.
- **UX Focus:** Designed for 'Agents de Santé' and Community Health Agents. It emphasizes an interactive, guided UI suitable for fast-paced medical environments.
- **Analytics:** Uses [[phd/wiki/entities/posthog|PostHog]] for deployment monitoring.
- **Release Criteria:** The first release must successfully port all existing Excel-based diagnostic functions to the offline app.
