---
type: map
title: "OAD Mobile Health Application"
aliases: []
tags: [map, phd]
updated: 2026-07-13
status: stable
---

# OAD Mobile Health Application

The [[OAD]] (Outil d'Aide au Diagnostic), formally managed as the [[phd/wiki/entities/oad|OAD]] project ([[phd/wiki/sources/notes2026oad|OAD — Project Hub]]), is a [[phd/wiki/concepts/react-native|React Native]] Android tablet application developed to assist healthcare workers (Agents de Santé) in the Central African Republic and other sub-Saharan African resource-limited medical settings with the clinical diagnosis of non-malarial febrile illnesses. Designed to replace legacy Excel-based systems in environments lacking laboratory infrastructure, it functions as a [[phd/wiki/concepts/syndromic-approach|syndromic diagnostic aid tool]] grounded in a clinical [[Syndromic Approach]]. This method enables workers to diagnose and treat patients based on observed clinical syndromes rather than waiting for laboratory confirmation of infectious agents. To maintain seamless functionality in remote areas without active internet access, the application relies on an [[Offline-First Architecture]]. This [[phd/wiki/concepts/offline-first-architecture|offline-first architecture]] ensures that data reads and writes occur on a local device database, which subsequently synchronizes with remote servers in the background once connectivity is restored. Before finalizing the mobile infrastructure, an early technical comparison was conducted evaluating [[phd/wiki/concepts/react-native|React Native]] against [[phd/wiki/concepts/open-data-kit|ODK]]. The project's core team and stakeholders include Project Responsible [[phd/wiki/entities/romaric-nzoumbou-boko|Pr Romaric Nzoumbou-Boko]], alongside [[phd/wiki/entities/didier-menard|Pr Didier Ménard]] and [[phd/wiki/entities/jean-de-dieu-longo|Pr Jean-de-Dieu Longo]]. The system's diagnostic workflow was designed by [[phd/wiki/entities/patrice-piola|Dr Patrice Piola]], with [[phd/wiki/entities/aboubacar-soumah|Dr Aboubacar Soumah]] serving as Project Manager, and [[phd/wiki/entities/mehdi-el-alaoua|Mehdi El Alaoua]] operating as the primary developer and designer.

## Pages in this area

- [[phd/wiki/entities/oad|OAD]]
- [[phd/wiki/concepts/syndromic-approach|Syndromic Approach]]
- [[phd/wiki/concepts/offline-first-architecture|Offline-First Architecture]]

## From [[phd/wiki/sources/notes2026oadlog|OAD(log) - Beta-Bangui]] (2026-07-13)

## Field Deployment Timeline
- **June 21st**: Target date for equipping tablets with the application and handing them off for internal testing in Bangui, Central African Republic.
- **September**: Target date for the final public launch of version 1.2.0, incorporating feedback (critics) from the internal beta testing.
