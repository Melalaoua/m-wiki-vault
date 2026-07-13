---
type: map
title: "OAD Mobile Health Application"
aliases: []
tags: [map, phd]
updated: 2026-07-13
status: stable
---

# OAD Mobile Health Application

The [[OAD]] (Outil d'Aide au Diagnostic), formally managed as the [[phd/wiki/entities/oad|OAD]] project ([[phd/wiki/sources/notes2026oad|OAD — Project Hub]]), is a [[phd/wiki/concepts/react-native|React Native]] Android tablet application designed to assist healthcare workers in the Central African Republic and other sub-Saharan African resource-limited settings with diagnosing non-malarial febrile illnesses. Operating as a [[phd/wiki/concepts/syndromic-approach|syndromic diagnostic aid tool]] grounded in a clinical [[Syndromic Approach]], it enables diagnosis and treatment based on observed clinical syndromes rather than laboratory confirmation, aiming to reduce unnecessary prescriptions, integrate AI decision support with limited means, and demonstrate economic viability. Replacing legacy Excel-based systems, the [[phd/wiki/entities/oad|OAD]] Mobile Health Application relies on an [[Offline-First Architecture]]. This [[phd/wiki/concepts/offline-first-architecture|offline-first architecture]] guarantees uninterrupted functionality in remote areas by reading and writing to a local device database, syncing with remote servers when connectivity is restored. Early technical scoping ([[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - React Native ou ODK]]) compared [[phd/wiki/concepts/react-native|React Native]] against [[phd/wiki/concepts/open-data-kit|Open Data Kit]] (commonly referred to as [[phd/wiki/concepts/open-data-kit|ODK]]). While the ODK route offered a fast one-month build and built-in offline synchronization, it yielded a static UI and limited dynamic capabilities without paid tier entity management. The chosen [[phd/wiki/concepts/react-native|React Native]] approach prioritized custom UX, interactive functionality, and design flexibility, requiring a four-month full-stack engineering investment encompassing app, server, infrastructure, and security development. The core team includes Project Responsible/Lead [[phd/wiki/entities/romaric-nzoumbou-boko|Pr Romaric Nzoumbou-Boko]] (noted in coordination logistics as [[phd/wiki/entities/romaric|Romaric]]), Project Manager [[phd/wiki/entities/aboubacar-soumah|Dr Aboubacar Soumah]] ([[phd/wiki/entities/souma|Souma]]), [[phd/wiki/entities/didier-menard|Pr Didier Ménard]], and [[phd/wiki/entities/jean-de-dieu-longo|Pr Jean-de-Dieu Longo]]. The system's diagnostic workflow was designed by [[phd/wiki/entities/patrice-piola|Dr Patrice Piola]], while [[phd/wiki/entities/mehdi-el-alaoua|Mehdi El Alaoua]] serves as the primary developer and designer. Field deployment records ([[phd/wiki/sources/notes2026oadlog|OAD(log) - Beta-Bangui]]) outline a hardware strategy utilizing tablets budgeted at ~300€ each, which requires explicit theft mitigation. The implementation timeline targets equipping these tablets for internal testing with the team in Bangui by June 21st, scaling toward mid-October logistical targets and a final public launch of version 1.2.0 in September to integrate beta feedback.

## Pages in this area

- [[phd/wiki/entities/oad|OAD]]
- [[phd/wiki/concepts/syndromic-approach|Syndromic Approach]]
- [[phd/wiki/concepts/offline-first-architecture|Offline-First Architecture]]
