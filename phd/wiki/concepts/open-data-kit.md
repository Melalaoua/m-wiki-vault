---
type: concept
title: "Open Data Kit"
aliases: []
tags: [concept, phd]
updated: 2025-09-09
status: developing
---

# Open Data Kit

**Open Data Kit (ODK)** is an open-source set of tools for data collection in resource-constrained environments. It was evaluated as a potential infrastructure for the [[phd/wiki/maps/oad-mobile-health-application|OAD Mobile Health Application]], and compared against custom development via [[phd/wiki/concepts/react-native|React Native]].

Source: [[phd/wiki/sources/notes2026oad|OAD — Project Hub]]

## From [[phd/wiki/sources/notes2025oadhandoff|OAD(handoff) - React Native ou ODK]] (2025-09-09)

[[phd/wiki/concepts/open-data-kit|Open Data Kit]] (ODK) is a suite of tools for data collection that supports forms via XLS (Excel/Google Sheets) or web formats. 

**Capabilities**: It natively handles photos, GPS coordinates, internal calculations, external datasets, and multiple languages. A major strength is its [[offline-first-architecture|Offline-First Architecture]], seamlessly syncing data collected offline once a connection is reestablished. Data can be exported or connected to Python, Excel, Power BI, and R. It supports both cloud and self-hosted server deployments.

**Trade-offs in Rapid Prototyping**: ODK is highly effective for spinning up stable, functional data collection apps quickly (e.g., within a month). However, this speed comes at the cost of UI/UX flexibility. The free tiers often restrict complex relational data ("entities"), and the resulting applications tend to have static interfaces lacking rich interactivity or dynamic custom designs.
