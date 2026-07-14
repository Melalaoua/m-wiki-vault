---
type: entity
title: "OAD"
aliases: []
tags: [entity, phd]
updated: 2025-09-12
status: stable
---

# OAD

The **[[OAD]]** (Outil d'Aide au Diagnostic, or Outil de Diagnostic) is a mobile health initiative that developed an [[phd/wiki/concepts/offline-first-architecture|offline-first]] Android tablet application to assist healthcare workers (Agents de Santé) with clinical diagnosis in fast-paced, resource-constrained medical settings across sub-Saharan Africa, such as the Central African Republic ([[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - product requirements document]], [[phd/wiki/sources/notes2026oad|OAD — Project Hub]]). Built in [[phd/wiki/concepts/react-native|React Native]], the software functions as a [[phd/wiki/concepts/syndromic-approach|syndromic diagnostic]] aid using a [[phd/wiki/concepts/syndromic-approach|syndromic approach]] to manage conditions like non-malarial febrile illnesses. Its v0.1 PRD specifies an [[phd/wiki/concepts/offline-first-architecture|offline-first architecture]] that enables practitioners to work without internet connectivity, syncing local databases to remote servers once access is restored ([[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - product requirements document]], [[phd/wiki/sources/notes2026oad|OAD — Project Hub]]). A comprehensive overview of stakeholders and scope is documented in the [[phd/wiki/maps/oad-mobile-health-application|OAD Mobile Health Application]] (or [[phd/wiki/maps/oad-mobile-health-application|oad-mobile-health-application]]) project map. The project reached its MVP milestone in late May 2026, targeting field deployment by early June ([[phd/wiki/sources/notes2026oadlog|OAD(log) - MVP Sprint]]). Development of the server backend and the [[OAD Mobile Health Application|mobile client]] was heavily accelerated through the adoption of multi-agent AI coding workflows using tools like [[Claude|Claude Code]] and [[Claude|Claude Design]] ([[phd/wiki/sources/notes2026oadlog|OAD(log) - MVP Sprint]]). A critical evolution during the MVP phase involved discarding legacy, untyped Excel files for pathology and treatment mapping in favor of a robust, internal typing system to prevent logic-breaking bugs ([[phd/wiki/sources/notes2026oadlog|OAD(log) - MVP Sprint]]).

## From [[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - product requirements document]] (2025-09-12)

The **OAD** (Outil d’aide au diagnostic) is a diagnostic support tool designed to assist healthcare workers in fast-paced, low-resource medical settings, particularly addressing non-malarial febrile illnesses via a [[phd/wiki/concepts/syndromic-approach|Syndromic Approach]]. 

Key stakeholders include document owners (Pr Romaric NZOUMBOU-BOKO, Pr Didier MENARD, Pr Jean-de-Dieu LONGO, Dr Patrice PIOLA) and project manager Dr Aboubacar SOUMAH. The initial v0.1 targets Android tablets and heavily relies on an [[phd/wiki/concepts/offline-first-architecture|Offline-First Architecture]] to function without reliable internet.
