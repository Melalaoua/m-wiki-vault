Chose FastAPI : faster (async), pydantic typing, but low documentation (still tbd).
Django is more reliable and older and includes easy admin panel integration

Chose uv instead of pip : faster, new, good material to learn if it becomes the norm.

What I did today
1. Started from OAD DAT (system architecture documentation) for a cold start.
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

####  Plan for the API integration  
##### Revised api/ layout — adapted for RxDB HTTP Replication

**Proposed structure**
api/
├── Dockerfile
├── pyproject.toml
├── uv.lock
├── .python-version
├── .gitignore
├── .env.example
│
├── main.py                          # App factory, lifespan (DB pool + Redis), middleware, router mount
│
├── core/
│   ├── __init__.py
│   ├── config.py                    # pydantic-settings: DB DSN, Redis URL, JWT secret, encryption key
│   ├── security.py                  # JWT bearer verify, AES decrypt/encrypt, gzip de/compress, SHA-256 check
│   ├── dependencies.py              # Depends: get_db, get_redis, get_current_device
│   └── events.py                    # Per-collection event bus (asyncio) feeding SSE streams
│
├── models/
│   ├── __init__.py
│   ├── base.py                      # DeclarativeBase + RxDB-compatible mixin:
│   │                                #   id (text PK), updated_at (float, indexed), _deleted (bool)_
│   ├── patient.py
│   ├── consultation.py
│   ├── tutor.py
│   └── health_staff.py
│
├── schemas/
│   ├── __init__.py
│   ├── replication.py               # RxDB protocol types (see below)
│   ├── patient.py
│   ├── consultation.py
│   ├── tutor.py
│   └── health_staff.py
│
├── routers/
│   ├── __init__.py
│   ├── replication.py               # /v1/{collection}/pull, /push, /stream  (3 routes)
│   └── health.py                    # GET /health (Docker healthcheck)
│
├── services/
│   ├── __init__.py
│   ├── pull.py                      # Query docs after checkpoint, respect batchSize, build response
│   ├── push.py                      # Conflict detection loop, write non-conflicting rows, emit to event bus
│   └── registry.py                  # Map collection name → (SQLAlchemy model, Pydantic schema)
│
└── tasks/                           # Celery — post-sync side-effects only
    ├── __init__.py
    └── post_sync.py                 # audit log, push notifications, cross-collection cascades
RxDB protocol schemas (schemas/replication.py)

class Checkpoint(BaseModel):
    id: str
    updated_at: float

class ChangeRow(BaseModel):
    new_document_state: dict          # the full doc to write
    assumed_master_state: dict | None  # what the client thinks the server has (None = new doc)

class PullResponse(BaseModel):
    documents: list[dict]
    checkpoint: Checkpoint

\# Push request body  = list[ChangeRow]
\# Push response body = list[dict]      (conflicts only)

Endpoint mapping to RxDB protocol
GET /v1/{collection}/pull

Query params: ?updatedAt=float&id=str&batchSize=int
Auth: JWT Bearer

Server logic:
  1. Verify JWT
  2. SELECT * FROM {table}
     WHERE (updated_at > :updatedAt)
        OR (updated_at = :updatedAt AND id > :id)
     ORDER BY updated_at ASC, id ASC
     LIMIT :batchSize
  3. Build checkpoint from last document (or echo input if empty)
  4. Return { documents, checkpoint }
POST /v1/{collection}/push

Body: gzip( encrypt( JSON(list[ChangeRow]) ) )
Headers: Authorization: Bearer \<jwt>
         X-Payload-Hash: \<sha256 of raw body>
         Content-Encoding: gzip

Server logic:
  1. Verify JWT
  2. Verify SHA-256 hash
  3. Decrypt → Decompress → parse list[ChangeRow]
  4. For each changeRow:
     a. Fetch real master state from DB
     b. If conflict (real ≠ assumed) → append to conflicts[]
     c. Else → UPSERT into DB, append to written_events[]
  5. Emit written_events to event bus (→ SSE stream)
  6. Optionally: dispatch post_sync Celery task (audit, notifications)
  7. Return conflicts[] (encrypted + compressed back to client)
GET /v1/{collection}/stream

Auth: JWT Bearer (via query param token for SSE compatibility)
Response: text/event-stream (SSE)

Server logic:
  1. Verify JWT
  2. Subscribe to event bus for this collection
  3. On each event → write SSE frame:
     data: {"documents": [...], "checkpoint": {...}}
  4. Client sends RESYNC on reconnect → falls back to /pull iteration
Security layers (unchanged, applied as middleware/dependencies)

Tablet → Server (push):
  RxDB changeRows → JSON → encrypt(AES-GCM) → gzip → SHA-256 → POST + JWT

Server → Tablet (pull + stream):
  DB query → JSON → (optional encrypt + gzip) → response + JWT verified
core/events.py — In-process event bus for SSE
Since the API is a single FastAPI process per container, we use asyncio primitives (no need for Redis pub/sub at this stage):


# Simplified concept
from asyncio import Queue
from collections import defaultdict

class EventBus:
    def __init__(self):
        self._subscribers: dict[str, list[Queue]] = defaultdict(list)

    async def emit(self, collection: str, event: dict):
        for queue in self._subscribers[collection]:
            await queue.put(event)

    def subscribe(self, collection: str) -> Queue:
        q = Queue()
        self._subscribers[collection].append(q)
        return q

    def unsubscribe(self, collection: str, queue: Queue):
        self._subscribers[collection].remove(queue)
If you scale to multiple API replicas later, swap this for Redis pub/sub.

services/registry.py — Collection routing
Maps the {collection} path param to the correct ORM model and Pydantic schema, so the 3 endpoints stay generic:


