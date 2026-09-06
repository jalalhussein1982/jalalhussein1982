# Hi, I'm Jalal Hussein 👋

**Data Engineer · Full-Stack Engineer · AI/LLM Engineer** — I design, build, and *operate* production
systems end to end: ingestion pipelines that survive failure, web applications people use daily, and
LLM systems with evaluation and guardrails rather than vibes.

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
**AI / LLM:** RAG with hybrid retrieval (BM25 ⊕ dense, reciprocal-rank fusion) · rerankers · citation verification and validator gates · structured outputs · evaluation harnesses · token/cost metering · self-hosted open-weight models on **vLLM**
**Infra:** **Kubernetes** (Kustomize, StatefulSets, CronJobs, RBAC, sealed secrets, NetworkPolicies, CloudNativePG) · Docker · **Terraform / Bicep** · **Azure** (Container Apps, Functions, Key Vault, AI Search, Entra) · GitHub Actions · Prometheus/Grafana
**HPC:** **MetaCentrum** PBS batch · Apptainer/Singularity images · GPU jobs on H100-class nodes

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
