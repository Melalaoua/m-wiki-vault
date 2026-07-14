---
type: source
title: "OAD(log) - Server"
citekey: notes2026oadlog
source_type: article
captured: 2026-07-14
site: notes
url: 
aliases: []
tags: [source, phd]
updated: 2026-07-14
status: developing
---

# OAD(log) - Server

Original: [[OAD(log) - Server]]

Chose [[phd/wiki/concepts/fastapi|FastAPI]] : faster (async), pydantic typing, but low documentation (still tbd). [[phd/wiki/concepts/django|Django]] is more reliable and older and includes easy admin panel integration.

Chose [[phd/wiki/concepts/uv|uv]] instead of pip : faster, new, good material to learn if it becomes the norm.

What I did today
1. Started from [[phd/wiki/maps/oad-technical-infrastructure-and-evaluation|OAD DAT (system architecture documentation)]] for a cold start.
Develop 5 docker container (nginx, api, worker-celery, redis, database-postgres)
I intend to dig in each and educate myself oneach subject.

### Celery
I Read :
- https://medium.com/@hitorunajp/celery-and-background-tasks-aebb234cae5d
- https://docs.celeryq.dev/en/main/getting-started/first-steps-with-celery.html
- https://lip17.medium.com/hands-on-learn-python-celery-in-30-minutes-9544aabb70b1

### API
- https://rxdb.info/replication-http.html
- FastAPI tutorial
- Used claude Opus 4.6 for the plan

#### Plan for the API integration
##### Revised api/ layout — adapted for RxDB HTTP Replication

The structure sets up an API using [[phd/wiki/concepts/rxdb-http-replication|RxDB protocol types]], defining standard `PullResponse`, `ChangeRow`, and `Checkpoint` schemas. The server has 3 main endpoints for replication:
- `GET /v1/{collection}/pull` (Checkpoint pagination)
- `POST /v1/{collection}/push` (Encrypted payload, synchronous conflict return)
- `GET /v1/{collection}/stream` ([[phd/wiki/concepts/server-sent-events|SSE]] realtime events)

Security layers apply AES-GCM encryption, gzip compression, and SHA-256 validation alongside JWT verification.

**Key architectural takeaway:**
The RxDB protocol requires synchronous conflict resolution — the push response must contain the conflicts array. This means the DB write happens in the request cycle (inside a transaction), not in a [[phd/wiki/concepts/celery|Celery]] worker. Celery is only used for fire-and-forget side-effects after a successful sync.

Complete stack overview:
- **nginx**: Reverse proxy, upstream to api:8000, SSE buffering disabled.
- **api**: FastAPI gateway (RxDB HTTP replication) on python:3.13-slim + uv.
- **worker**: Celery worker (async post-sync) via psycopg2 (sync SQLAlchemy).
- **redis**: Message broker + cache (appendonly AOF persistence).
- **db**: PostgreSQL 17 (initialized via init.sql).

### April, the 24th
Big advancements made in [[OAD(log) - Tablet Database]], clean slate on the [[phd/wiki/entities/oad|OAD]]. Time to get back to testing between the server and the tablet through the API gateway.

### June, the 11th
Réunion avec salim :
- 2 serveurs : Poweredge 540 cluster. RAM 456Go x2. Stockage 6to avec 3to de libre.
- Domaine pasteur-bangui.cf
- Jeudi 18 activation serveur 10h

## Key claims

- The RxDB push protocol mandates synchronous conflict resolution, meaning database writes must happen inside the immediate API request cycle rather than being offloaded. ([[OAD(log) - Server#Key architectural takeaway]]) — "The RxDB protocol requires synchronous conflict resolution — the push response must contain the conflicts array. This means the DB write happens in the request cycle (inside a transaction), not in a Celery worker."
- FastAPI and uv were selected over alternatives like Django and pip due to speed, asynchronous support, and modern tooling. ([[OAD(log) - Server#Intro (No heading)]]) — "Chose FastAPI : faster (async), pydantic typing... Chose uv instead of pip : faster, new, good material to learn"
- The OAD production deployment in Bangui relies on a heavy-compute cluster of two Poweredge 540 servers. ([[OAD(log) - Server#June, the 11th]]) — "2 serveurs : Poweredge 540 cluster. RAM 456Go x2. Stockage 6to avec 3to de libre."