REGISTRY = {
    "patients":      (PatientModel, PatientSchema),
    "consultations": (ConsultationModel, ConsultationSchema),
    "tutors":        (TutorModel, TutorSchema),
    "health_staff":  (HealthStaffModel, HealthStaffSchema),
}
Updated dependencies (pyproject.toml)

dependencies = [
    "fastapi[standard]>=0.135.2",
    "pydantic-settings>=2.0",
    "sqlalchemy[asyncio]>=2.0",
    "asyncpg>=0.30",
    "sse-starlette>=2.0",          # SSE support for FastAPI
    "python-jose[cryptography]>=3.3",
    "cryptography>=44.0",
    "celery[redis]>=5.4",          # demoted to post-sync side-effects
]
Key architectural takeaway
The RxDB protocol requires synchronous conflict resolution — the push response must contain the conflicts array. This means the DB write happens in the request cycle (inside a transaction), not in a Celery worker. Celery is only used for fire-and-forget side-effects after a successful sync.

Update Todos
Create directory structure and foundational files (config, .env.example)

Implement core modules (security, events, dependencies)

Implement SQLAlchemy models (base + entities)

Implement Pydantic schemas (replication + entities)

Implement services (registry, pull, push)

Implement routers (replication, health) and Celery tasks

Rewrite main.py (app factory, lifespan, middleware)

Update pyproject.toml and create Dockerfile


Registered route 
GET /health : Docker healthcheck
GET /v1/{collection}/pull : RxDB pull -- checkpoint pagination
POST /v1/{collection}/push : RxDB push -- encrypted payload, returns conflicts
GET /v1/{collection}/stream : SSE for pull.streams$ realtime events


Request flow
**Push** : Tablet encrypts+compresses changeRows -> post /v1/patients/push with JWT + SHA-256 hash -> server verifies JWT, hash, decrypts, decompresses -> conflict detection per row -> upserts non-conflicting -> emits SSE events -> return conflicts[] synchronously.

**Pull** : Tablet sends checkpoint -> GET /v1/patients/pull?updatedAT=...&id=...&batchSize=50 with JWT -> server queries DB after checkpoint ->return {documents, checkpoint}.

**Stream**: Tablet connects via EventSource to /v1/patients/stream?token=\<jwt> -> receives SSE frames with {documents, checkpoint} on every push from any client -> on disconnect, client emits RESYNC and falls back to pull iteration


Well I asked opus to write the follow up steps to follow but he instead coded THE ENTIRE codebase. Here's the specs below, need to be tested though.

Complete stack overview

OAD-Server/
├── docker-compose.yml          # Orchestrates all 5 services
├── .env.example                # Shared env vars (PG creds, JWT, encryption key)
│
├── nginx/                      # 1. Reverse proxy
│   ├── Dockerfile              #    nginx:1.27-alpine
│   └── nginx.conf              #    Upstream → api:8000, SSE buffering disabled
│
├── api/                        # 2. FastAPI gateway (RxDB HTTP replication)
│   ├── Dockerfile              #    python:3.13-slim + uv
│   └── (full layout from prior step)
│
├── worker/                     # 3. Celery worker (async post-sync)
│   ├── Dockerfile              #    python:3.13-slim + uv
│   ├── pyproject.toml          #    celery[redis], sqlalchemy, psycopg2
│   ├── celery_app.py           #    Celery app instance + autodiscover
│   ├── config.py               #    DATABASE_URL, REDIS_URL from env
│   ├── db.py                   #    Sync SQLAlchemy session (psycopg2)
│   └── tasks/
│       └── post_sync.py        #    audit_log, notify tasks
│
├── redis/                      # 4. Message broker + cache
│   ├── Dockerfile              #    redis:7-alpine
│   └── redis.conf              #    AOF persistence, 256MB limit, noeviction
│
└── db/                         # 5. PostgreSQL
    ├── Dockerfile              #    postgres:17-alpine
    └── init.sql                #    Bootstrap: create oad_user, grant permissions
Container dependency graph

nginx ──▶ api ──▶ db
              ──▶ redis
          worker ──▶ db
                 ──▶ redis
Key design decisions per container
Container	Detail
nginx	SSE location block disables proxy_buffering and sets read_timeout to 24h so streams stay open. Passes X-Payload-Hash header through to API.
worker	Uses synchronous psycopg2 (not asyncpg) since Celery workers are sync. Shares task names with the API (post_sync.audit_log, post_sync.notify) but has its own implementation.
redis	appendonly yes for AOF persistence — queued Celery tasks survive restarts. noeviction policy ensures tasks are never silently dropped.
db	Init script runs once on first volume creation. Grants oad_user full privileges on the oad database. Table creation is deferred to Alembic migrations (not included here).
compose	All services use healthchecks with condition: service_healthy dependencies, so the API waits for db+redis, and nginx waits for the API. Single oad bridge network, no ports exposed except nginx:80.
To start

cp .env.example .env
# Edit .env with production values
docker compose up --build



Tried booting up the docker-compose with all 5 container managed 
Some hiccups then n there but seems nominal. Did minimal testing and got nominal response.
Need to try on the tablet and with some real data. 



Alembic migration for boostrap & migration
- uv run alembic revision -m "create initial tables" 2>&1
- docker compose up --build api


### April, the 24th
Big advancements made in [[OAD(log) - Tablet Database]], I didn't expect to go down the rabbit hole and to do a clean slate on the OAD, but I master much more my crafts now. It's time to get back to testing between the server and the tablet through the API gateway now.



### June, the 11th

réunion avec salim :
- 2 serveurs : Poweredge 540 cluster. RAM 456Go x2. Stockage 6to avec 3to de libre. 
- Domaine pasteur-bangui.cf
- Jeudi 18 activation serveur 10h