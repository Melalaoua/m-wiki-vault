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

Link to figma PRD : https://www.figma.com/board/iIu27enlCVIRwyJt7ysKoY/OAD-PRD?node-id=0-1&t=1EWlWScBIM8ief2C-1

Project: [[phd/wiki/entities/oad|OAD]]
Target release: 0.1
Document owner: Pr Romaric NZOUMBOU-BOKO & Pr Didier MENARD & Pr Jean-de-Dieu LONGO | Dr Patrice PIOLA
Project manager: Dr Aboubacar SOUMAH
Designer: Medhi El alaoua, Dr Patrice PIOLA
Developer: Medhi El alaoua

**Project objectives:**
- **Purpose:** Développer un outil d’aide au diagnostic (OAD) basé sur une approche syndromique ([[phd/wiki/concepts/syndromic-approach|Syndromic Approach]]).
- **Background:** La croissance d’utilisation des tests de diagnostic rapide pour la paludisme confronte les médecins au diagnostic de plus en plus de maladies fébriles non palustres - sans méthodes ou moyens alternatifs pour leur prise en charge.
- **Strategic context:** We’re prioritizing UX and platform accessibility. The field where the app will be delivered is medical with fast-paced settings. So releasing a tablet app with ease-of-use, clear design and main UX is important. But non only, the OAD needs to be reliable and functional, in poor regions where internet is not always accessible.

**Feature requirements:**
- App is coded in [[phd/wiki/concepts/react-native|React Native]] on android tablet.
- Full platform functionality accessible from a tablet device without internet ([[phd/wiki/concepts/offline-first-architecture|Offline-First Architecture]]).
- A fully-fedged interface optimized for the tablet experience.
- Interactive & guided UI.
- Syncing so updates are sent to server when internet is available. (local and distant databases with syncing.)
- Integrates [[phd/wiki/entities/posthog|PostHog]] to the app for monitoring/deployment purposes

**User personas:**
- Agent de Santé
- Agent de santé communautaire

**Release criteria:**
- Design an eye-catching, user-friendly interface.
- Port all excel's existing functions to the app.
- App functional without internet.

## Key claims

- The OAD tool is necessitated by the rise of rapid diagnostic tests for malaria, which leaves doctors needing alternative methods to diagnose non-malarial febrile illnesses. ([[raw/notes/OAD(handoff) - product requirements document#Project objectives]]) — "La croissance d’utilisation des tests de diagnostic rapide pour la paludisme confronte les médecins au diagnostic de plus en plus de maladies fébriles non palustres - sans méthodes ou moyens alternatifs pour leur prise en charge."
- The OAD application must be fully functional on a tablet without an internet connection. ([[raw/notes/OAD(handoff) - product requirements document#Feature requirements]]) — "Full platform functionality accessible from a tablet device without internet."
- The application will sync local data to distant databases once an internet connection is available. ([[raw/notes/OAD(handoff) - product requirements document#Feature requirements]]) — "Syncing so updates are sent to server when internet is available. (local and distant databases with syncing.)"
