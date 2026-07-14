---
type: entity
title: "OAD"
aliases: []
tags: [entity, phd]
updated: 2026-07-14
status: stable
---

# OAD

The **[[OAD]]** (Outil d'Aide au Diagnostic, or Outil de Diagnostic) is a mobile health initiative providing an Android tablet application to assist healthcare workers (Agents de Santé) with clinical diagnosis in fast-paced, resource-constrained medical settings across sub-Saharan Africa, notably the Central African Republic. The scope and key stakeholders—including document owners Pr Romaric NZOUMBOU-BOKO, Pr Didier MENARD, Pr Jean-de-Dieu LONGO, Dr Patrice PIOLA, and project manager Dr Aboubacar SOUMAH—are mapped in the [[phd/wiki/maps/oad-mobile-health-application|OAD Mobile Health Application]] (or [[phd/wiki/maps/oad-mobile-health-application|oad-mobile-health-application]]) project overview ([[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - product requirements document]]). 

The v0.1 software is built in [[phd/wiki/concepts/react-native|React Native]] and functions as a [[phd/wiki/concepts/syndromic-approach|syndromic diagnostic]] aid. By relying on a core [[phd/wiki/concepts/syndromic-approach|syndromic approach]] (formalized as a [[phd/wiki/concepts/syndromic-approach|Syndromic Approach]]), it helps practitioners manage and treat conditions such as non-malarial febrile illnesses ([[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - product requirements document]], [[phd/wiki/sources/notes2026oad|OAD — Project Hub]]). To circumvent unreliable internet connectivity, the application integrates an [[phd/wiki/concepts/offline-first-architecture|offline-first]] design. This [[phd/wiki/concepts/offline-first-architecture|Offline-First Architecture]] (or general [[phd/wiki/concepts/offline-first-architecture|offline-first architecture]]) enables practitioners to continue working locally, automatically syncing local databases to remote servers once internet access is restored ([[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - product requirements document]], [[phd/wiki/sources/notes2026oad|OAD — Project Hub]]).

The project achieved its MVP milestone in late May 2026, targeting field deployment by early June. Development of the server backend and the [[OAD Mobile Health Application|mobile client]] was significantly accelerated through multi-agent AI coding workflows utilizing tools like [[Claude|Claude Code]] and [[Claude|Claude Design]]. During the MVP sprint, the team also made a critical architectural pivot by discarding legacy, untyped Excel files previously used for pathology and treatment mapping in favor of a robust internal typing system, successfully preventing logic-breaking bugs ([[phd/wiki/sources/notes2026oadlog|OAD(log) - MVP Sprint]]).
