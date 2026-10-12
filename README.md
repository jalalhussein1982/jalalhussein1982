# Hi, I'm Jalal Hussein 👋

**Data Engineer · Full-Stack Engineer · AI/LLM Engineer** — I design, build, and *operate* production
systems end to end: ingestion pipelines that survive failure, web applications people use daily, and
LLM systems with evaluation and guardrails rather than vibes — and **MCP servers** that give an agent
governed access to those systems.

📍 Prague, Czechia &nbsp;·&nbsp; 🎓 MA Geopolitical Studies, Charles University &nbsp;·&nbsp; 📫 [jalalhussein@gmail.com](mailto:jalalhussein@gmail.com) &nbsp;·&nbsp; 💼 [LinkedIn](https://linkedin.com/in/jalal-hussein-prg)

> **Work authorization:** long-term residence in the Czech Republic with **free access to the Czech
> labour market** as a graduate of a Czech university (Act No. 435/2004 Coll., §98(j)) — **no work
> permit and no sponsorship required.**

---

## 🔭 What I actually do

I own systems from schema to deployment. That usually means: multi-source ingestion that is
**idempotent and resumable** (run-state checkpointing, gap detection, backfill); a **PostgreSQL**
model I designed and migrated myself; an **LLM layer that is measured** — golden sets, inter-coder
reliability, LLM-judge precision/recall against blind human verdicts, and A/B harnesses that report
what was *lost* as well as gained; and **Kubernetes** underneath it, with the on-call to match.

I am equally comfortable writing the React front end that makes it usable, and I have shipped
**GDPR** and statutory-reporting work where being wrong has consequences.

## 🛠️ Tech

**Languages:** Python 3.12 · TypeScript / Node · SQL · Bash · PHP
**Backend:** FastAPI (async, Pydantic v2) · NestJS · REST/OpenAPI · Server-Sent Events · WebSockets
**Frontend:** React 18/19 · Next.js · Astro · Vite · Tailwind · Mapbox GL JS · ECharts · Streamlit
**Data:** PostgreSQL (psycopg 3, SQLAlchemy 2, Alembic) · **PostGIS** · **pgvector** · **Neo4j** · Qdrant · SQLite · Redis · Parquet
**AI / LLM:** RAG with hybrid retrieval (BM25 ⊕ dense, reciprocal-rank fusion) · rerankers · citation verification and validator gates · structured outputs · evaluation harnesses · token/cost metering · self-hosted open-weight models on **vLLM** · **MCP servers** (Python MCP SDK 2.x: tools, resources and prompts with typed output schemas; stdio and Streamable HTTP; OAuth 2.1 resource servers with per-tool scopes; Multi Round-Trip Requests for human-confirmed destructive actions; durable job handles with progress notifications)
**Infra:** **Kubernetes** (Kustomize, StatefulSets, CronJobs, RBAC, sealed secrets, NetworkPolicies, CloudNativePG) · Docker · **Terraform / Bicep** · **Azure** (Container Apps, Functions, Key Vault, AI Search, Entra) · GitHub Actions · Prometheus/Grafana
**HPC:** **MetaCentrum** PBS batch · Apptainer/Singularity images · GPU jobs on H100-class nodes

## 🔌 MCP servers

Five MCP (Model Context Protocol) servers over systems I built and operate, each giving a host model governed
access to a production system. Use case first, then what it took to build. Python MCP SDK 2.x, protocol
revision 2026-07-28.

| Server | What an agent can do with it | What it took |
|---|---|---|
| **[ihkam-eval-mcp](https://github.com/jalalhussein1982/ihkam-eval-mcp)** | Read the lawyer-verified golden set, the frozen A/B artifacts and the two-sided acceptance gate behind a legal RAG, so a retrieval change is judged on recorded numbers before it ships. The corpus and the red-team payload never leave the host. | Seven read-only tools, three resources and a prompt expose the gate (lost = 0, recall@10 ≥ 0.98, every style ≥ 0.95) as data; stdio transport; every number verified against the recorded artifacts. |
| **[siem-mcp](https://github.com/jalalhussein1982/conflict-trends-dashboard/tree/main/phase1/siem-mcp)** | Question the Sahel conflict-event platform — trends, lethality per event, actor composition, admin-1 hotspots, radius and bounding-box queries, ingestion freshness — with no licensed ACLED text in any result. | Nine typed tools behind one store interface: a synthetic SQLite backend ships with the code, live PostGIS (`ST_DWithin` for radius queries) in production. |
| **[hostel-ops-mcp](https://github.com/jalalhussein1982/hostel-ops-mcp)** | Run the front desk of a hostel's statutory guest-registration system from Claude Desktop, Claude Code or a remote host: triage the queue, flag minors, approve or return submissions, manage group bookings, prepare the authority export — seeing only the personal data its scope grants, erasing nothing a human has not confirmed. | OAuth 2.1 resource server over Streamable HTTP (JWTs against the issuer's JWKS, RFC 9728 metadata), nine per-tool scopes; a fail-closed redaction table over every column and a test that scans every read for every PII literal; writes run the app's own state machine and audit; erasure confirmed through Multi Round-Trip Requests with a sealed request state bound to tool, arguments and caller. 165 tests. |
| **[geoecon-pipeline-mcp](https://github.com/jalalhussein1982/geoecon-pipeline-mcp)** | Operate a long-running LLM news pipeline from a chat: inspect runs, read what the validator held back, resume a failed run from the right stage with its original window, watch progress, stay inside an LLM budget, write the incident report in the house format. | Long-running jobs on a stateless transport: durable PostgreSQL-backed job handles, progress from the pipeline's own logs and row counts, `ResourceUpdated` notifications over `subscriptions/listen`, a cost gate that estimates each LLM stage first and parks the job in `input_required` above budget; Job model mapped onto the MCP tasks extension. 151 tests. |
| **[coin-wargame-mcp](https://github.com/jalalhussein1982/coin-wargame-mcp)** | Any host model plays the Mauritania COIN wargame as Government or Red Team through tools instead of vendor-specific prompt glue; two hosts can share one game; every game replays from its seed; a benchmark that only speaks MCP scores models on identical scenarios against a rule-based floor. | Stateful games on a stateless transport: every call loads a SQLite row, rebuilds the engine, acts and writes back under a version check; dice state persisted per call; `replay()` verifies a recorded state hash per log entry; illegal moves come back as errors carrying the engine's reasons and legal alternatives; fog of war enforced by type. 73 tests. |

## ⭐ Featured projects

### Data engineering & geospatial
- **[conflict-trends-dashboard](https://github.com/jalalhussein1982/conflict-trends-dashboard)** — Interactive geospatial dashboard over **34,681 ACLED conflict events** (Sahel, 1997–present). **FastAPI + PostgreSQL/PostGIS + Mapbox GL JS**, with ingest and serve split into independently deployable services and an automated OAuth ingestion pipeline on **Kubernetes** (StatefulSet, bulk-load Job, daily incremental CronJob). *Anonymised portfolio copy of an MA research system — no licensed data included.*

### AI / LLM engineering
- **[geoeconomics-news-fetcher](https://github.com/jalalhussein1982/geoeconomics-news-fetcher)** — Daily multilingual LLM pipeline: GDELT + curated sources → event clustering → grounded synthesis **behind a validator gate** → HTML + email newsletter. Dockerised, deployed as a resumable **Kubernetes CronJob** with Postgres run-state. *MIT.*
- **[european-defence-daily-brief](https://github.com/jalalhussein1982/european-defence-daily-brief)** — Serverless daily intelligence pipeline done properly: **idempotency, ETag optimistic concurrency, run leases, self-healing backfill**, 334 tests.
- **[mauritania-coin-wargame](https://github.com/jalalhussein1982/mauritania-coin-wargame)** — Counter-insurgency simulation against a doctrine-grounded **LLM adversary**: deterministic rules engine at the core, generative behaviour at the edges, FastAPI + WebSockets + React.

### Full-stack & systems
- **[hostel-checkin-system](https://github.com/jalalhussein1982/hostel-checkin-system)** — Multilingual (**7 languages, RTL**) self-service guest registration: FastAPI, argon2 auth, digital signatures, encrypted backups, GDPR compliance, **500+ tests**.
- **[regression-analysis-ide](https://github.com/jalalhussein1982/regression-analysis-ide)** — A *type-checked* statistical IDE treating regression **assumptions as type constraints** — immutable snapshots, leakage-safe transforms, auto-invalidating cached diagnostics.
- **[twg-gallery](https://github.com/jalalhussein1982/twg-gallery)** — A from-scratch **PHP photo-gallery CMS** (albums, search, admin, REST API, installer) — no framework dependencies.

---

## 📊 GitHub

![Jalal's GitHub stats](https://github-readme-stats.vercel.app/api?username=jalalhussein1982&show_icons=true&hide_border=true&count_private=true)
![Top languages](https://github-readme-stats.vercel.app/api/top-langs/?username=jalalhussein1982&layout=compact&hide_border=true&langs_count=8)

---

💬 Open to **mid-to-senior individual-contributor** roles in **data engineering, backend/full-stack,
and AI/LLM engineering** — Prague or remote. Reach me at **[jalalhussein@gmail.com](mailto:jalalhussein@gmail.com)**.
