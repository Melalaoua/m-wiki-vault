---
type: map
title: "OAD Technical Infrastructure and Evaluation"
aliases: []
tags: [map, phd]
updated: 2026-07-13
status: stable
---

# OAD Technical Infrastructure and Evaluation

The [[OAD]] (Outil d'Aide au Diagnostic) is an offline-first mobile health application developed for Android tablets to assist healthcare workers with syndromic clinical diagnostics for non-malarial febrile illnesses in resource-constrained settings like the Central African Republic. To replace legacy Excel-based tools, the project evaluated two primary infrastructure paths. [[Open Data Kit]] (ODK) offered rapid prototyping capable of deploying offline-first forms with built-in GPS, photo support, and server syncing within a month, but was constrained by rigid UI/UX and relational data limits on free tiers. Custom development using [[React Native]] was ultimately pursued despite requiring higher engineering costs and full-stack expertise (demanding approximately four months for a minimum viable product), as it provided the complete architectural freedom and interactive functionality necessary for complex diagnostic workflows. As documented during the 2026 sprint ([[phd/wiki/sources/notes2026oadlog|OAD(log) - MVP Sprint]]), the [[OAD]] custom architecture utilized [[Tamagui]] tokens for the frontend, heavily assisted by AI multi-agent workflows, alongside a backend implementing [[JWT]] authentication and a [[Caddy]] reverse proxy. Local connectivity challenges with the [[Expo]] development client over USB were bypassed via manual tunneling and deep-linking using `adb reverse`. Furthermore, critical data schema corrections were implemented to ensure auditability for the eventual impact study: diagnostic consultations now snapshot a hash or version of the `pathologies.json` and `treatments.json` rulesets to guarantee historical reproducibility, and `healthStaff` profiles transitioned from device-specific UUIDs to server-issued identities to accurately compute per-clinician socio-economic metrics across distributed devices.

## Pages in this area

- [[phd/wiki/entities/oad|OAD]]
- [[phd/wiki/concepts/open-data-kit|Open Data Kit]]
- [[phd/wiki/concepts/react-native|React Native]]
