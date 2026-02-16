# bungepulse-ai-tracker
AI parliamentary accountability tracker for Kenya. Ingests Hansard, Votes &amp; Proceedings, and Order Papers. Uses spaCy and transformers for entity extraction and commitment detection. Built with Laravel, FastAPI, Celery, Redis, MySQL, MariaDB, n8n, and Docker. NIRU AI Hackathon 2026.
<div align="center">

# BungePulse

### National Security Infrastructure for Parliamentary Accountability

[![AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue.svg)](LICENSE)
[![Python 3.11+](https://img.shields.io/badge/Python-3.11+-3776AB.svg?logo=python&logoColor=white)](https://python.org)
[![PHP 8.3](https://img.shields.io/badge/PHP-8.3-777BB4.svg?logo=php&logoColor=white)](https://php.net)
[![Laravel 11](https://img.shields.io/badge/Laravel-11-FF2D20.svg?logo=laravel&logoColor=white)](https://laravel.com)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-009688.svg?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED.svg?logo=docker&logoColor=white)](https://docker.com)
[![Status](https://img.shields.io/badge/Status-In_Development-yellow.svg)]()
[![Hackathon](https://img.shields.io/badge/NIRU_AI_Hackathon-2026-1B5E20.svg)]()

**Democratic early-warning system â€” not civic tech.**

*AI processes. Humans approve. Citizens know.*

NIRU AI Hackathon 2026 â€” Submission Deadline: March 26, 2026

[The Problem](#the-problem) â€¢
[Security Framework](#five-dimensional-national-security-framework) â€¢
[Four AI Moments](#the-four-ai-moments) â€¢
[Architecture](#architecture) â€¢
[Dashboard](#dashboard-architecture) â€¢
[WhatsApp Bot](#whatsapp-bot) â€¢
[Trust & Safety](#trust-safety--legal) â€¢
[Quick Start](#quick-start) â€¢
[Roadmap](#roadmap)

</div>

---

## The Problem

Kenya has early-warning systems for terrorism (NCTC), drought (NDMA), and disease (KEMRI).

**Parliament â€” where the money, laws, and power are controlled â€” has nothing.**

349 MPs. 67 Senators. 26 data sources. 200â€“400 pages of parliamentary text per sitting day. No system connects what an MP says in January to how they vote in March. No system tracks which Cabinet Secretary dodges parliamentary summons 8 out of 10 times. No system tells 1.2 million people in Kibera that the health centre promised in 2024 is now 580 days overdue.

BungePulse fills that gap.

---

## Five-Dimensional National Security Framework

Every tab in the dashboard, every WhatsApp alert, every AI pipeline output connects to at least one of these five dimensions. This is how BungePulse organizes accountability â€” not as a transparency exercise, but as national security infrastructure.

| Dimension | Threat Without BungePulse | What BungePulse Tracks |
|-----------|--------------------------|----------------------|
| **Political Security** | MP promises anti-corruption legislation in January, quietly votes against it in March. Nobody connects those two moments across 400 pages of Hansard. Eroded trust is how democracies collapse. | Speech-to-vote contradictions detected automatically via semantic matching |
| **Economic Security** | Every ghost project, every diverted budget that goes untracked signals to investors that institutions don't work. Sovereign credibility erodes. | Budget discrepancies, CDF utilization, project completion rates, financial anomalies |
| **Health Security** | The Kibera Health Centre stalled 18 months. 1.2 million people with reduced health access. That's pandemic preparedness failure. | Stalled health facilities, budget utilization gaps, construction timeline tracking |
| **Education Security** | When CBC funding commitments aren't tracked, school infrastructure stalls. Under-educated generations become vulnerable to radicalization. | Education budget votes tracked to actual school construction outcomes |
| **Environmental Security** | Conservation funds stolen, climate adaptation budgets diverted â€” these become resource conflicts and displacement. | Parliamentary votes on environmental budgets tracked to implementation |

---

## Constitutional Grounding

Every feature traces to specific articles of the **Constitution of Kenya 2010**. This is structural defense â€” if anyone challenges BungePulse's right to exist, the response is: *Article 1* (sovereignty belongs to the people), *Article 35* (access to information), *Article 118* (public participation).

Every constitutional citation in BungePulse â€” dashboard, WhatsApp alert, bill detail, MP profile â€” becomes a **clickable learning moment** with plain-language summaries at Grade 8 reading level and Kiswahili translations. Most Kenyans have never read their Constitution. BungePulse builds constitutional literacy at scale.

<details>
<summary><strong>19 Constitutional Articles Mapped Across All Features</strong></summary>
<br>

| Article | What It Covers | Feature It Powers |
|---------|---------------|-------------------|
| Art. 1 | Sovereignty belongs to the people | MP accountability tracking, system rationale |
| Art. 10 | National values (transparency, accountability) | Overall system rationale |
| Art. 27 | Equality (at least 1/3 gender representation) | Vote gender breakdowns |
| Art. 35 | Right to information | WhatsApp bot, data access |
| Art. 43 | Right to health, housing, education | Projects tracker, health facility monitoring |
| Art. 53 | Children's rights | Intergenerational impact flags (long-term debt) |
| Art. 54 | Persons with disabilities | WCAG 2.1 AA compliance, voice note summaries |
| Art. 56 | Marginalized communities | Community impact tags |
| Art. 63 | Community land | Indigenous community alerts (Turkana oil, Maasai corridors) |
| Art. 75 | Conduct of State officers | Accountability tracking, performance monitoring |
| Art. 91 | Political parties | Party discipline index |
| Art. 94â€“96 | Parliament's role (lawmaking) | Vote and bill tracking |
| Art. 103 | Vacation of office (MPs) | MP removal tracking, performance monitoring |
| Art. 114 | Public finance | Budget and bill pipeline |
| Art. 118 | Public participation | Citizen campaigns, evidence submission |
| Art. 122 | Quorum of Parliament | Sitting outcomes, plenary monitoring |
| Art. 153 | Summoning before Parliament | Summons tracker, ministry grades, proxy detection |
| Art. 201, 202, 217 | Finance, revenue, division of funds | Project budgets, CDF tracking |
| Art. 226 | Accounts and audit | Financial tracking, Auditor-General reports |

</details>

---

## The Four AI Moments

Four capabilities where no human team could replicate what AI does. Each has a live demo moment designed for judges.

### Moment 1: Scale Detection

Parliament produces 200â€“400 pages per sitting day. A human team would need **15 full-time researchers** to monitor this daily. BungePulse processes it all before dawn.

> **Demo:** Raw Hansard paragraph on screen. Click "Process." Watch extraction: MP name, topic tags, commitment candidate, confidence score, linked bill, linked vote. **2 seconds.** A human takes 20 minutes per speech segment. There are 300 per sitting day.

**Tech:** Custom spaCy NER model trained on Kenyan parliamentary text. Celery + Redis for automated 6:00 AM daily processing.

### Moment 2: Cross-Source Contradiction Detection

Hansard says 210 voted Yes. Votes & Proceedings says 208. **The 2-vote discrepancy is flagged automatically.** A human would need to compare two PDFs side by side, line by line.

> **Demo:** Verification panel â€” Hansard vs V&P, the 2-vote gap flagged in amber. *"This is how we catch data manipulation or OCR errors before they become published misinformation."*

**Five anomaly types detected:**

1. Impossible totals (vote count > 349 MPs)
2. Missing MPs (named in Hansard, absent from roll-call)
3. Mathematical errors (Yes + No + Abstain + Absent â‰  Total)
4. Title mismatches across sources
5. Temporal inconsistencies (commitment date after vote date)

All flagged for mandatory human investigation before publication.

### Moment 3: Commitment-to-Vote Linking

An MP says *"I will fight corruption"* on January 15. On March 8, they vote **NO** on the Anti-Corruption Amendment Bill. 52 days apart. Different documents. Different formatting. The semantic matching engine connects them automatically.

> **Demo:** Evidence tab on bill detail â€” the chain: Hansard quote (Jan 15, p.23) â†’ Bill tabled (Feb 1) â†’ Committee Stage (Feb 20) â†’ Vote (Mar 8) â†’ Alignment verdict. *"No human is reading 8 weeks of Hansard to catch that contradiction."*

**Tech:** Sentence embeddings (all-MiniLM-L6-v2) compute similarity between speech text and bill text. Timeline validation ensures commitment date < vote date. Alignment score calculated **deterministically**: `(matching votes / relevant votes) Ã— 100`.

### Moment 4: Pattern Detection Across Time

One CS missing one summons is an incident. The same ministry sending proxies **8 out of 10 times** over 90 days is a pattern of systematic avoidance. BungePulse detects it from Order Paper and Hansard cross-referencing.

> **Demo:** Ministry Responsiveness Index. Point to the lowest-scoring ministry. *"No journalist has the time to manually cross-check 90 days of Order Papers against 90 days of Hansard. AI does."*

---

## Architecture

Dual-service system connected via REST APIs inside Docker.

```
â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”
â”‚                      DOCKER ENVIRONMENT                          â”‚
â”‚                                                                  â”‚
â”‚  â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”              â”Œâ”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”  â”‚
â”‚  â”‚  LARAVEL STACK    â”‚    REST     â”‚  FASTAPI STACK            â”‚  â”‚
â”‚  â”‚  (Steve Maloba)   â”‚    API      â”‚  (Derick Ochieng)         â”‚  â”‚
â”‚  â”‚                   â”‚             â”‚                           â”‚  â”‚
â”‚  â”‚  Laravel 11      â—„â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â–º  FastAPI                   â”‚  â”‚
â”‚  â”‚  (Dashboard +     â”‚             â”‚  (NLP API + Admin         â”‚  â”‚
â”‚  â”‚   Auth + Search)  â”‚             â”‚   + WhatsApp Webhook)     â”‚  â”‚
â”‚  â”‚       â”‚           â”‚             â”‚       â”‚                   â”‚  â”‚
â”‚  â”‚       â–¼           â”‚             â”‚       â–¼                   â”‚  â”‚
â”‚  â”‚  MySQL 8.0        â”‚             â”‚  Celery + Redis 7.x      â”‚  â”‚
â”‚  â”‚  (14 canonical    â”‚             â”‚  (6 AM daily pipeline +   â”‚  â”‚
â”‚  â”‚   tables)         â”‚             â”‚   background tasks)       â”‚  â”‚
â”‚  â”‚       â”‚           â”‚  trigger    â”‚       â”‚                   â”‚  â”‚
â”‚  â”‚       â–¼           â”‚             â”‚       â–¼                   â”‚  â”‚
â”‚  â”‚  n8n (Self-      â—„â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€  Python NLP Engine        â”‚  â”‚
â”‚  â”‚   Hosted)         â”‚             â”‚  spaCy + Transformers     â”‚  â”‚
â”‚  â”‚  (Ingestion +     â”‚             â”‚  (NER + Classification    â”‚  â”‚
â”‚  â”‚   Orchestration)  â”‚             â”‚   + Verification)         â”‚  â”‚
â”‚  â”‚                   â”‚             â”‚       â”‚                   â”‚  â”‚
â”‚  â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜             â”‚       â–¼                   â”‚  â”‚
â”‚                                    â”‚  MariaDB 11.x            â”‚  â”‚
â”‚                                    â”‚  (8 audit/provenance     â”‚  â”‚
â”‚                                    â”‚   tables â€” append-only)  â”‚  â”‚
â”‚                                    â”‚       â”‚                   â”‚  â”‚
â”‚                                    â”‚       â–¼                   â”‚  â”‚
â”‚                                    â”‚  Twilio / Meta            â”‚  â”‚
â”‚                                    â”‚  WhatsApp Cloud API       â”‚  â”‚
â”‚                                    â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜  â”‚
â””â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”€â”˜
```

### Tech Stack

| Component | Technology | Role | Security Dimension |
|-----------|------------|------|--------------------|
| Dashboard + Auth | Laravel 11 (PHP 8.3) | 10-tab dashboard, authentication, search | All five dimensions |
| Ingestion | n8n (self-hosted) | Source ingestion workflows, scheduling triggers | Scale Detection (Moment 1) |
| Canonical DB | MySQL 8.0 | 14 tables: MPs, bills, votes, alerts, users, campaigns | Data integrity |
| NLP API + Admin | FastAPI (Python 3.11+) | NLP endpoints, admin review, WhatsApp webhook | Moments 1â€“4 |
| Background Tasks | Celery + Redis 7.x | 6 AM daily pipeline, parallel document processing | Automated monitoring |
| NLP Engine | spaCy + transformers | Parliamentary NER, classification, semantic matching | Entity extraction, linking |
| Audit DB | MariaDB 11.x | 8 tables: immutable logs, SHA-256 hashes, provenance | Tamper-proof records |
| Containers | Docker + Docker Compose | Repeatable setup, isolated services | Operational resilience |

---

## The Daily Pipeline

```
06:00 AM  â€” Ingestion â€”â€”â€”â€”â€”â€”â€”â€” Download + normalize from 26 parliamentary sources
          â€” Archival â€”â€”â€”â€”â€”â€”â€”â€”â€”â€” Store raw documents + SHA-256 content hashes
          â€” NLP â€”â€”â€”â€”â€”â€”â€”â€”â€”â€”â€”â€”â€” Entity extraction + commitment candidate detection
          â€” Linking â€”â€”â€”â€”â€”â€”â€”â€”â€”â€”â€” Semantic similarity: speech â†’ bill â†’ vote chains
          â€” Verification â€”â€”â€”â€”â€” Hansard Ã— V&P Ã— Order Papers cross-check
06:15 AM  â€” Queue â€”â€”â€”â€”â€”â€”â€”â€”â€”â€” Flagged items enter human review queue

07:00 AM  â€” Human Review â€”â€”â€”â€”â€” Approve / block / investigate (immutably logged)
          â€” Every decision: reviewer ID + timestamp + action + rationale + IP hash

09:00 AM  â€” Publishing â€”â€”â€”â€”â€” WhatsApp alerts + dashboard updates go live
          â€” Citizens know before Parliament's morning sitting begins
```

**Golden Rule:** AI processes. Humans approve. Citizens know.

---

## Dashboard Architecture

10 tabs. 10 constitutional mandates. Zero redundancy.

| Tab | National Security Need | Constitutional Anchor |
|-----|----------------------|-----------------------|
| **Overview** | System health + 5-dimension security monitor | Art. 1, 10 |
| **Recent Votes** | How Parliament voted (gender/party breakdowns) | Art. 94â€“96, 27 |
| **MPs Tracker** | Individual MP accountability + commitment tracking | Art. 1, 75, 103 |
| **Bills Pipeline** | Legislation progress (5-stage visual flow) | Art. 94, 114 |
| **Summons Tracker** | Executive responsiveness + Ministry Grade Cards (Aâ€“F) | Art. 153 |
| **Party Positions** | Party discipline index | Art. 91 |
| **Campaigns** | Citizen mobilization + WhatsApp polls | Art. 118 |
| **WhatsApp Bot** | Population-scale information delivery | Art. 35 |
| **Projects** | Budget-to-ground reality (tri-source tracking) | Art. 43, 201, 217 |
| **About** | Methodology transparency + "How AI Works" | Art. 35 |

### Eight Dashboard Components Built for Judges

1. **"Why BungePulse" Welcome Card** â€” Democratic early-warning system title, four AI capability bullets, constitutional references. Sets the national security frame before judges click anything.

2. **AI Processing Today Panel** â€” Live proof: documents ingested (47), entities extracted (312 MPs, 23 Bills, 8 Votes), commitment candidates found (14), cross-source checks (6 matched, 2 flagged), evidence links (23 chains). Footer: *"AI processes. Humans approve. Citizens know by 7 AM."*

3. **Governance Security Monitor** â€” Five traffic-light cards: Political Security (3 contradictions â€” Amber), Economic Security (KSh 4.2B flagged â€” Red), Health Security (2 stalled facilities â€” Amber), Education Security (CBC report 41 days overdue â€” Red), Environmental Security (No anomalies â€” Green).

4. **AI Analysis Tab (Bill Detail)** â€” Entity extraction, commitment detection with confidence score, cross-source verification (Hansard vs V&P vs Order Paper), semantic linking to prior speeches.

5. **AI Commitment Tracker (MP Detail)** â€” Promise â†’ evidence â†’ status. Example: *"I will fight corruption"* (Hansard Jan 15 p.23) â†’ Voted YES (Anti-Corruption Bill, V&P Feb 6) â†’ ALIGNED. Alignment Score: 80%. Human reviewer: Approved (R-041).

6. **Pattern Detection Card (Summons Tab)** â€” Ministry of Health: CS summoned 4 times, appeared 1 (25%), PS proxy 2 times, no-show 1, questions deferred 3 (oldest 67 days). *"This pattern would take a researcher 40 hours. AI detected it in 8 seconds."*

7. **Persistent Footer Status Bar** â€” Every page: `Pipeline healthy | Last sync: Today 6:04 AM | 47 docs processed | 7 items in human review | AI confidence avg: 93%`

8. **"How AI Works" Sub-Tab** â€” What AI Does (6 bullets), What AI Does NOT Do (5 bullets), The Pipeline (visual flow), Why This Matters for Security.

### Original Innovations

Features born during development â€” not in any original planning document:

- **Ministry Grade Cards (Aâ€“F)** â€” Ministries graded on summons responsiveness: A (0â€“7 days, â‰¥95%) through F (>90 days, <60%). Visually devastating when a ministry scores F.
- **Proxy Power Map** â€” When PS (Parliamentary Affairs) appears in 9 of 12 Health summons, that's not normal delegation â€” it's systematic avoidance made visible.
- **County Radar** â€” Multi-committee geographic clustering. Turkana appeared in 3 committees on the same day (Energy, Lands, Roads). No journalist catches that without AI.
- **580-Day Overdue Counter** â€” Kibera Health Centre: KSh 69.5M from 3 sources (National KSh 30M + NG-CDF KSh 20M + World Bank KSh 19.5M), promised within 6 months (Jan 2024), 580+ days overdue. Updates daily.
- **Population-Weighted Representation** â€” An MP vote shows *"representing 120,000 constituents"* not just "1 of 349."

### Design System

Dark theme: `#0f172a` base, `#1e293b` surfaces, `#38bdf8` accent. Kenya colors `#1B5E20` (green) and `#B71C1C` (red) used strategically. Information-dense, professional aesthetic â€” not flashy, but credible.

---

## NLP Pipeline

| Step | Technology | What It Does | Security Moment |
|------|-----------|-------------|-----------------|
| Entity Extraction | spaCy + custom NER | Extracts MP names, bill titles, committees, counties | Moment 1: Scale |
| Commitment Detection | Rule-based patterns (MVP) | Flags "I commit", "I will ensure", "we shall" + confidence scores | Moment 3: Linking |
| Semantic Matching | sentence-transformers (all-MiniLM-L6-v2) | Speech-to-bill similarity for evidence chains | Moment 3: Linking |
| Verification | Custom Python engine | Hansard Ã— V&P Ã— Order Papers cross-check | Moment 2: Contradiction |
| Pattern Detection | Time-series analysis | 90-day proxy frequency, ministry responsiveness | Moment 4: Patterns |
| Anomaly Detection | Rule-based checks | 5 anomaly types flagged automatically | Moment 2: Contradiction |

**Confidence Gates:** â‰¥95% auto-approve â†’ â‰¥80% human review â†’ â‰¥40% auto-flag for investigation â†’ <40% rejected

---

## WhatsApp Bot

Kiswahili-first. 9 commands. Article 35 (access to information) at population scale â€” 29 million potential users.

| Kiswahili | English | Function |
|-----------|---------|----------|
| `ANZA` | `START` | Opt in, store phone + constituency |
| `ACHA` | `STOP` | Opt out, delete all data |
| `MBUNGE WANGU` | `MY MP` | MP profile + voting record (returns **both** constituency MP and County Woman Representative â€” Art. 27) |
| `LEO` | `LATEST` | Today's votes + active polls |
| `KURA` | `POLL` | View and respond to active polls |
| `MATOKEO` | `RESULTS` | Poll results by constituency |
| `DATA YANGU` | `DATA` | View all stored user data |
| `FUTA` | `DELETE` | Permanently erase all data |
| `MSAADA` | `HELP` | List all commands |

**Context-aware sessions:** If you just asked about Finance Bill, `KURA` defaults to showing the Finance Bill vote.

**"MY MP" returns both representatives** â€” constituency MP *and* County Woman Representative. Kenya has 47 CWRs representing entire counties. Most tracking systems ignore them. BungePulse doesn't â€” Article 27 (gender rule) is constitutional, not optional.

### 48-Hour Poll Cycle

Replaces X Spaces. WhatsApp polls produce **structured, measurable, constituency-level citizen voice** shareable with parliamentary committees as evidence.

| Phase | Timeline | What Happens |
|-------|----------|-------------|
| **Day 1** | 9 AM â€“ 6 PM | Issue verified (triple-source â‰¥80%), poll drafted, sent to affected constituencies, media backgrounder distributed |
| **Day 2** | 6 PM â€“ 8 PM | Poll closes, results aggregated by constituency, broadcast to participants + media partners |
| **Day 3** | Ongoing | Monitor institutional response, create `outcome_event` record if action taken, broadcast success alert |

---

## Data Model

### MySQL (Laravel) â€” 14 Canonical Tables

```
constituencies  mps  sitting_days  documents  bills_or_motions
vote_events  mp_votes  speech_segments  alerts  whatsapp_users
polls  poll_responses  campaigns  outcome_events
```

### MariaDB (FastAPI) â€” 8 Audit/Provenance Tables

```
commitment_candidates  evidence_links  verification_results
review_decisions  nlp_run_logs  anomaly_flags
content_hashes  provenance_chains
```

**Audit principle:** `review_decisions` is append-only. Source documents archived with SHA-256 content hashes. No record can be deleted or modified after creation.

---

## Admin Review Console

Three queues. Zero high-stakes claims publish without explicit human approval.

| Queue | Contents | Actions |
|-------|---------|---------|
| **Commitment Candidates** | AI-flagged statements pending verification | Approve / reject with evidence links |
| **Anomalies** | Cross-source discrepancies | Investigate / resolve / escalate |
| **High-Stakes Alerts** | Accountability alerts awaiting publication | Approve / block with rationale |

Every decision logged immutably: reviewer ID, timestamp, action, reasoning, IP hash, linked source documents.

---

## 10 Invisible Constituencies

Stakeholders missing from all original planning. Each requires specific dashboard design.

> *"BungePulse isn't built for 'citizens' in the abstract. It's built for the Turkana grandmother whose land sits on oil. The diaspora son in Houston who can't attend the Finance Bill debate. The blind voter in Kibera who's never read Hansard."*

| # | Constituency | National Security Need | Feature |
|---|-------------|----------------------|---------|
| 1 | **Diaspora Kenyans** (4M, KSh 400B remittances) | Economic Security: remittance legislation affects sovereign revenue | Time-zone aware alerts, Diaspora Impact tag |
| 2 | **Persons with Disabilities** (6M) | Political Security: exclusion undermines democratic participation | WCAG 2.1 AA, voice note summaries (Art. 54) |
| 3 | **Indigenous Communities** | Environmental Security: land decisions made without knowledge | Community Impact tags (Art. 56, 63) |
| 4 | **The Judiciary** | Political Security: courts need parliamentary intent records | Intent Record on bill detail pages |
| 5 | **Trade Unions** (COTU, KNUT, KMPDU) | Economic Security: legislation affects millions of workers | Sector Watch alerts |
| 6 | **SMEs** (80% of economy, 90% of employment) | Economic Security: VAT changes affect livelihoods | `BIASHARA` command, Business Impact translations |
| 7 | **Whistleblowers** | All dimensions: insiders see gaps between promises and reality | Encrypted tip channel (separate from public system) |
| 8 | **Political Parties** | Political Security: discipline tracking prevents fragmentation | Party Discipline Index |
| 9 | **Diplomatic Missions** | Economic Security: governance assessments affect investment | API/About page for international-grade credibility |
| 10 | **Children & Future Generations** | All dimensions: today's debt is tomorrow's burden | Intergenerational Impact flag on 25-year commitments (Art. 53) |

---

## Prediction Policy

The line between insight and accusation is where BungePulse lives or dies.

### Allowed: System-Level Risk Signals

Historical patterns from 4 years of parliamentary voting data (2022â€“2026):

1. Bills at Committee Stage with <60% party alignment historically fail at Third Reading 73% of the time
2. Ministries sending proxies >50% in Q1 tend to have highest unanswered question backlogs by Q4
3. Constituencies where CDF utilization drops below 40% in H1 historically don't recover by year-end
4. When a CS promises to table a report "next month" and doesn't â€” 78% chance they won't table it at all this session
5. FLLoCA-type devolved projects missing first milestone by 30+ days â€” 65% chance of stalling completely

### Banned: Individual Predictions

| Banned | Why |
|--------|-----|
| "This MP will vote against..." | Profiling, not pattern analysis |
| "This CS will not show up..." | Prejudgment |
| "This Governor is likely corrupt..." | Accusation |

**Framing rule:** Always *"historically, when X pattern occurs, Y tends to follow."* Never *"this person will do X."*

---

## Governance Design Patterns

What separates national security infrastructure from a basic dashboard.

| Pattern | How It Works | Security Impact |
|---------|-------------|-----------------|
| **Triple-Source Verification** | Every high-stakes claim cross-checked: Hansard Ã— V&P Ã— Order Papers. Two agree, third contradicts = amber flag for human investigation. | Prevents data manipulation becoming published misinformation |
| **Absence as First-Class Data** | Non-participation and proxy substitution are trackable, visible patterns â€” not blank cells | Exposes systematic avoidance of parliamentary accountability |
| **Bill Lifecycle Pipeline** | 5-stage visual flow: First Reading â†’ Committee â†’ Second Reading â†’ Third Reading â†’ Assent. Each stage shows who spoke, voted, amended. | Makes legislation a story, not a spreadsheet row |
| **Population-Weighted Votes** | MP absence shows "120,000 constituents relied on party representation" â€” not just "1 absent" | Reframes every vote in human terms |
| **Verifiable Hashes** | Every alert carries SHA-256 hash of source documents. Independently verifiable by any journalist, CSO, or citizen. | Tamper-proof publication record |
| **Immutable Audit Trail** | `review_decisions` table: append-only, reviewer ID, timestamp, action, IP hash. No deletion possible. | Every approval traceable forever |
| **Independent Trust Board** (Phase 4) | Non-partisan oversight, quarterly bias audits by constituency/party/coalition | Prevents political capture |

---

## Real Data Integration

Three actual parliamentary committee alerts from **February 12, 2026** replaced all placeholder content. Judges specifically want real data, not mock data.

<details>
<summary><strong>February 12, 2026 â€” Three Committee Alerts + Seven Insights</strong></summary>
<br>

**Alert 1: Joint Committee on Energy** (Political + Economic + Environmental Security)
- Venue: Hilton Garden Inn, Machakos County (off-site â€” flagged)
- Agenda: South Lokichar Field Development Plan and Production Sharing Contracts
- Appearing: CS (Water/Sanitation), CS (Energy & Petroleum), Gulf Energy (private sector), KRA (statutory body), CS (Interior)

**Alert 2: Senate Lands Committee** (Environmental Security)
- Venue: Bunge Tower, Committee Room 1
- Agenda: Status of County Projects funded by FLLoCA (Financing Locally-Led Climate Action)
- Appearing: Governor of Bungoma County, Governor of Turkana County

**Alert 3: Senate Roads Committee** (Economic Security)
- Venue: Bunge Tower, Committee Room 2
- Agenda: Status of roads in Turkana County
- Appearing: Governor of Turkana County

**Seven Insights Extracted:**

1. **Joint committees exist** â€” Need "Joint" badge when both chambers sit together. Signals high national importance.
2. **County governors appear before Senate** â€” Summons Tracker must expand beyond CS/PS. Entity scope change.
3. **Private sector actors appear** â€” Gulf Energy before a joint committee proves private entities are part of the accountability ecosystem.
4. **Turkana in ALL THREE committees** â€” County Radar justified instantly. One county, three committees, same day.
5. **Committees meet outside Parliament** â€” Hilton Garden Inn, Machakos is nowhere near Bunge Tower. Venue tracking with off-site flags required.
6. **FLLoCA is real devolved funds** â€” Perfect demo data for Projects view. Budget-to-ground tracking.
7. **Three new gap brief items** â€” Joint badge (1.3), County Radar (4.4), Expanded entity types (4.5).

</details>

---

## Trust, Safety & Legal

### Legal Disclaimer

This project and its outputs are provided "as is" without warranty of any kind. Nothing in this repository constitutes legal advice. All data sourced from official parliamentary records published by the Parliament of Kenya. Use at your own risk.

### Core Publication Rules

| Rule | Implementation |
|------|---------------|
| **Human-in-the-loop** | Zero high-stakes claims publish without explicit human approval |
| **Defamation-safe language** | "Voted differently from stated position" â€” never "broke promise", "lied", "corrupt" |
| **Triple-source verification** | Hansard Ã— V&P Ã— Order Papers. Confidence gates: 95/80/40 |
| **Non-partisan** | Same data, same methodology, same scrutiny â€” every MP, every party, every region |
| **No MP contact info** | System never publishes MP phone numbers or instructs citizens to "contact your MP" |

### Electoral Integrity Policy

90 days before a general election: publish only verified factual data. No new campaigns, no "worst MP" rankings, no targeted constituency pushes, no manipulative call-to-action targeting.

### Privacy & Data Protection (KDPA-Aligned)

- **Collected:** Phone number + optional constituency + language preference. Nothing else.
- **Never collected:** Names, national IDs, locations, political affiliations.
- **User control:** `FUTA`/`DELETE` erases everything. `DATA YANGU`/`DATA` shows what's stored.
- **Retention:** Stale records auto-purge after defined retention windows.

### Whistleblower Protection

Encrypted tip channel â€” completely separate from public WhatsApp. Source identity never published. Tips verified through standard pipeline before any action.

### Venue Safety

Off-site committee meetings: public channels show committee name, date, agenda, summoned parties, and "off-site" flag only. Exact hotel/room details restricted to accredited media. Constitutional basis: Art. 31 (privacy) balanced against Art. 35 (access to information).

---

## Existential Risks & Mitigations

| Risk | Mitigation |
|------|-----------|
| Parliament turns off the data tap | SHA-256 archive of all source documents, data resilience plan |
| Legal exposure | Factual framing only, pro-bono legal partnerships, disclaimers |
| Personal targeting of team | Register as organization, multiple admins, no single point of failure |
| Electoral weaponization | 90-day pre-election lockdown protocol |
| AI hype vs reality gap | Honest positioning: rule-based MVP, BERT is Phase 2 |
| It works and nobody cares | Lead with Kibera (580 days), prove outcomes not just transparency |
| Zero real user testing | 15 structured interviews planned post-hackathon |

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
# Edit .env with MySQL/MariaDB passwords and WhatsApp API credentials

docker-compose up --build

# Run migrations (once containers are up)
docker-compose exec laravel php artisan migrate
docker-compose exec fastapi alembic upgrade head

# Seed demo data (real Feb 12, 2026 parliamentary committee records)
docker-compose exec laravel php artisan db:seed
```

### Access Points

| Service | URL |
|---------|-----|
| Dashboard | `http://localhost:8000` |
| Admin Console | `http://localhost:8001/admin` |
| n8n Orchestration | `http://localhost:5678` |
| FastAPI Docs | `http://localhost:8001/docs` |

---

## Repository Structure

```
bungepulse-ai-tracker/
â”œâ”€â”€ README.md
â”œâ”€â”€ ARCHITECTURE.md
â”œâ”€â”€ LICENSE                          # AGPL-3.0
â”œâ”€â”€ CONSTITUTIONAL_EDUCATION.md      # 19-article education library
â”œâ”€â”€ docker-compose.yml
â”œâ”€â”€ .env.example
â”‚
â”œâ”€â”€ laravel/                         # Steve Maloba
â”‚   â”œâ”€â”€ app/
â”‚   â”‚   â”œâ”€â”€ Http/Controllers/
â”‚   â”‚   â”œâ”€â”€ Models/
â”‚   â”‚   â””â”€â”€ Services/
â”‚   â”œâ”€â”€ database/migrations/
â”‚   â”œâ”€â”€ resources/views/             # 10-tab dashboard (Blade templates)
â”‚   â”œâ”€â”€ routes/
â”‚   â””â”€â”€ Dockerfile
â”‚
â”œâ”€â”€ fastapi/                         # Derick Ochieng
â”‚   â”œâ”€â”€ app/
â”‚   â”‚   â”œâ”€â”€ api/
â”‚   â”‚   â”œâ”€â”€ models/
â”‚   â”‚   â”œâ”€â”€ nlp/
â”‚   â”‚   â”‚   â”œâ”€â”€ entity_extraction.py
â”‚   â”‚   â”‚   â”œâ”€â”€ commitment_detection.py
â”‚   â”‚   â”‚   â”œâ”€â”€ semantic_matching.py
â”‚   â”‚   â”‚   â”œâ”€â”€ verification_engine.py
â”‚   â”‚   â”‚   â””â”€â”€ anomaly_detection.py
â”‚   â”‚   â”œâ”€â”€ celery_tasks.py
â”‚   â”‚   â””â”€â”€ whatsapp/
â”‚   â”œâ”€â”€ alembic/
â”‚   â””â”€â”€ Dockerfile
â”‚
â”œâ”€â”€ n8n/
â”‚   â””â”€â”€ workflows/                   # Ingestion + orchestration flows
â”‚
â”œâ”€â”€ docs/
â”‚   â”œâ”€â”€ API.md
â”‚   â”œâ”€â”€ DEPLOYMENT.md
â”‚   â”œâ”€â”€ LEGAL.md
â”‚   â”œâ”€â”€ PREDICTION_POLICY.md
â”‚   â””â”€â”€ ELECTORAL_INTEGRITY.md
â”‚
â””â”€â”€ demo/
    â”œâ”€â”€ screenshots/
    â”œâ”€â”€ sample-data/                 # Real Feb 12, 2026 committee data
    â””â”€â”€ video/
```

---

## Roadmap

### 11 Milestones â€” 39 Days â€” Feb 16 to Mar 26, 2026

| # | Milestone | Dates | Priority | Owner |
|---|-----------|-------|----------|-------|
| 1 | Infrastructure & Scaffolding | Feb 16â€“18 | CRITICAL | All |
| 2 | Data Ingestion & Document Processing | Feb 18â€“21 | CRITICAL | Steve + Derick |
| 3 | NLP Engine â€” Entity Extraction & Commitment Detection | Feb 18â€“22 | CRITICAL | Derick |
| 4 | Cross-Source Verification & Anomaly Detection | Feb 21â€“24 | HIGH | Derick |
| 5 | Admin Review Console (Human-in-the-Loop) | Feb 23â€“25 | HIGH | Steve + Gerald |
| 6 | Dashboard â€” 10-Tab Navigation & Core Components | Feb 26â€“Mar 5 | CRITICAL | Steve + Gerald |
| 7 | Pattern Detection & Ministry Responsiveness | Mar 6â€“9 | HIGH | Derick |
| 8 | WhatsApp Bot â€” 9 Kiswahili Commands & Poll System | Mar 10â€“14 | HIGH | Derick + Gerald |
| 9 | Constitutional Education Layer (19 Articles) | Mar 15â€“16 | MEDIUM | Gerald + Steve |
| 10 | Real Data Integration & Kibera Project | Mar 17â€“20 | CRITICAL | All |
| 11 | Demo Video, Documentation & Submission | Mar 21â€“26 | CRITICAL | All |

Milestones 2 & 3 run in parallel (Steve handles ingestion while Derick builds NLP). Same for M4 & M5.

**Deadline: March 26, 2026** â€” Demo video + working system + technical documentation.

---

## Gap Brief â€” 21 Items Across 6 Themes

<details>
<summary><strong>View Complete Gap Brief</strong></summary>
<br>

**Theme 1: Bicameral Parliament & Committees**
- 1.1 Add Senate (67 Senators, Senate votes, committee summons) â€” judges will notice if absent
- 1.2 Committee-level tracking (names, members, schedules, reports as UI components)
- 1.3 Joint committee badge (both chambers sitting together â€” strong differentiator)

**Theme 2: Citizen Experience & Inclusion**
- 2.1 Citizen feedback loop ("What did this alert make you do?")
- 2.2 SMS fallback for non-smartphone users
- 2.3 Multilingual (Kiswahili minimum; Turkana/Luo/Kikuyu for county alerts â€” roadmap)
- 2.4 WCAG 2.1 AA accessibility (screen readers, high contrast, voice notes)

**Theme 3: Devolution & County Governance**
- 3.1 County-level data views (filter everything by constituency/county)
- 3.2 County budgets (revenue division, conditional grants, CDF tracking)
- 3.3 Projects view (FLLoCA as demo data: allocation â†’ debate â†’ vote â†’ implementation)

**Theme 4: Power Mapping & Executive Accountability**
- 4.1 Summons Tracker â€” CS/PS attendance vs expectation (MVP killer feature)
- 4.2 Proxy detection â€” who speaks on behalf of whom, how often
- 4.3 Unanswered questions tracker â€” deferred questions by ministry with aging
- 4.4 County Radar â€” multi-committee geographic clustering (Turkana 3 committees same day)
- 4.5 Expanded entity types â€” Governors, statutory bodies, private sector in Summons

**Theme 5: Data Integrity & Verification**
- 5.1 Verification UI â€” triple-source comparison shown visually
- 5.2 Immutable audit trail â€” every decision logged, SHA-256 hashed, tamper-proof
- 5.3 Data source health dashboard â€” uptime, freshness, last sync per source

**Theme 6: Sustainability & Safety**
- 6.1 Revenue model â€” citizen access free forever; paid newsroom/CSO/industry tiers
- 6.2 Electoral integrity policy â€” 90-day pre-election protocol
- 6.3 Legal shield â€” disclaimers, factual framing, pro-bono legal partnership
- 6.4 Venue disclosure policy â€” tiered by audience for physical safety

</details>

---

## Philosophical Foundations

Two frameworks that shaped every design decision:

**Dr. David Dixon's MIT Framework â€” AI as Teammate** (NIRU AI Symposium, January 2026): AI accelerates human capability 100x faster than manual methods, but humans retain final authority over all high-stakes outputs. This is why the Golden Rule exists.

**Lorna Okola's Three Pillars â€” Google DeepMind Africa:**
- **Stay Curious** â€” Process 400 pages daily because patterns hide in Hansard
- **Build With Empathy** â€” WhatsApp-first because that's where 29M Kenyans are, not Silicon Valley
- **Turn Constraints Into Advantages** â€” Kenya's constraints are prompt designs; the zero-cost stack makes the system replicable by any country

---

## Licensing

**GNU Affero General Public License v3.0 (AGPL-3.0)**

BungePulse is a network service. The AGPL ensures:
- Anyone can use, modify, and distribute the source code
- Modified versions run as public services must share source code
- National security infrastructure stays open â€” no proprietary parliamentary trackers from this codebase

Full license: [LICENSE](LICENSE)

---

## Contributing

Contributions welcome under AGPL-3.0:

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit changes (`git commit -m 'Add your feature'`)
4. Push (`git push origin feature/your-feature`)
5. Open a Pull Request with clear description

---

## Team

| Role | Name | Responsibility |
|------|------|---------------|
| **Team Lead** | Gerald Kombo | Architecture, product strategy, constitutional mapping, coordination |
| **Dev A â€” Laravel** | Steve Maloba | Laravel 11 dashboard, n8n orchestration, MySQL, Meilisearch |
| **Dev B â€” FastAPI** | Derick Ochieng | FastAPI, Celery, spaCy, MariaDB, WhatsApp API, NLP pipeline |

---

<div align="center">

**NIRU AI Hackathon 2026**

*AI processes. Humans approve. Citizens know.*

*Parliament makes decisions about all of them. We make sure all of them know.*

Built in Nairobi, Kenya ðŸ‡°ðŸ‡ª

</div>
