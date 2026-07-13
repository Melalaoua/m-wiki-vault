---
type: map
title: "OAD Mobile Health Application"
aliases: []
tags: [map, phd]
updated: 2025-09-09
status: stable
---

# OAD Mobile Health Application

The [[OAD]] (Outil d'Aide au Diagnostic), formally managed as the [[phd/wiki/entities/oad|OAD]] project ([[phd/wiki/sources/notes2026oad|OAD — Project Hub]]), is a [[phd/wiki/concepts/react-native|React Native]] Android tablet application developed to assist healthcare workers (Agents de Santé) in the Central African Republic and other sub-Saharan African resource-limited medical settings with the clinical diagnosis of non-malarial febrile illnesses. Designed to replace legacy Excel-based systems in environments lacking laboratory infrastructure, it functions as a [[phd/wiki/concepts/syndromic-approach|syndromic diagnostic aid tool]] grounded in a clinical [[Syndromic Approach]]. This method enables workers to diagnose and treat patients based on observed clinical syndromes rather than waiting for laboratory confirmation of infectious agents. Before finalizing the mobile infrastructure, an early technical comparison was conducted evaluating [[phd/wiki/concepts/react-native|React Native]] against [[phd/wiki/concepts/open-data-kit|ODK]]. To maintain seamless functionality in remote areas without active internet access, the application relies on an [[Offline-First Architecture]]. This [[phd/wiki/concepts/offline-first-architecture|offline-first architecture]] ensures that data reads and writes occur on a local device database, which subsequently synchronizes with remote servers in the background once connectivity is restored. The project's core team and stakeholders include Project Responsible [[phd/wiki/entities/romaric-nzoumbou-boko|Pr Romaric Nzoumbou-Boko]], alongside [[phd/wiki/entities/didier-menard|Pr Didier Ménard]] and [[phd/wiki/entities/jean-de-dieu-longo|Pr Jean-de-Dieu Longo]]. The system's diagnostic workflow was designed by [[phd/wiki/entities/patrice-piola|Dr Patrice Piola]], with [[phd/wiki/entities/aboubacar-soumah|Dr Aboubacar Soumah]] serving as Project Manager, and [[phd/wiki/entities/mehdi-el-alaoua|Mehdi El Alaoua]] operating as the primary developer and designer. According to field deployment records ([[phd/wiki/sources/notes2026oadlog|OAD(log) - Beta-Bangui]]), the implementation timeline aimed to equip tablets and initiate internal testing in Bangui by June 21st, targeting a final public launch of version 1.2.0 in September to integrate beta testing feedback.

## Pages in this area

- [[phd/wiki/entities/oad|OAD]]
- [[phd/wiki/concepts/syndromic-approach|Syndromic Approach]]
- [[phd/wiki/concepts/offline-first-architecture|Offline-First Architecture]]

## From [[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - React Native ou ODK]] (2025-09-09)

The [[phd/wiki/entities/oad|OAD]] Mobile Health Application faces a core architectural decision between [[phd/wiki/concepts/open-data-kit|Open Data Kit]] and [[phd/wiki/concepts/react-native|React Native]]. 

**ODK Route**: Prioritizes speed (1 month build) and built-in offline synchronization, but results in static UI and limited dynamic functionality unless a paid version is leveraged for entity management.
**React Native Route**: Prioritizes custom UX, interactive functionality, and design flexibility, but requires a ~4-month full-stack engineering effort (app, server, infrastructure, security).

### Logistical & Operational Factors
- **Hardware:** Tablets are budgeted at ~300€ each, with a target timeline around mid-October. Theft mitigation must be addressed.
- **Team:** Key stakeholders include [[phd/wiki/entities/souma|Souma]] (Project Manager) and [[phd/wiki/entities/romaric|Romaric]] (Project Lead). Collaboration requires upcoming coordination with the team in Bangui.
- **Clinical Goals:** The app must help reduce unnecessary prescriptions, integrate AI for decision support with limited means, and prove its economic interest.
