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

# OAD(handoff) - product requirements document

This document outlines the Product Requirements Document (PRD) for the [[phd/wiki/entities/oad|OAD]] project (Target Release: 0.1), mapped under the [[phd/wiki/maps/oad-mobile-health-application|OAD Mobile Health Application]].

## Project Objectives
*   **Purpose:** Develop a diagnostic aid tool (OAD) based on a [[phd/wiki/concepts/syndromic-approach|syndromic approach]].
*   **Background:** The increasing use of rapid diagnostic tests for malaria means doctors are confronted with diagnosing more non-malarial febrile diseases, often lacking alternative methods for their management.
*   **Strategic Context:** The team prioritizes UX and platform accessibility for fast-paced medical environments. Crucially, the tool must function reliably in poor regions with limited internet, necessitating an [[phd/wiki/concepts/offline-first-architecture|offline-first architecture]].

## Feature Requirements
*   Developed in [[phd/wiki/concepts/react-native|React Native]] for Android tablets.
*   Full functionality accessible without the internet.
*   Optimized tablet experience with an interactive, guided UI.
*   Local and distant databases with syncing capabilities when internet is restored.
*   Integration of PostHog for deployment monitoring and analytics.

## User Personas
*   Agent de Santé
*   Agent de santé communautaire

## Release Criteria
*   Design an eye-catching, user-friendly interface.
*   Port all existing Excel functions to the app.
*   Ensure the application is fully functional offline.

**Personnel involved:** Pr Romaric NZOUMBOU-BOKO, Pr Didier MENARD, Pr Jean-de-Dieu LONGO, Dr Patrice PIOLA (Document Owners/Designers); Dr Aboubacar SOUMAH (Project Manager); Medhi El alaoua (Designer/Developer).

## Key claims

- The OAD aims to assist in diagnosing non-malarial febrile illnesses by utilizing a syndromic approach. ([[raw/notes/OAD(handoff) - product requirements document#Project objectives:]]) — "Développer un outil d’aide au diagnostic (OAD) basé sur une approche syndromique. [...] La croissance d’utilisation des tests de diagnostic rapide pour la paludisme confronte les médecins au diagnostic de plus en plus de maladies fébriles non palustres"
- The OAD application must be fully functional on a tablet without an internet connection. ([[raw/notes/OAD(handoff) - product requirements document#Feature requirements:]]) — "Full platform functionality accessible from a tablet device without internet."
- The OAD application relies on local and distant databases that synchronize when an internet connection becomes available. ([[raw/notes/OAD(handoff) - product requirements document#Feature requirements:]]) — "Syncing so updates are sent to server when internet is available. (local and distant databases with syncing.)"
- The app is being developed for Android tablets using React Native. ([[raw/notes/OAD(handoff) - product requirements document#Feature requirements:]]) — "App is coded in react native on android tablet."
