# bungepulse-ai-tracker
AI parliamentary accountability tracker for Kenya. Ingests Hansard, Votes &amp; Proceedings, and Order Papers. Uses spaCy and transformers for entity extraction and commitment detection. Built with Laravel, FastAPI, Celery, Redis, MySQL, MariaDB, n8n, and Docker. NIRU AI Hackathon 2026.
<div align="center">

# BungePulse

### AI Parliamentary Accountability Tracker

[![AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue.svg)](LICENSE)
[![Python 3.11+](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://python.org)
[![PHP 8.3](https://img.shields.io/badge/PHP-8.3-purple.svg)](https://php.net)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED.svg)](https://docker.com)
[![Status](https://img.shields.io/badge/Status-In_Development-yellow.svg)]()

*NIRU AI Hackathon 2026 -- Submission Deadline: March 26, 2026*

[About](#about) -- [Architecture](#architecture) -- [Quick Start](#quick-start) --
[Policies](#trust-safety--legal) -- [Roadmap](#roadmap) -- [Contributing](#contributing)

</div>

---

## About

BungePulse is an AI system designed to process Kenyan parliamentary documents (Hansard, Votes & Proceedings, Order Papers) and produce structured accountability data for a web dashboard and WhatsApp delivery.

This repository contains:
- A Laravel 11 dashboard and ingestion/orchestration layer
- A FastAPI service for NLP, verification, admin review, and WhatsApp webhook
- A background task queue (Celery + Redis)
- A canonical database (MySQL) plus an audit/provenance database (MariaDB)
- Docker Compose to run all services locally

**Important:**
- This project is under active development for a hackathon.
- Features described as "designed to" or "planned" are goals, not guarantees.
- No statements in this README should be interpreted as claims of operational deployment unless explicitly stated.

---

## What It Does (Designed Behavior)

- Ingest parliamentary PDFs/HTML from official sources
- Extract entities (MPs, bills, votes, committees) using NLP
- Flag commitment-like statements in MP speeches (MVP: rule-based patterns)
- Link speeches to bills/votes using semantic similarity
- Cross-check key facts across multiple parliamentary sources
- Flag discrepancies for human review (human-in-the-loop)
- Deliver verified alerts to citizens via WhatsApp and publish to dashboard

---

## Architecture

BungePulse runs as a dual-service system connected via REST APIs inside Docker.

```
+------------------------------------------------------------------+
|                      DOCKER ENVIRONMENT                          |
|                                                                  |
|  +------------------+              +--------------------------+  |
|  |  DEV A STACK     |    REST     |  DEV B STACK              |  |
|  |                  |    API      |                           |  |
|  |  Laravel 11     <-------------->  FastAPI                  |  |
|  |  (Dashboard +    |             |  (API + Admin Console     |  |
|  |   Auth + Search) |             |   + WhatsApp Webhook)     |  |
|  |       |          |             |       |                   |  |
|  |       v          |             |       v                   |  |
|  |  MySQL 8.0       |             |  Celery + Redis 7.x      |  |
|  |  (Canonical      |             |  (Background Tasks +     |  |
|  |   Data Store)    |             |   Scheduling)             |  |
|  |       |          |             |       |                   |  |
|  |       v          |  trigger    |       v                   |  |
|  |  n8n (Self-     <--------------  Python NLP Engine        |  |
|  |   Hosted)        |             |  spaCy + Transformers    |  |
|  |  (Ingestion +    |             |  (Entity Extraction +    |  |
|  |   Orchestration) |             |   Classification +       |  |
|  |                  |             |   Verification)           |  |
|  +------------------+             |       |                   |  |
|                                   |       v                   |  |
|                                   |  MariaDB 11.x            |  |
|                                   |  (Audit Logs +           |  |
|                                   |   Provenance Tracking)   |  |
|                                   |       |                   |  |
|                                   |       v                   |  |
|                                   |  Twilio / Meta            |  |
|                                   |  WhatsApp Cloud API       |  |
|                                   +--------------------------+  |
+------------------------------------------------------------------+
```

---

## Tech Stack

| Component | Technology | Role |
|----------|------------|------|
| UI + App | Laravel 11 (PHP 8.3) | Dashboard, auth, search |
| Ingestion/Orchestration | n8n (self-hosted) | Source ingestion workflows, scheduling triggers |
| Canonical DB | MySQL 8.0 | MPs, bills, votes, alerts, users |
| API + Admin | FastAPI (Python 3.11+) | NLP API, admin review, WhatsApp webhook |
| Background Tasks | Celery + Redis 7.x | Scheduled and parallel processing |
| NLP | spaCy + transformers | NER, classification, semantic similarity |
| Audit/Provenance DB | MariaDB 11.x | Immutable logs, hashes, verification records |
| Containerization | Docker + Docker Compose | Local dev + repeatable setup |

---

## Quick Start

### Prerequisites
- Docker + Docker Compose
- Git

### Setup
```bash
git clone https://github.com/geraldkombo/bungepulse-ai-tracker.git
cd bungepulse-ai-tracker

cp .env.example .env
# Edit .env with your MySQL/MariaDB passwords and WhatsApp credentials

docker-compose up --build

# Run migrations (once containers are up)
docker-compose exec laravel php artisan migrate
docker-compose exec fastapi alembic upgrade head

# Seed demo data
docker-compose exec laravel php artisan db:seed
```

### Access Points
| Service | URL |
|--------|-----|
| Dashboard | http://localhost:8000 |
| Admin Console | http://localhost:8001/admin |
| n8n | http://localhost:5678 |
| FastAPI Docs | http://localhost:8001/docs |

---

## Repository Structure

```
bungepulse-ai-tracker/
|-- README.md
|-- ARCHITECTURE.md
|-- LICENSE
|-- SECURITY.md
|-- docker-compose.yml
|-- .env.example
|
|-- laravel/                # Dev A -- Steve Maloba
|   |-- app/
|   |   |-- Http/Controllers/
|   |   |-- Models/
|   |   |-- Services/
|   |-- database/migrations/
|   |-- resources/views/
|   |-- routes/
|   |-- Dockerfile
|
|-- fastapi/                # Dev B -- Derick Ochieng
|   |-- app/
|   |   |-- api/
|   |   |-- models/
|   |   |-- nlp/
|   |   |   |-- entity_extraction.py
|   |   |   |-- commitment_detection.py
|   |   |   |-- semantic_matching.py
|   |   |   |-- verification_engine.py
|   |   |   |-- anomaly_detection.py
|   |   |-- celery_tasks.py
|   |   |-- whatsapp/
|   |-- alembic/
|   |-- Dockerfile
|
|-- n8n/
|   |-- workflows/
|
|-- docs/
|   |-- API.md
|   |-- DEPLOYMENT.md
|   |-- LEGAL.md
|   |-- SECURITY.md
|
|-- demo/
    |-- screenshots/
    |-- sample-data/
    |-- video/
```

---

## Data Model

**MySQL (Dev A) -- 14 tables** for canonical parliamentary data:

`constituencies` `mps` `sitting_days` `documents` `bills_or_motions` `vote_events` `mp_votes` `speech_segments` `alerts` `whatsapp_users` `polls` `poll_responses` `campaigns` `outcome_events`

**MariaDB (Dev B) -- 8 tables** for audit, provenance, and NLP results:

`commitment_candidates` `evidence_links` `verification_results` `review_decisions` `nlp_run_logs` `anomaly_flags` `content_hashes` `provenance_chains`

Audit principle: review decisions are append-only. Source documents are archived with SHA-256 content hashes.

---

## The Daily Pipeline (Designed)

Designed as an automated pipeline with human approval required for high-stakes publication:

```
- Ingestion: download + normalize from parliamentary sources
- Archival: store raw documents + SHA-256 hashes
- NLP: entity extraction + commitment candidate detection
- Linking: semantic similarity for speech-to-bill-to-vote evidence chains
- Verification: cross-source consistency checks
- Human review: approvals/rejections logged immutably
- Publishing: WhatsApp alerts + dashboard updates
```

---

## NLP Pipeline

| Step | Technology | What It Does |
|------|-----------|-------------|
| Entity Extraction | spaCy with custom NER model | Extracts MP names, bill titles, committee names, counties |
| Commitment Detection | Rule-based keyword matching (MVP) | Flags statements containing "I commit", "I will ensure", "we shall" |
| Semantic Matching | Sentence-transformers (all-MiniLM-L6-v2) | Computes similarity between speech text and bill text |
| Verification | Custom Python engine | Cross-checks Hansard vs V&P vs Order Papers, flags 5 anomaly types |
| Anomaly Types | Rule-based checks | Impossible vote totals, missing MPs, math errors, title mismatches, temporal inconsistencies |

**Note:** The MVP uses rule-based commitment detection. Fine-tuned BERT classification is planned for a later phase.

---

## WhatsApp Bot (Planned Commands)

| Command | Kiswahili | Function |
|--------|-----------|----------|
| START | ANZA | Register + set constituency |
| MY MP | -- | MP profile + voting record |
| LATEST | LEO | Latest parliamentary alerts |
| POLL | KURA | Active poll |
| RESULTS | MATOKEO | Poll results |
| DATA YANGU | -- | View stored user data |
| DELETE | FUTA | Delete user data |
| HELP | MSAADA | Help menu |

---

## Admin Review Console

Three review queues in the FastAPI admin console:

1. **Commitment Candidates** -- AI-flagged statements pending human verification
2. **Anomalies** -- Cross-source discrepancies requiring investigation
3. **High-Stakes Alerts** -- Accountability alerts awaiting approval before publication

Every review decision is logged immutably: reviewer ID, timestamp, action, and reasoning.

---

# Trust, Safety & Legal

## Legal Disclaimer
This project and its outputs are provided "as is" without warranty of any kind, express or implied. Nothing in this repository constitutes legal advice. All data is sourced from official parliamentary records published by the Parliament of Kenya. Use at your own risk.

## Source-of-Truth & Defamation-Safe Language
- All data and quotes are sourced from official parliamentary records
- The system does not assert intent or wrongdoing
- Neutral phrasing is enforced:
  - Use: "Voted differently from stated position"
  - Never: "Broke promise", "Lied", "Corrupt"
- Alignment scores are mathematical calculations from public voting records using a published formula

## Human-in-the-Loop Publication Rule
No high-stakes claims publish without explicit human approval, logged with:
- Reviewer ID
- Timestamp
- Decision (approve/reject)
- Rationale
- Links to source documents

## Verification Standard
Key facts are cross-checked across at least two independent parliamentary artifacts (Hansard, Votes & Proceedings, Order Papers). Discrepancies are flagged for mandatory human investigation before publication.

Five anomaly types detected: impossible vote totals, missing MPs, mathematical errors, title mismatches across sources, and temporal inconsistencies.

## Prediction Policy
**Allowed:** System-level risk signals framed historically using aggregate patterns. Example: "Bills matching this profile historically pass at Third Reading only 31% of the time."

**Banned:** Individual predictions about how a named MP, CS, or Governor will act. No accusations or probabilistic claims about corruption or criminality. Framing rule: always "historically, when X pattern occurs, Y tends to follow" -- never "this person will do X."

## Electoral Integrity Policy
During election-sensitive periods (90 days before a general election):
- Publish only verified factual data
- No new campaigns
- No "worst MP" rankings
- No targeted constituency pushes
- No manipulative call-to-action targeting

## Venue Safety (Physical Security)
For off-site committee meetings:
- Public channels show: committee name, date, agenda, summoned parties, and an "off-site" flag only
- Exact hotel/room details are restricted to accredited media and internal admin
- Constitutional basis: Art. 31 (privacy) balanced against Art. 35 (access to information)

## Privacy & Data Protection (KDPA-Aligned)
**Data minimization:** Collect only what is necessary (phone number + optional constituency + language preference). No names, national IDs, locations, or political affiliations.

**User control:** DELETE/FUTA command erases all user data. DATA YANGU command shows stored data.

**Retention:** Stale user records auto-purge after defined retention windows.

**Security:** Secrets stored in environment variables. Admin access restricted and logged. No MP contact information published. System never instructs citizens to "contact your MP."

## Whistleblower Protection
Encrypted tip channel (separate from public WhatsApp). Source identity never published. Tips verified through standard pipeline before any action.

## Non-Partisan Commitment
Same data, same methodology, same scrutiny for every MP regardless of party, region, or political alignment.

---

## Licensing

This project is licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**.

### Why AGPL-3.0

BungePulse is a network service (web dashboard + WhatsApp bot). The AGPL-3.0 ensures that:

1. **Anyone can use, modify, and distribute** the source code
2. **If someone runs a modified version as a public service**, they must make their source code available to users of that service
3. **The civic accountability tooling stays open** -- no one can take this code, modify it behind closed doors, and run a proprietary parliamentary tracking service without sharing improvements

This closes the "SaaS loophole" that exists in standard GPL licensing, which is critical for a project designed to serve the public interest.

Full license text: [LICENSE](LICENSE)

**AGPL-3.0 in plain terms:**
- You CAN: use, copy, modify, distribute, run as a service
- You MUST: share source code of modified versions (including network use), include license notice, state changes
- You CANNOT: sublicense, hold authors liable

---

## Security

If you discover a security vulnerability, do not open a public issue. Email the team privately. See [SECURITY.md](SECURITY.md) for disclosure policy.

---

## Roadmap

| Phase | Timeline | Goal |
|------|----------|------|
| MVP | Feb 16 - Feb 28, 2026 | Pipeline skeleton + demo dataset end-to-end |
| Integration | Mar 1 - Mar 20, 2026 | WhatsApp webhook + admin review loop + demo video |
| Submission | Mar 21 - Mar 26, 2026 | Polish + documentation + final testing + submission |

**Deadline: March 26, 2026** -- Demo video + working system + technical roadmap PDF.

---

## Contributing

Contributions are welcome under the AGPL-3.0 license:

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add your feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request with a clear description

By contributing, you agree that your contributions will be licensed under AGPL-3.0.

---

## Team

| Role | Name | Stack |
|------|------|-------|
| Team Lead | Gerald Kombo | Architecture, product strategy, coordination |
| Dev A | Steve Maloba | Laravel 11, n8n, MySQL 8.0, Meilisearch |
| Dev B | Derick Ochieng | FastAPI, Celery, spaCy, MariaDB 11.x, WhatsApp API |

---

<div align="center">

*NIRU AI Hackathon 2026*

</div>
