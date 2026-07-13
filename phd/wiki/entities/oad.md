---
type: entity
title: "OAD"
aliases: []
tags: [entity, phd]
updated: 2025-09-12
status: stable
---

# OAD

The **OAD** (Outil d'Aide au Diagnostic) is a mobile health initiative developing an [[phd/wiki/concepts/offline-first-architecture|offline-first]] tablet application to assist healthcare workers (Agents de Santé) with clinical diagnosis in resource-constrained medical settings across sub-Saharan Africa, such as the Central African Republic ([[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - product requirements document]], [[phd/wiki/sources/notes2026oad|OAD — Project Hub]]). Built to replace legacy Excel-based tools, the software acts as a [[phd/wiki/concepts/syndromic-approach|syndromic diagnostic]] aid utilizing a [[phd/wiki/concepts/syndromic-approach|syndromic approach]] to manage conditions like non-malarial febrile illnesses ([[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - product requirements document]], [[phd/wiki/sources/notes2026oad|OAD — Project Hub]]). Developed for Android tablets in [[phd/wiki/concepts/react-native|React Native]], it implements an [[phd/wiki/concepts/offline-first-architecture|offline-first architecture]] that enables practitioners to work without internet access, syncing local databases to remote servers once connectivity is restored ([[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - product requirements document]], [[phd/wiki/sources/notes2026oad|OAD — Project Hub]]). A comprehensive overview of stakeholders and scope is documented in the [[phd/wiki/maps/oad-mobile-health-application|OAD Mobile Health Application]] (or [[phd/wiki/maps/oad-mobile-health-application|oad-mobile-health-application]]) project map ([[phd/wiki/sources/notes2026oad|OAD — Project Hub]]).

## From [[phd/wiki/sources/notes2026oadlog|OAD(log) - MVP Sprint]] (2026-07-13)

The [[OAD]] (Outil de Diagnostic) reached its MVP milestone in late May 2026, targeted for a field deployment in early June. Its [[OAD Mobile Health Application|mobile client]] and server backend were heavily accelerated through the adoption of multi-agent AI coding workflows (using tools like [[Claude|Claude Code]] and [[Claude|Claude Design]]).

A critical evolution during the MVP phase involved discarding untyped, legacy Excel files for pathology/treatment mapping in favor of a robust, internal typing system to avoid logic-breaking bugs.

## From [[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - product requirements document]] (2025-09-12)

The OAD (Outil d'aide au diagnostic) is a diagnostic aid tool documented in the [[phd/wiki/maps/oad-mobile-health-application|OAD Mobile Health Application]] map. Its v0.1 PRD specifies a tablet-based [[phd/wiki/concepts/react-native|React Native]] application leveraging an [[phd/wiki/concepts/offline-first-architecture|offline-first architecture]] to support a [[phd/wiki/concepts/syndromic-approach|syndromic approach]] in fast-paced medical settings with poor internet connectivity.
