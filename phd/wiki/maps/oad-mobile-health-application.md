---
type: map
title: "OAD Mobile Health Application"
aliases: []
tags: [map, phd]
updated: 2026-07-13
status: stable
---

# OAD Mobile Health Application

The [[OAD]] (Outil d'Aide au Diagnostic) is a React Native Android tablet application developed to assist healthcare workers (Agents de Santé) in the Central African Republic with the clinical diagnosis of non-malarial febrile illnesses. Built for resource-constrained environments that lack laboratory infrastructure, the tool replaces legacy Excel-based systems by utilizing a [[Syndromic Approach]]. This method allows workers to diagnose and treat patients based on observed clinical syndromes rather than waiting for laboratory confirmation of infectious agents. To maintain seamless functionality in remote areas without active internet access, the application is built on an [[Offline-First Architecture]]. This software design paradigm ensures that data reads and writes occur on a local device database, which then synchronizes with remote servers in the background once connectivity is restored.

## Pages in this area

- [[phd/wiki/entities/oad|OAD]]
- [[phd/wiki/concepts/syndromic-approach|Syndromic Approach]]
- [[phd/wiki/concepts/offline-first-architecture|Offline-First Architecture]]

## From [[phd/wiki/sources/notes2026oad|OAD — Project Hub]] (2026-07-13)

The [[phd/wiki/entities/oad|OAD]] (Outil d'Aide au Diagnostic) project aims to provide a [[phd/wiki/concepts/syndromic-approach|syndromic diagnostic aid tool]] through a [[phd/wiki/concepts/react-native|React Native]] tablet application. It is specifically designed to function with an [[phd/wiki/concepts/offline-first-architecture|offline-first architecture]] to serve resource-limited medical settings, notably in sub-Saharan Africa.

### Core Team & Stakeholders
- [[phd/wiki/entities/romaric-nzoumbou-boko|Pr Romaric Nzoumbou-Boko]] (Project Responsible)
- [[phd/wiki/entities/didier-menard|Pr Didier Ménard]]
- [[phd/wiki/entities/jean-de-dieu-longo|Pr Jean-de-Dieu Longo]]
- [[phd/wiki/entities/patrice-piola|Dr Patrice Piola]] (Designer)
- [[phd/wiki/entities/aboubacar-soumah|Dr Aboubacar Soumah]] (Project Manager)
- [[phd/wiki/entities/mehdi-el-alaoua|Mehdi El Alaoua]] (Developer & Designer)

### Technical Decisions
An early technical comparison was made between [[phd/wiki/concepts/react-native|React Native]] and [[phd/wiki/concepts/open-data-kit|ODK]] to determine the best approach for the mobile infrastructure.
