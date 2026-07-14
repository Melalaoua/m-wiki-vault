---
type: map
title: "OAD Technical Infrastructure and Evaluation"
aliases: []
tags: [map, phd]
updated: 2026-07-14
status: stable
---

# OAD Technical Infrastructure and Evaluation

The [[OAD]] (Outil d'Aide au Diagnostic) is an offline-first mobile health application developed for Android tablets to assist healthcare workers with syndromic clinical diagnostics for non-malarial febrile illnesses in resource-constrained settings like the Central African Republic. To replace legacy Excel-based tools, the project evaluated two primary infrastructure paths. [[Open Data Kit]] (ODK) offered rapid prototyping capable of deploying offline-first forms with built-in GPS, photo support, and server syncing within a month, but was constrained by rigid UI/UX and relational data limits on free tiers. Custom development using [[React Native]] was ultimately pursued despite requiring higher engineering costs and full-stack expertise (demanding approximately four months for a minimum viable product), as it provided the complete architectural freedom and interactive functionality necessary for complex diagnostic workflows. As documented during the 2026 sprint ([[phd/wiki/sources/notes2026oadlog|OAD(log) - MVP Sprint]]), the [[OAD]] custom architecture utilized [[Tamagui]] tokens for the frontend, heavily assisted by AI multi-agent workflows, alongside a backend implementing [[JWT]] authentication and a [[Caddy]] reverse proxy. Local connectivity challenges with the [[Expo]] development client over USB were bypassed via manual tunneling and deep-linking using `adb reverse`. Furthermore, critical data schema corrections were implemented to ensure auditability for the eventual impact study: diagnostic consultations now snapshot a hash or version of the `pathologies.json` and `treatments.json` rulesets to guarantee historical reproducibility, and `healthStaff` profiles transitioned from device-specific UUIDs to server-issued identities to accurately compute per-clinician socio-economic metrics across distributed devices.

## Pages in this area

- [[phd/wiki/entities/oad|OAD]]
- [[phd/wiki/concepts/open-data-kit|Open Data Kit]]
- [[phd/wiki/concepts/react-native|React Native]]

## From [[phd/wiki/sources/notes2026oadlog|OAD(log) - Server]] (2026-07-14)

## OAD Server Infrastructure

The server architecture for [[phd/wiki/entities/oad|OAD]] runs on a 5-container Docker stack orchestrated via Docker Compose:
1. **Nginx**: Operates as a reverse proxy. Explicitly configured to disable proxy buffering to support [[phd/wiki/concepts/server-sent-events|SSE]] streams.
2. **FastAPI Gateway**: The core API layer, using [[phd/wiki/concepts/uv|uv]] and Python 3.13. Handles JWT verification, AES-GCM decryption, gzip, and SHA-256 checks.
3. **PostgreSQL**: The primary relational database (v17).
4. **Redis**: Used as a message broker for Celery, configured with AOF persistence and `noeviction` policy to protect background tasks.
5. **Celery Worker**: Restricted strictly to post-sync, fire-and-forget side effects (like audit logs and push notifications) using synchronous psycopg2 sessions.

### Sync Protocol (RxDB)
The system uses RxDB HTTP replication featuring three standardized endpoints per collection (`pull`, `push`, `stream`). A fundamental constraint of this setup is that **conflict resolution must be synchronous**. Because the client expects an immediate array of conflicts on a push, database UPSERT operations cannot be offloaded to Celery workers; they must happen directly within the FastAPI request cycle.

### Production Hardware (Pasteur Bangui)
The Central African Republic deployment (hosted at `pasteur-bangui.cf`) utilizes a dual-node Dell PowerEdge 540 cluster. Each node boasts 456GB of RAM and 6TB of storage (3TB allocated), ensuring high availability and robust data capacity.
