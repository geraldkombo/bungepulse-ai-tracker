# bungepulse-ai-tracker

AI parliamentary accountability tracker for Kenya. Ingests Hansard, Votes & Proceedings, and Order Papers. Uses intfloat/e5-small-v2 sentence embeddings and rule-based patterns for entity extraction and commitment detection. Built with Laravel, FastAPI, Celery, Redis, MariaDB, n8n, and Docker. NIRU AI Hackathon 2026.

<div align="center">

# BungePulse

### National Security Infrastructure for Parliamentary Accountability

[![AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue.svg)](LICENSE)
[![Python 3.11+](https://img.shields.io/badge/Python-3.11+-3776AB.svg?logo=python&logoColor=white)](https://python.org)
[![PHP 8.2](https://img.shields.io/badge/PHP-8.2-777BB4.svg?logo=php&logoColor=white)](https://php.net)
[![Laravel 11](https://img.shields.io/badge/Laravel-11-FF2D20.svg?logo=laravel&logoColor=white)](https://laravel.com)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.109+-009688.svg?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Docker](https://img.shields.io/badge/Docker-8_Containers-2496ED.svg?logo=docker&logoColor=white)](https://docker.com)
[![MariaDB](https://img.shields.io/badge/MariaDB-11.4-003545.svg?logo=mariadb&logoColor=white)](https://mariadb.org)
[![Status](https://img.shields.io/badge/Status-In_Development-yellow.svg)]()
[![Hackathon](https://img.shields.io/badge/NIRU_AI_Hackathon-2026-1B5E20.svg)]()

**Democratic early-warning system -- not civic tech.**

*AI processes. Humans approve. Citizens know.*

NIRU AI Hackathon 2026 | Project ID: PJ2A5E23R | Deadline: March 26, 2026

[The Problem](#the-problem) Â· [Security Framework](#eight-dimensional-national-security-framework) Â· [Four AI Moments](#the-four-ai-moments) Â· [Architecture](#architecture) Â· [Dashboard](#dashboard-architecture) Â· [NLP Pipeline](#nlp-pipeline) Â· [WhatsApp Bot & SMS](#whatsapp-bot--sms) Â· [Trust & Safety](#trust-safety--legal) Â· [Quick Start](#quick-start) Â· [Team](#team)

</div>

---

## The Problem

Kenya has early-warning systems for terrorism (NCTC), drought (NDMA), and disease (KEMRI). **Parliament -- where the money, laws, and power are controlled -- has nothing.**

349 MPs. 67 Senators. 26 official sources. 200--400 pages of parliamentary text per sitting day. No system connects what an MP says in January to how they vote in March. No system tracks which Cabinet Secretary dodges parliamentary summons 8 out of 10 times. No system surfaces stalled constituency projects, budget gaps, or broken commitments at scale.

BungePulse fills that gap -- across all 290 constituencies, all 47 counties, all 8 national security dimensions.

---

## Eight-Dimensional National Security Framework

Every dashboard tab, WhatsApp alert, SMS notification, and AI pipeline output maps to at least one of these eight dimensions. This is how BungePulse organises accountability -- as national security infrastructure, not a transparency exercise.

| # | Dimension | Kiswahili | What BungePulse Tracks |
|---|-----------|-----------|------------------------|
| 1 | **Political Security** | Usalama wa Kisiasa | Speech-to-vote contradictions via semantic matching |
| 2 | **Economic Security** | Usalama wa Kiuchumi | Budget gaps, CDF utilisation, financial anomalies |
| 3 | **Health Security** | Usalama wa Afya | Health facility timelines, stalled projects, budget execution |
| 4 | **Education Security** | Usalama wa Elimu | Education budgets tracked to school build-out and policy delivery |
| 5 | **Environmental Security** | Usalama wa Mazingira | Environment votes and climate funds tracked to implementation |
| 6 | **Food Security** | Usalama wa Chakula | Agriculture bills, subsidy flows, fertiliser programs |
| 7 | **Cyber Security** | Usalama wa Mtandao | ICT committee work, data protection bills, digital infrastructure |
| 8 | **Territorial Security** | Usalama wa Mipaka | Border county projects, land committee activity, cross-border infrastructure |

### Constitutional Grounding

Every feature traces to specific articles of the **Constitution of Kenya 2010**. If anyone challenges BungePulse's right to exist, the response is: *Article 1* (sovereignty belongs to the people), *Article 35* (access to information), *Article 118* (public participation). Every constitutional citation in the UI becomes a clickable learning moment with plain-language summaries at Grade 8 reading level and Kiswahili translations.

<details>
<summary><strong>19 Constitutional Articles Mapped</strong></summary>
<br>

| Article | What It Covers | Feature It Powers |
|---------|---------------|-------------------|
| Art. 1 | Sovereignty belongs to the people | MP accountability tracking |
| Art. 10 | National values (transparency, accountability) | System rationale |
| Art. 27 | Equality (1/3 gender representation) | Vote gender breakdowns |
| Art. 35 | Right to information | WhatsApp bot, SMS alerts, data access |
| Art. 43 | Right to health, housing, education | Projects tracker |
| Art. 53 | Children's rights | Intergenerational impact flags |
| Art. 54 | Persons with disabilities | WCAG 2.1 AA, voice summaries |
| Art. 56 | Marginalized communities | Community impact tags |
| Art. 63 | Community land | Indigenous community alerts |
| Art. 75 | Conduct of State officers | Performance monitoring |
| Art. 91 | Political parties | Party discipline index |
| Art. 94--96 | Parliament's role | Vote and bill tracking |
| Art. 114 | Public finance | Budget and bill pipeline |
| Art. 118 | Public participation | Citizen campaigns |
| Art. 125 | Plenary sittings conducted openly | Plenary monitoring |
| Art. 153 | Summoning before Parliament | Summons tracker, proxy detection |
| Art. 201, 202, 217 | Finance, revenue, division of funds | CDF tracking |
| Art. 226 | Accounts and audit | Financial tracking |
| Art. 229 | Removal and accountability | MP performance tracking |

</details>

---

## The Four AI Moments

Four capabilities where no human team could replicate what AI does. Each has a live demo moment designed for judges.

### Moment 1: Scale Detection

Parliament produces 200--400 pages per sitting day. A human team would need 15 full-time researchers. BungePulse processes it all before dawn.

> **Demo:** Raw Hansard paragraph on screen. Click "Process." Watch extraction: MP name, topic tags, commitment candidate, confidence score, linked bill. 2 seconds. A human takes 20 minutes per segment. There are 300 per sitting day.

### Moment 2: Cross-Source Contradiction Detection

Hansard says 210 voted Yes. Votes & Proceedings says 208. The 2-vote discrepancy is flagged automatically.

> **Demo:** Verification panel -- Hansard vs V&P, the 2-vote gap flagged in amber. *"This is how we catch data manipulation or OCR errors before they become published misinformation."*

**Five anomaly types:** impossible totals (votes > 349), missing MPs (named but absent from roll-call), mathematical errors (Yes + No + Abstain + Absent != Total), title mismatches across sources, temporal inconsistencies (commitment date after vote date).

### Moment 3: Commitment-to-Vote Linking

An MP says *"I will fight corruption"* on January 15. On March 8, they vote NO on the Anti-Corruption Amendment Bill. 52 days apart. Different documents. The semantic matching engine connects them automatically.

> **Demo:** Evidence chain: Hansard quote (Jan 15, p.23) > Bill tabled (Feb 1) > Committee Stage (Feb 20) > Vote (Mar 8) > Alignment verdict.

### Moment 4: Pattern Detection Across Time

One CS missing one summons is an incident. The same ministry sending proxies 8 out of 10 times over 90 days is systematic avoidance.

> **Demo:** Ministry Responsiveness Index -- lowest-scoring ministry highlighted. *"No journalist has time to cross-check 90 days of Order Papers against 90 days of Hansard. AI does."*

---

## Architecture

Dual-service system sharing one MariaDB instance, connected via REST APIs inside Docker.

```
+----------------------------------------------------------------------+
|                         DOCKER ENVIRONMENT                           |
|                     Network: bungepulse (bridge)                     |
|                                                                      |
|  +----------------------+             +---------------------------+  |
|  |  LARAVEL STACK       |    REST     |  FASTAPI STACK            |  |
|  |  (Steve Maloba)      |    API      |  (Derick Ochieng)         |  |
|  |                      |             |                           |  |
|  |  Laravel 11 (PHP 8.2)<------------>  FastAPI 0.109             |  |
|  |  Dashboard + Auth    |             |  NLP API + Admin          |  |
|  |  Meilisearch         |             |  WhatsApp + Celcom SMS    |  |
|  |  n8n Orchestration   |             |  Celery + Redis 7.x      |  |
|  |                      |   trigger   |  e5-small-v2 NLP Engine   |  |
|  +----------+-----------+             +-------------+-------------+  |
|             |                                       |                |
|             +--------->  MariaDB 11.4 (shared)  <---+                |
|                        10 canonical tables (Derick)                  |
|                        + Laravel tables (Steve)                      |
+----------------------------------------------------------------------+
                                  |
                    Meta WhatsApp Cloud API (primary)
                    Celcom Africa SMS API (fallback)
```

**Data ownership:** Derick writes 10 tables via SQLAlchemy/Alembic. Steve reads them via read-only DB user. Steve writes to Laravel's own tables (users, sessions, cache). Derick sends WhatsApp via Meta Cloud API and SMS via Celcom Africa REST API. Gerald owns content strategy, Kiswahili templates, and QA review.

### 8 Docker Containers

| # | Container | Stack | Port | Purpose |
|---|-----------|-------|------|---------|
| 1 | bp_mariadb | Steve | 3306 | Shared MariaDB 11.4 database |
| 2 | bp_laravel | Steve | 8001 | Laravel PHP 8.2-FPM + nginx |
| 3 | bp_n8n | Steve | 5678 | n8n workflow automation |
| 4 | bp_redis | Steve | 6379 | Sessions, cache, Celery broker |
| 5 | bp_meilisearch | Steve | 7700 | Full-text search |
| 6 | bp_fastapi | Derick | 8000 | FastAPI + 19 endpoints |
| 7 | bp_celery_worker | Derick | -- | Background NLP + alerts (concurrency=2) |
| 8 | bp_celery_beat | Derick | -- | Scheduled daily pipeline |

### Tech Stack

| Layer | Technology | Owner |
|-------|-----------|-------|
| Web UI + Auth | Laravel 11 (PHP 8.2), Tailwind CSS, daisyUI, Alpine.js | Steve |
| Admin Panel | Filament 3 | Steve |
| Orchestration | n8n (self-hosted, 15 workflows) | Steve |
| Search | Meilisearch | Steve |
| API | FastAPI (Python 3.11+), 19 endpoints | Derick |
| Background Tasks | Celery 5.3 + Redis 7.x | Derick |
| NLP Engine | intfloat/e5-small-v2 (384-dim) | Derick |
| Database | MariaDB 11.4 (10 canonical tables) | Shared |
| Alerts (WhatsApp) | Meta Cloud API v18.0 | Derick |
| Alerts (SMS) | Celcom Africa REST API | Derick |
| Containerisation | Docker + docker-compose | Shared |

### Integration Rules

- **One database.** MariaDB 11.4. No separate MySQL.
- **One network.** All containers on `bungepulse` bridge.
- **One scrape schedule.** Celery beat at 06:00. n8n for manual/webhook only.
- **One API contract.** Laravel reads/writes via FastAPI endpoints.
- **One alerts engine.** WhatsApp + SMS both in Derick's stack.

---

## Dashboard Architecture

10 tabs. 10 constitutional mandates. Zero redundancy.

| Tab | National Security Need | Constitutional Anchor |
|-----|----------------------|-----------------------|
| **Overview** | System health + 8-dimension security monitor | Art. 1, 10 |
| **Recent Votes** | How Parliament voted (gender/party breakdowns) | Art. 94--96, 27 |
| **MPs Tracker** | Individual MP accountability + commitment tracking | Art. 1, 75, 229 |
| **Bills Pipeline** | Legislation progress (5-stage visual flow) | Art. 94, 114 |
| **Summons Tracker** | Executive responsiveness + Ministry Grade Cards (A--F) | Art. 153 |
| **Party Positions** | Party discipline index | Art. 91 |
| **Campaigns** | Citizen mobilisation + polls | Art. 118 |
| **WhatsApp Bot** | Population-scale information delivery | Art. 35 |
| **Projects** | Budget-to-ground reality (tri-source tracking) | Art. 43, 201, 217 |
| **About** | Methodology transparency + "How AI Works" | Art. 35 |

### Design System

| Element | Value |
|---------|-------|
| Background | `#FFFFFF` (white) |
| Primary | `#16a34a` (green) |
| Accent | `#F9A825` (gold) |
| Error states | Contextual red only |
| Typography | System fonts, Grade 8 reading level |
| Accessibility | WCAG 2.1 AA compliant |

---

## The Daily Pipeline

```
06:00 AM  Ingestion ......... Celery downloads + normalises from 26 sources
          Archival .......... Raw documents + SHA-256 content hashes
          NLP ............... Entity extraction + commitment candidate detection
          Linking ........... Semantic similarity: speech > bill > vote chains
          Verification ...... Hansard x V&P x Order Papers cross-check
06:15 AM  Queue ............. Flagged items enter human review queue

07:00 AM  Human Review ...... Approve / block / investigate (immutably logged)
          Every decision: reviewer ID, timestamp, action, rationale, IP hash

09:00 AM  Publishing ........ WhatsApp + SMS alerts + dashboard updates go live
```

**Golden Rule:** AI processes. Humans approve. Citizens know.

---

## NLP Pipeline

MVP uses intfloat/e5-small-v2 embeddings and rule-based patterns. Honest and fast.

| Step | Technology | What It Does |
|------|-----------|-------------|
| Sentence embeddings | intfloat/e5-small-v2 | Encodes speeches, bills, votes for similarity |
| Commitment detection | Rule-based patterns | Flags "I commit...", "I will ensure..." |
| Semantic matching | intfloat/e5-small-v2 | Links commitments to bills and votes over time |
| Verification | Custom Python engine | Cross-checks Hansard, V&P, Order Papers |
| Pattern detection | Time-series analysis | Tracks summons, proxies, responsiveness |
| Anomaly detection | Rule-based checks | Flags five anomaly types for human review |

**Confidence gates:**

| Threshold | Action |
|-----------|--------|
| >= 95% | Auto-approve |
| >= 80% | Human review |
| >= 40% | Auto-flag for investigation |
| < 40% | Discard |

> **Honesty note:** MVP uses rule-based commitment detection (~70% recall). Fine-tuned classification is Phase 2.

---

## WhatsApp Bot & SMS

Kiswahili-first. 9 commands. Article 35 at population scale.

| Command | Kiswahili | Function |
|---------|-----------|----------|
| `ANZA` | Start | Opt-in; store phone + optional constituency |
| `ACHA` | Stop | Opt-out; delete all data |
| `MBUNGE WANGU` | My MP | Returns constituency MP + County Woman Rep (Art. 27) |
| `LEO` | Latest | Today's votes and active polls |
| `KURA` | Poll | View/respond to active polls |
| `MATOKEO` | Results | Poll results by constituency |
| `DATA YANGU` | My Data | View what is stored |
| `FUTA` | Delete | Permanently erase all stored data |
| `MSAADA` | Help | Show all commands |

**Delivery channels:** WhatsApp via Meta Cloud API (primary, free 1,000 conversations/month). SMS via Celcom Africa REST API (fallback for citizens without smartphones, KES 0.25/SMS). Both implemented in Derick's FastAPI/Celery stack via httpx.

---

## Who Uses This

| Tier | Audience | Access | Cost |
|------|----------|--------|------|
| **Citizen** | General public | WhatsApp/SMS alerts, public dashboard, constitutional education | Free forever (Art. 35) |
| **Newsroom** | Media houses | Journalist API, bulk exports, webhook alerts | KSh 50K/year |
| **CSO** | Civil society | Thematic dashboards, campaign tools, outcome reports | KSh 30K/year |
| **Industry** | Private sector | Sector dashboards, risk signals, regulatory pipeline | KSh 150K/year |
| **Research** | Academia | Historical datasets, custom queries | By arrangement |

Paying users see the same parliamentary facts citizens see -- faster, filtered, better-formatted. No citizen data, no suppression, no private feeds.

---

## Trust, Safety & Legal

### What BungePulse Never Does

| Boundary | Reason |
|----------|--------|
| Collects National ID or Maisha Namba | Unnecessary -- phone + constituency is sufficient |
| Publishes MP phone numbers | Prevents harassment |
| Uses "broke promise", "lied", or "corrupt" | Defamation risk -- always "voted differently from stated position" |
| Publishes AI claims without human approval | One hallucination destroys all credibility |
| Shares citizen data with anyone | Privacy is constitutional (Art. 31) |
| Makes individual predictions | Profiling is accusation, not accountability |
| Makes endorsements during elections | 90-day pre-election lockdown protocol |

### Publication Rules

- **Human-in-the-loop:** No high-stakes alert publishes without explicit approval.
- **Triple-source verification:** Hansard x V&P x Order Papers with 95/80/40 confidence gates.
- **Non-partisan:** Same data, same methodology, every MP, every party, every region.
- **Electoral integrity:** 90 days before elections -- verified factual data only.

### Privacy (Kenya DPA 2019)

- **Collected:** Phone number + optional constituency + language preference.
- **Never collected:** Names, National ID, Maisha Namba, precise location, political affiliation.
- **User control:** `DATA YANGU` shows stored data. `FUTA` erases everything.
- **Retention:** Stale records auto-purge after defined windows.

### Legal Disclaimer

This project and its outputs are provided "as is" without warranty of any kind. Nothing in this repository constitutes legal advice. All data sourced from official parliamentary records published by the Parliament of Kenya.

---

## Quick Start

### Prerequisites

- Git, Docker, Docker Compose

### Setup

```bash
git clone https://github.com/geraldkombo/bungepulse-ai-tracker.git
cd bungepulse-ai-tracker

cp .env.example .env
# Fill in: MariaDB credentials, Meta WhatsApp keys, Celcom Africa SMS key

docker-compose up --build
# Wait 30s for MariaDB initialisation

# Derick's stack
docker-compose exec fastapi alembic upgrade head

# Steve's stack
docker-compose exec laravel php artisan migrate
docker-compose exec laravel php artisan db:seed
```

### Verify

```bash
curl http://localhost:8000/api/health
# {"status": "healthy", "database": "connected"}

curl http://localhost:8001
# Laravel dashboard loads
```

### Access Points

| Service | URL | Owner |
|---------|-----|-------|
| Dashboard | `http://localhost:8001` | Steve |
| Admin Panel | `http://localhost:8001/admin` | Steve |
| FastAPI Docs | `http://localhost:8000/docs` | Derick |
| n8n Workflows | `http://localhost:5678` | Steve |
| Meilisearch | `http://localhost:7700` | Steve |

### Deployment

| Environment | Domain | Status |
|-------------|--------|--------|
| Development | `bungepulse.duckdns.org` | Active |
| Production | `bungepulse.co.ke` | Purchased, pending DNS migration |

---

## Repository Structure

**Root**

| Path | Purpose |
|------|---------|
| `README.md` | This file |
| `ARCHITECTURE.md` | Detailed technical architecture |
| `LICENSE` | AGPL-3.0 |
| `CONSTITUTIONAL_EDUCATION.md` | 19-article education library |
| `docker-compose.yml` | All services |
| `.env.example` | Environment template |

**Laravel (Steve Maloba) -- 61 files**

| Path | Purpose |
|------|---------|
| `laravel/app/Http/Controllers/` | 4 controllers |
| `laravel/app/Services/` | DerickApiService (circuit breaker) |
| `laravel/app/Http/Middleware/` | SecurityHeaders (CSP, HSTS) |
| `laravel/app/Filament/Resources/` | CommitmentResource, UserResource |
| `laravel/app/Providers/Filament/` | AdminPanelProvider |
| `laravel/config/security_dimensions.php` | 8 dimensions, EN/SW, Katiba |
| `laravel/config/stakeholders.php` | 37 groups, 9 categories |
| `laravel/config/counties_constituencies.php` | 47 counties, 290 constituencies |
| `laravel/config/goke_sources.php` | 38 official .go.ke URLs |
| `laravel/resources/views/` | 14 Blade templates |
| `laravel/routes/web.php` | Web routes |
| `laravel/database/seeders/` | Database seeders |
| `laravel/n8n/workflows/` | 15 JSON workflow files |
| `laravel/Dockerfile` | PHP 8.2-FPM + nginx + supervisord |
| `laravel/docker-compose.yml` | 5 containers |

**FastAPI (Derick Ochieng) -- 41 files**

| Path | Purpose |
|------|---------|
| `fastapi/app/api/routes/` | 10 route modules, 19 endpoints |
| `fastapi/app/nlp/` | e5-small-v2 NLP engine |
| `fastapi/app/sms/` | celcom.py + whatsapp.py |
| `fastapi/app/tasks/` | Celery: processor, alerts, scores |
| `fastapi/app/config/` | 8 security dimensions + keywords |
| `fastapi/app/models.py` | 8 SQLAlchemy tables |
| `fastapi/app/crypto.py` | SHA-256 + AES-256 (DPA 2019) |
| `fastapi/app/main.py` | FastAPI entry, CORS, 10 routers |
| `fastapi/alembic/` | Database migrations |
| `fastapi/tests/` | Unit tests |
| `fastapi/Dockerfile` | Python 3.11 + e5-small-v2 baked in |
| `fastapi/docker-compose.yml` | 3 containers (joins Steve's network) |
| `fastapi/requirements.txt` | 15 pinned dependencies |

**Documentation**

| Path | Purpose |
|------|---------|
| `docs/GAP_BRIEF.md` | Gap analysis |
| `docs/PREDICTION_POLICY.md` | Prediction policy |
| `docs/EDITORIAL_QUALITY.md` | Editorial standards |
| `docs/STAKEHOLDER_TAXONOMY.md` | Stakeholder taxonomy |

**Total: 102 files** (61 frontend + 41 backend). All code written Week 1. Week 2 is deployment only.

---

## Team

| Role | Name | Responsibilities |
|------|------|-----------------|
| **Team Lead** | Gerald Kombo | Architecture, product strategy, content, Kiswahili templates, editorial QA |
| **Frontend Engineer** | Steve Maloba | Laravel 11, Filament admin, n8n workflows, Meilisearch, dashboard UX |
| **Backend Engineer** | Derick Ochieng | FastAPI, Celery/Redis, NLP (e5-small-v2), MariaDB, WhatsApp bot, Celcom Africa SMS |

---

<div align="center">

**BungePulse** -- Democratic early-warning infrastructure for Kenya's Parliament.

*AI processes. Humans approve. Citizens know.*

NIRU AI Hackathon 2026 | Project ID: PJ2A5E23R

</div>
