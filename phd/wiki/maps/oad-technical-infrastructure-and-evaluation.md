---
type: map
title: "OAD Technical Infrastructure and Evaluation"
aliases: []
tags: [map, phd]
updated: 2026-07-14
status: stable
---

# OAD Technical Infrastructure and Evaluation

The [[phd/raw/OAD/OAD | OAD]] (Outil d'Aide au Diagnostic) is an offline-first mobile health application developed for Android tablets to assist healthcare workers with syndromic clinical diagnostics for non-malarial febrile illnesses in resource-constrained environments like the Central African Republic. Replacing legacy Excel-based tools, the project evaluated [[open-data-kit]] (ODK) against custom development. While ODK offered rapid, month-long prototyping of offline-first forms with built-in GPS, photo support, and server syncing, it was constrained by rigid UI/UX and relational data limits on free tiers. Custom development utilizing [[react-native]] was ultimately chosen despite higher engineering costs and a four-month minimum viable product cycle, as it provided the architectural freedom and interactive functionality necessary for complex workflows. During the 2026 sprint ([[notes2026oadlogtablet|OAD(log) - MVP Sprint]]), the frontend was constructed using [[Tamagui]] tokens and AI multi-agent workflows, deploying an [[Expo]] development client where USB connectivity challenges were bypassed via manual tunneling and `adb reverse` deep-linking. The backend [[phd/wiki/entities/oad|OAD]] architecture, detailed in [[notes2026oadlogserver|OAD(log) - Server]], operates as a 5-container Docker Compose stack. A FastAPI gateway running Python 3.13 via [[phd/wiki/concepts/uv|uv]] manages [[JWT]] authentication, AES-GCM decryption, payload checks, and RxDB HTTP replication. Because RxDB clients require an immediate array of conflicts on a push, database UPSERT operations and synchronous conflict resolutions are executed directly within the FastAPI request cycle against a PostgreSQL v17 database. Asynchronous side effects like audit logs and push notifications are offloaded to a Celery worker via a Redis message broker configured for AOF persistence. The networking layer utilizes reverse proxies, incorporating both [[Caddy]] and an Nginx instance explicitly configured to disable proxy buffering for [[phd/wiki/concepts/server-sent-events|SSE]] streams. To ensure reproducibility and auditability for impact studies, diagnostic consultations snapshot a hash or version of the `pathologies.json` and `treatments.json` rulesets, while `healthStaff` profiles transitioned from device-specific UUIDs to server-issued identities to accurately compute per-clinician socio-economic metrics. The production deployment at Pasteur Bangui is hosted on a high-availability dual-node Dell PowerEdge 540 cluster, with each node providing 456GB of RAM and robust storage capacity.

## Pages in this area

- [[phd/wiki/entities/oad|OAD]]
- [[phd/wiki/concepts/open-data-kit|Open Data Kit]]
- [[phd/wiki/concepts/react-native|React Native]]
