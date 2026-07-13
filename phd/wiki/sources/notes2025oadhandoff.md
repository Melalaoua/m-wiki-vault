---
type: source
title: "OAD(handoff) - product requirements document"
citekey: notes2025oadhandoff
source_type: article
captured: 2025-09-12
site: notes
url: 
aliases: []
tags: [source, phd]
updated: 2025-09-12
status: developing
---

# OAD(handoff) - product requirements document

Original: [[raw/notes/OAD(handoff) - product requirements document]]

This document is the Product Requirements Document (PRD) for the [[phd/wiki/entities/oad|OAD]] (Outil d'Aide au Diagnostic), targeting release 0.1. 

## Project Objectives
The primary purpose is to develop a diagnostic tool based on a [[phd/wiki/concepts/syndromic-approach|syndromic approach]]. This is necessitated by the increased use of rapid diagnostic tests for malaria, which leaves doctors facing a growing number of non-malarial febrile illnesses without alternative diagnostic methods. 

The strategic context emphasizes UX and platform accessibility in fast-paced medical field settings. The application must be highly reliable and fully functional in impoverished regions where internet access is intermittent or non-existent.

## Feature Requirements
- Built using [[phd/wiki/concepts/react-native|React Native]] for Android tablets.
- **[[phd/wiki/concepts/offline-first-architecture|Offline-first]]**: Full platform functionality must be accessible without internet connectivity.
- Interactive and guided UI optimized for tablets.
- Data architecture requires local and distant databases with syncing capabilities when internet becomes available.
- Integration with [[phd/wiki/entities/posthog|PostHog]] for deployment monitoring.

## Personas and Release Criteria
The primary users are the *Agent de Santé* (Health Worker) and *Agent de santé communautaire* (Community Health Worker). 

For the 0.1 release, the team must design an eye-catching, user-friendly interface that successfully ports all existing functions from a legacy Excel tool into a standalone, offline-functional app.

## Key claims

- The widespread use of rapid diagnostic tests for malaria has increased the need for doctors to diagnose and manage non-malarial febrile illnesses without adequate alternative methods. ([[raw/notes/OAD(handoff) - product requirements document#Project objectives:]]) — "La croissance d’utilisation des tests de diagnostic rapide pour la paludisme confronte les médecins au diagnostic de plus en plus de maladies fébriles non palustres - sans méthodes ou moyens alternatifs pour leur prise en charge."
- The application must be able to operate entirely offline on a tablet and synchronize data with a server once internet connectivity is restored. ([[raw/notes/OAD(handoff) - product requirements document#Feature requirements:]]) — "Full platform functionality accessible from a tablet device without internet. [...] Syncing so updates are sent to server when internet is available. (local and distant databases with syncing.)"
- The initial release of the app must replicate the functionality currently handled by an existing Excel document. ([[raw/notes/OAD(handoff) - product requirements document#Release criteria:]]) — "Port all excel's existing functions to the app."
