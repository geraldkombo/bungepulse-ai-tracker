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

**Democratic early-warning system -- not civic tech.**

*AI processes. Humans approve. Citizens know.*

NIRU AI Hackathon 2026 | Submission Deadline: March 26, 2026

[The Problem](#the-problem) |
[Security Framework](#five-dimensional-national-security-framework) |
[Four AI Moments](#the-four-ai-moments) |
[Architecture](#architecture) |
[Dashboard](#dashboard-architecture) |
[WhatsApp Bot](#whatsapp-bot) |
[Who Uses This](#who-uses-this) |
[Trust & Safety](#trust-safety--legal) |
[Quick Start](#quick-start) |
[Roadmap](#roadmap)

</div>

---

## The Problem

Kenya has early-warning systems for terrorism (NCTC), drought (NDMA), and disease (KEMRI).

**Parliament -- where the money, laws, and power are controlled -- has nothing.**

349 MPs. 67 Senators. 26 data sources. 200-400 pages of parliamentary text per sitting day. No system connects what an MP says in January to how they vote in March. No system tracks which Cabinet Secretary dodges parliamentary summons 8 out of 10 times. No system tells 1.2 million people in Kibera that the health centre promised in 2024 is now 580+ days overdue.

BungePulse fills that gap.

*AI makes it possible. Humans make it trustworthy. Citizens make it powerful.*

---

## Five-Dimensional National Security Framework

Every tab in the dashboard, every WhatsApp alert, every AI pipeline output connects to at least one of these five dimensions. This is how BungePulse organizes accountability -- not as a transparency exercise, but as national security infrastructure.

| Dimension | Threat Without BungePulse | What BungePulse Tracks |
|-----------|--------------------------|----------------------|
| **Political Security** | MP promises anti-corruption legislation in January, quietly votes against it in March. Nobody connects those two moments across 400 pages of Hansard. Eroded trust is how democracies collapse. | Speech-to-vote contradictions detected automatically via semantic matching |
| **Economic Security** | Every ghost project, every diverted budget that goes untracked signals to investors that institutions don't work. Sovereign credibility erodes. | Budget discrepancies, CDF utilization, project completion rates, financial anomalies |
| **Health Security** | The Kibera Health Centre stalled 18 months. 1.2 million people with reduced health access. That's pandemic preparedness failure. | Stalled health facilities, budget utilization gaps, construction timeline tracking |
| **Education Security** | When CBC funding commitments aren't tracked, school infrastructure stalls. Under-educated generations become vulnerable to radicalization. | Education budget votes tracked to actual school construction outcomes |
| **Environmental Security** | Conservation funds stolen, climate adaptation budgets diverted -- these become resource conflicts and displacement. | Parliamentary votes on environmental budgets tracked to implementation |

---

## Constitutional Grounding

Every feature traces to specific articles of the **Constitution of Kenya 2010**. This is structural defense -- if anyone challenges BungePulse's right to exist, the response is: *Article 1* (sovereignty belongs to the people), *Article 35* (access to information), *Article 118* (public participation).

Every constitutional citation in BungePulse -- dashboard, WhatsApp alert, bill detail, MP profile -- becomes a **clickable learning moment** with plain-language summaries at Grade 8 reading level and Kiswahili translations. Most Kenyans have never read their Constitution. BungePulse builds constitutional literacy at scale.

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
| Art. 94-96 | Parliament's role (lawmaking) | Vote and bill tracking |
| Art. 114 | Public finance | Budget and bill pipeline |
| Art. 118 | Public participation | Citizen campaigns, evidence submission |
| Art. 125 | Plenary sittings conducted openly | Sitting outcomes, plenary monitoring |
| Art. 153 | Summoning before Parliament | Summons tracker, ministry grades, proxy detection |
| Art. 201, 202, 217 | Finance, revenue, division of funds | Project budgets, CDF tracking |
| Art. 226 | Accounts and audit | Financial tracking, Auditor-General reports |
| Art. 229 | Removal and accountability of officials | MP performance tracking |

</details>

### How Constitutional Education Appears

Constitutional education is woven into every channel -- not as footnotes, but as civic literacy at scale.

**On the Web Dashboard (tooltip/expandable card):**

```
Article 153 -- Cabinet Secretaries Accountability

Plain language: Cabinet Secretaries must appear before Parliament when
summoned. Parliament has the power to call any CS to explain what their
ministry is doing.

Constitutional text: "A Cabinet Secretary shall attend before a committee
of the National Assembly, or the Senate, when required by the committee..."

Why it matters here: This is why the Summons Tracker exists. When a CS
sends a proxy instead of appearing personally, Article 153 is the standard
being tested.
```

**On WhatsApp (inline education):**

```
Your MP's Vote -- Finance Bill 2026
Hon. Jane Doe voted YES on Feb 10
Alignment Score: 80% (4 of 5 matching votes)

Art. 94 -- Parliament makes laws and controls public funds on your behalf.
This vote decided how your taxes are spent.

Reply LATEST for today's votes
```

**On Campaign Messages / Poll Results:**

```
POLL RESULTS -- Kibera Health Centre
1,247 citizens responded. 78% disagree with the delay.

Art. 43 -- Every person has the right to the highest attainable standard
of health, including healthcare services. A stalled health facility is a
violation of this right.

This result has been shared with the Parliamentary Committee on Health.
```

---

## The Four AI Moments

Four capabilities where no human team could replicate what AI does. Each has a live demo moment designed for judges.

### Moment 1: Scale Detection

Parliament produces 200-400 pages per sitting day. A human team would need **15 full-time researchers** to monitor this daily. BungePulse processes it all before dawn.

> **Demo:** Raw Hansard paragraph on screen. Click "Process." Watch extraction: MP name, topic tags, commitment candidate, confidence score, linked bill, linked vote. **2 seconds.** A human takes 20 minutes per speech segment. There are 300 per sitting day.

**Tech:** Custom spaCy NER model trained on Kenyan parliamentary text. Celery + Redis for automated 6:00 AM daily processing.

### Moment 2: Cross-Source Contradiction Detection

Hansard says 210 voted Yes. Votes & Proceedings says 208. **The 2-vote discrepancy is flagged automatically.** A human would need to compare two PDFs side by side, line by line.

> **Demo:** Verification panel -- Hansard vs V&P, the 2-vote gap flagged in amber. *"This is how we catch data manipulation or OCR errors before they become published misinformation."*

**Five anomaly types detected:**

1. Impossible totals (vote count > 349 MPs)
2. Missing MPs (named in Hansard, absent from roll-call)
3. Mathematical errors (Yes + No + Abstain + Absent != Total)
4. Title mismatches across sources
5. Temporal inconsistencies (commitment date after vote date)

All flagged for mandatory human investigation before publication.

### Moment 3: Commitment-to-Vote Linking

An MP says *"I will fight corruption"* on January 15. On March 8, they vote **NO** on the Anti-Corruption Amendment Bill. 52 days apart. Different documents. Different formatting. The semantic matching engine connects them automatically.

> **Demo:** Evidence tab on bill detail -- the chain: Hansard quote (Jan 15, p.23) > Bill tabled (Feb 1) > Committee Stage (Feb 20) > Vote (Mar 8) > Alignment verdict. *"No human is reading 8 weeks of Hansard to catch that contradiction."*

**Tech:** Sentence embeddings (all-MiniLM-L6-v2) compute similarity between speech text and bill text. Timeline validation ensures commitment date < vote date. Alignment score calculated **deterministically**: `(matching votes / relevant votes) x 100`.

### Moment 4: Pattern Detection Across Time

One CS missing one summons is an incident. The same ministry sending proxies **8 out of 10 times** over 90 days is a pattern of systematic avoidance. BungePulse detects it from Order Paper and Hansard cross-referencing.

> **Demo:** Ministry Responsiveness Index. Point to the lowest-scoring ministry. *"No journalist has the time to manually cross-check 90 days of Order Papers against 90 days of Hansard. AI does."*

---

## Architecture

Dual-service system connected via REST APIs inside Docker.

```
+----------------------------------------------------------------------+
|                         DOCKER ENVIRONMENT                           |
|                                                                      |
|  +----------------------+             +---------------------------+  |
|  |  LARAVEL STACK       |    REST     |  FASTAPI STACK            |  |
|  |  (Steve Maloba)      |    API      |  (Derick Ochieng)         |  |
|  |                      |             |                           |  |
|  |  Laravel 11          <------------>  FastAPI                   |  |
|  |  (Dashboard +        |             |  (NLP API + Admin         |  |
|  |   Auth + Search)     |             |   + WhatsApp Webhook)     |  |
|  |       |              |             |       |                   |  |
|  |       v              |             |       v                   |  |
|  |  MySQL 8.0           |             |  Celery + Redis 7.x       |  |
|  |  (14 canonical       |             |  (6 AM daily pipeline +   |  |
|  |   tables)            |             |   background tasks)       |  |
|  |       |              |   trigger   |       |                   |  |
|  |       v              |             |       v                   |  |
|  |  n8n (Self-          <--------------  Python NLP Engine        |  |
|  |   Hosted)            |             |  spaCy + Transformers     |  |
|  |  (Ingestion +        |             |  (NER + Classification    |  |
|  |   Orchestration)     |             |   + Verification)         |  |
|  |                      |             |       |                   |  |
|  +----------------------+             |       v                   |  |
|                                       |  MariaDB 11.x             |  |
|                                       |  (8 audit/provenance      |  |
|                                       |   tables -- append-only)  |  |
|                                       |       |                   |  |
|                                       |       v                   |  |
|                                       |  Twilio / Meta            |  |
|                                       |  WhatsApp Cloud API       |  |
|                                       +---------------------------+  |
+----------------------------------------------------------------------+
```

### Tech Stack

| Component | Technology | Role | Security Dimension |
|-----------|------------|------|--------------------|
| Dashboard + Auth | Laravel 11 (PHP 8.3) | 10-tab dashboard, authentication, search | All five dimensions |
| Ingestion | n8n (self-hosted) | Source ingestion workflows, scheduling triggers | Scale Detection (Moment 1) |
| Canonical DB | MySQL 8.0 | 14 tables: MPs, bills, votes, alerts, users, campaigns | Data integrity |
| NLP API + Admin | FastAPI (Python 3.11+) | NLP endpoints, admin review, WhatsApp webhook | Moments 1-4 |
| Background Tasks | Celery + Redis 7.x | 6 AM daily pipeline, parallel document processing | Automated monitoring |
| NLP Engine | spaCy + transformers | Parliamentary NER, classification, semantic matching | Entity extraction, linking |
| Audit DB | MariaDB 11.x | 8 tables: immutable logs, SHA-256 hashes, provenance | Tamper-proof records |
| Containers | Docker + Docker Compose | Repeatable setup, isolated services | Operational resilience |

---

## The Daily Pipeline

```
06:00 AM  Ingestion ......... Download + normalize from 26 parliamentary sources
          Archival .......... Store raw documents + SHA-256 content hashes
          NLP ............... Entity extraction + commitment candidate detection
          Linking ........... Semantic similarity: speech > bill > vote chains
          Verification ...... Hansard x V&P x Order Papers cross-check
06:15 AM  Queue ............. Flagged items enter human review queue

07:00 AM  Human Review ...... Approve / block / investigate (immutably logged)
          Every decision: reviewer ID + timestamp + action + rationale + IP hash

09:00 AM  Publishing ........ WhatsApp alerts + dashboard updates go live
          Citizens know before Parliament's morning sitting begins
```

**Golden Rule:** AI processes. Humans approve. Citizens know.

---

## Dashboard Architecture

10 tabs. 10 constitutional mandates. Zero redundancy.

| Tab | National Security Need | Constitutional Anchor |
|-----|----------------------|-----------------------|
| **Overview** | System health + 5-dimension security monitor | Art. 1, 10 |
| **Recent Votes** | How Parliament voted (gender/party breakdowns) | Art. 94-96, 27 |
| **MPs Tracker** | Individual MP accountability + commitment tracking | Art. 1, 75, 229 |
| **Bills Pipeline** | Legislation progress (5-stage visual flow) | Art. 94, 114 |
| **Summons Tracker** | Executive responsiveness + Ministry Grade Cards (A-F) | Art. 153 |
| **Party Positions** | Party discipline index | Art. 91 |
| **Campaigns** | Citizen mobilization + WhatsApp polls | Art. 118 |
| **WhatsApp Bot** | Population-scale information delivery | Art. 35 |
| **Projects** | Budget-to-ground reality (tri-source tracking) | Art. 43, 201, 217 |
| **About** | Methodology transparency + "How AI Works" | Art. 35 |

### Eight Dashboard Components Built for Judges

1. **"Why BungePulse" Welcome Card** -- Democratic early-warning system title, four AI capability bullets, constitutional references. Sets the national security frame before judges click anything.

2. **AI Processing Today Panel** -- Live proof: documents ingested (47), entities extracted (312 MPs, 23 Bills, 8 Votes), commitment candidates found (14), cross-source checks (6 matched, 2 flagged), evidence links (23 chains). Footer: *"AI processes. Humans approve. Citizens know by 7 AM."*

3. **Governance Security Monitor** -- Five traffic-light cards: Political Security (3 contradictions -- Amber), Economic Security (KSh 4.2B flagged -- Red), Health Security (2 stalled facilities -- Amber), Education Security (CBC report 41 days overdue -- Red), Environmental Security (No anomalies -- Green).

4. **AI Analysis Tab (Bill Detail)** -- Entity extraction, commitment detection with confidence score, cross-source verification (Hansard vs V&P vs Order Paper), semantic linking to prior speeches. Constitutional Relevance section shows which articles the bill engages.

5. **AI Commitment Tracker (MP Detail)** -- Promise > evidence > status. Example: *"I will fight corruption"* (Hansard Jan 15 p.23) > Voted YES (Anti-Corruption Bill, V&P Feb 6) > ALIGNED. Alignment Score: 80%. Human reviewer: Approved (R-041).

6. **Pattern Detection Card (Summons Tab)** -- Ministry of Health: CS summoned 4 times, appeared 1 (25%), PS proxy 2 times, no-show 1, questions deferred 3 (oldest 67 days). *"This pattern would take a researcher 40 hours. AI detected it in 8 seconds."*

7. **Persistent Footer Status Bar** -- Every page: `Pipeline healthy | Last sync: Today 6:04 AM | 47 docs processed | 7 items in human review | AI confidence avg: 93%`

8. **"How AI Works" Sub-Tab** -- What AI Does (6 bullets), What AI Does NOT Do (5 bullets), The Pipeline (visual flow), Why This Matters for Security.

### Original Innovations

Features born during development -- not in any original planning document:

**Ministry Grade Cards (A-F)** -- Ministries graded on summons responsiveness. Visually devastating when a ministry scores F.

| Grade | Average Response Time | Response Rate |
|-------|----------------------|---------------|
| A | 0-7 days | 95%+ |
| B | 8-14 days | 85-94% |
| C | 15-30 days | 70-84% |
| D | 31-60 days | 60-69% |
| F | >90 days | Below 60% |

**Proxy Power Map** -- When PS (Parliamentary Affairs) appears in 9 of 12 Health summons, that's not normal delegation -- it's systematic avoidance made visible.

**County Radar** -- Multi-committee geographic clustering. Turkana appeared in 3 committees on the same day (Energy, Lands, Roads). No journalist catches that without AI.

**580+ Day Overdue Counter** -- Kibera Health Centre: KSh 69.5M from 3 sources (National KSh 30M + NG-CDF KSh 20M + World Bank KSh 19.5M), promised within 6 months (Jan 2024), 580+ days overdue. Counter updates daily.

**Population-Weighted Representation** -- An MP vote shows *"representing 120,000 constituents"* not just "1 of 349." An MP absence shows *"120,000 constituents relied on party representation rather than their direct MP."*

### Design System

Dark theme: `#0f172a` base, `#1e293b` surfaces, `#38bdf8` accent. Kenya colors `#1B5E20` (green) and `#B71C1C` (red) used strategically. Information-dense, professional aesthetic -- not flashy, but credible.

---

## NLP Pipeline

| Step | Technology | What It Does | Security Moment |
|------|-----------|-------------|-----------------|
| Entity Extraction | spaCy + custom NER | Extracts MP names, bill titles, committees, counties | Moment 1: Scale |
| Commitment Detection | Rule-based patterns (MVP) | Flags "I commit", "I will ensure", "we shall" + confidence scores | Moment 3: Linking |
| Semantic Matching | sentence-transformers (all-MiniLM-L6-v2) | Speech-to-bill similarity for evidence chains | Moment 3: Linking |
| Verification | Custom Python engine | Hansard x V&P x Order Papers cross-check | Moment 2: Contradiction |
| Pattern Detection | Time-series analysis | 90-day proxy frequency, ministry responsiveness | Moment 4: Patterns |
| Anomaly Detection | Rule-based checks | 5 anomaly types flagged automatically | Moment 2: Contradiction |

**Confidence Gates:** >=95% auto-approve > >=80% human review > >=40% auto-flag for investigation > <40% rejected

> **Honesty note:** MVP uses rule-based commitment detection (~70% recall). Fine-tuned BERT classification is Phase 2. The rule-based version works and is demonstrated live.

---

## WhatsApp Bot

Kiswahili-first. 9 commands. Article 35 (access to information) at population scale -- 29 million potential users.

| Kiswahili | English | Function |
|-----------|---------|----------|
| `ANZA` | `START` | Opt in, store phone + constituency |
| `ACHA` | `STOP` | Opt out, delete all data |
| `MBUNGE WANGU` | `MY MP` | MP profile + voting record (returns **both** constituency MP and County Woman Representative -- Art. 27) |
| `LEO` | `LATEST` | Today's votes + active polls |
| `KURA` | `POLL` | View and respond to active polls |
| `MATOKEO` | `RESULTS` | Poll results by constituency |
| `DATA YANGU` | `DATA` | View all stored user data |
| `FUTA` | `DELETE` | Permanently erase all data |
| `MSAADA` | `HELP` | List all commands |

**Context-aware sessions:** If you just asked about Finance Bill, `KURA` defaults to showing the Finance Bill vote.

**"MY MP" returns both representatives** -- constituency MP *and* County Woman Representative. Kenya has 47 CWRs representing entire counties. Most tracking systems ignore them. BungePulse doesn't -- Article 27 (gender rule) is constitutional, not optional.

### 48-Hour Poll Cycle

Replaces X Spaces. WhatsApp polls produce **structured, measurable, constituency-level citizen voice** shareable with parliamentary committees as evidence.

**Day 1 -- Verification + Poll Launch (Hours 0-24):**

| Time | Action |
|------|--------|
| 9:00 AM | Issue verified (triple-source confidence >=80%) |
| 10:00 AM | Poll question drafted, reviewed for neutrality by admin |
| 12:00 PM | Accountability poll sent via WhatsApp to affected constituencies |
| 3:00 PM | Media backgrounder distributed to journalists/CSOs with verified evidence |
| 6:00 PM | Reminder to non-responders -- poll closes tomorrow 6 PM |

**Day 2 -- Results + Escalation (Hours 24-48):**

| Time | Action |
|------|--------|
| 6:00 PM | Poll closes automatically |
| 7:00 PM | Results aggregated by constituency |
| 8:00 PM | Results broadcast to all participants + media partners |

**Day 3 -- Outcome Tracking (Hours 48+):**

Monitor for institutional response. Create `outcome_event` record if ministry/committee responds. Broadcast success alert if action is taken.

---

## Data Model

### MySQL (Laravel) -- 14 Canonical Tables

```
constituencies  mps  sitting_days  documents  bills_or_motions
vote_events  mp_votes  speech_segments  alerts  whatsapp_users
polls  poll_responses  campaigns  outcome_events
```

### MariaDB (FastAPI) -- 8 Audit/Provenance Tables

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

## What BungePulse Does NOT Do

Boundaries are survival infrastructure. These are non-negotiable.

| BungePulse Never... | Why |
|---------------------|-----|
| Publishes MP phone numbers or says "contact your MP" | Prevents harassment, maintains institutional posture |
| Broadcasts off-site committee venue locations to the public | Physical security risk for officials and witnesses |
| Makes individual predictions ("this MP will vote against...") | Profiling is accusation, not accountability |
| Uses the words "broke promise", "lied", or "corrupt" | Defamation risk -- always "voted differently from stated position" |
| Publishes AI-generated claims without human approval | One hallucination destroys all credibility permanently |
| Shares citizen data with industry clients or anyone else | Privacy is constitutional (Art. 31) and non-negotiable |
| Makes endorsements or rankings during election periods | 90-day pre-election lockdown protocol |

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

*Parliament makes decisions about all of them. We make sure all of them know.*

---

## Prediction Policy

The line between insight and accusation is where BungePulse lives or dies.

### Allowed: System-Level Risk Signals

Historical patterns from 4 years of parliamentary voting data (2022-2026):

1. Bills at Committee Stage with <60% party alignment historically fail at Third Reading 73% of the time
2. Ministries sending proxies >50% in Q1 tend to have highest unanswered question backlogs by Q4
3. Constituencies where CDF utilization drops below 40% in H1 historically don't recover by year-end
4. When a CS promises to table a report "next month" and doesn't -- 78% chance they won't table it at all this session
5. FLLoCA-type devolved projects missing first milestone by 30+ days -- 65% chance of stalling completely

### What a Risk Signal Looks Like in the UI

```
RISK SIGNAL -- Finance Bill 2026
Pattern match detected

This bill has been deferred twice, has 58% party alignment, and faces
3 pending amendments.

Historical pattern: Bills matching this profile pass at Third Reading
only 31% of the time.

This is a statistical pattern, not a prediction about any individual
MP's vote. Sources: 4 years of parliamentary voting data (2022-2026)
```

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
| **Triple-Source Verification** | Every high-stakes claim cross-checked: Hansard x V&P x Order Papers. Two agree, third contradicts = amber flag for human investigation. | Prevents data manipulation becoming published misinformation |
| **Absence as First-Class Data** | Non-participation and proxy substitution are trackable, visible patterns -- not blank cells | Exposes systematic avoidance of parliamentary accountability |
| **Bill Lifecycle Pipeline** | 5-stage visual flow: First Reading > Committee > Second Reading > Third Reading > Assent. Each stage shows who spoke, voted, amended. | Makes legislation a story, not a spreadsheet row |
| **Population-Weighted Votes** | MP absence shows "120,000 constituents relied on party representation" -- not just "1 absent" | Reframes every vote in human terms |
| **Verifiable Hashes** | Every alert carries SHA-256 hash of source documents. Independently verifiable by any journalist, CSO, or citizen. | Tamper-proof publication record |
| **Immutable Audit Trail** | `review_decisions` table: append-only, reviewer ID, timestamp, action, IP hash. No deletion possible. | Every approval traceable forever |
| **Independent Trust Board** (Phase 4) | Non-partisan oversight, quarterly bias audits by constituency/party/coalition | Prevents political capture |

---

## Real Data Integration

Three actual parliamentary committee alerts from **February 12, 2026** replaced all placeholder content. Judges specifically want real data, not mock data.

<details>
<summary><strong>February 12, 2026 -- Three Committee Alerts + Seven Insights</strong></summary>
<br>

**Alert 1: Joint Committee on Energy** (Political + Economic + Environmental Security)
- Venue: Hilton Garden Inn, Machakos County (off-site -- flagged)
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

1. **Joint committees exist** -- Need "Joint" badge when both chambers sit together. Signals high national importance.
2. **County governors appear before Senate** -- Summons Tracker must expand beyond CS/PS. Entity scope change.
3. **Private sector actors appear** -- Gulf Energy before a joint committee proves private entities are part of the accountability ecosystem.
4. **Turkana in ALL THREE committees** -- County Radar justified instantly. One county, three committees, same day.
5. **Committees meet outside Parliament** -- Hilton Garden Inn, Machakos is nowhere near Bunge Tower. Venue tracking with off-site flags required.
6. **FLLoCA is real devolved funds** -- Perfect demo data for Projects view. Budget-to-ground tracking.
7. **Three new gap brief items** -- Joint badge (1.3), County Radar (4.4), Expanded entity types (4.5).

</details>

---

## Who Uses This

The same data that empowers citizens is valuable to institutions that need parliamentary intelligence. *The intelligence that protects democracy also funds it.*

| Tier | Audience | What They Get | Cost |
|------|----------|---------------|------|
| **Citizen** | 29M Kenyans | WhatsApp bot (9 commands), dashboard (public view), basic alerts | Free forever (Art. 35) |
| **Newsroom** | Media houses | Journalist API, bulk exports, webhook alerts, embeddable widgets, weekly briefing PDF | KSh 50K/year |
| **CSO** | Civil society | Thematic dashboards, campaign tools, outcome evidence reports, donor-ready impact metrics | KSh 30K/year |
| **Industry** | Private sector | Sector-specific legislative tracking, regulatory pipeline, risk signals, custom API | KSh 150K/year |
| **Research** | Academia | Historical data access, bulk datasets, custom queries, longitudinal analysis | By arrangement |

**9 industry buyer categories:** Oil/Gas/Extractives, Banking/Financial Services, Telecommunications, Real Estate/Infrastructure, International Development/Donors, Law Firms/Lobbyists, Independent Commissions (EACC, Auditor-General), Trade Unions/Professional Bodies, Foreign Diplomatic Missions.

**Industry access safety principle:** Industries receive the same PUBLIC parliamentary data that citizens see. They get it faster, filtered, and analysed -- that's the paid value. They do NOT receive citizen data, predictive claims about individual MPs, draft alerts before human review, or ability to suppress published data.

---

## Trust, Safety & Legal

### Legal Disclaimer

This project and its outputs are provided "as is" without warranty of any kind. Nothing in this repository constitutes legal advice. All data sourced from official parliamentary records published by the Parliament of Kenya. Use at your own risk.

### Core Publication Rules

| Rule | Implementation |
|------|---------------|
| **Human-in-the-loop** | Zero high-stakes claims publish without explicit human approval |
| **Defamation-safe language** | "Voted differently from stated position" -- never "broke promise", "lied", "corrupt" |
| **Triple-source verification** | Hansard x V&P x Order Papers. Confidence gates: 95/80/40 |
| **Non-partisan** | Same data, same methodology, same scrutiny -- every MP, every party, every region |
| **No MP contact info** | System never publishes MP phone numbers or instructs citizens to "contact your MP" |

### Electoral Integrity Policy

90 days before a general election: publish only verified factual data. No new campaigns, no "worst MP" rankings, no targeted constituency pushes, no manipulative call-to-action targeting.

### Privacy & Data Protection (KDPA-Aligned)

- **Collected:** Phone number + optional constituency + language preference. Nothing else.
- **Never collected:** Names, national IDs, locations, political affiliations.
- **User control:** `FUTA`/`DELETE` erases everything. `DATA YANGU`/`DATA` shows what's stored.
- **Retention:** Stale records auto-purge after defined retention windows.

### Whistleblower Protection

Encrypted tip channel -- completely separate from public WhatsApp. Source identity never published. Tips verified through standard pipeline before any action.

### Venue Safety

Off-site committee meetings: public channels show committee name, date, agenda, summoned parties, and "off-site" flag only. Exact hotel/room details restricted to accredited media. Constitutional basis: Art. 31 (privacy) balanced against Art. 35 (access to information).

---

## Existential Risks & Mitigations

| Risk | Mitigation |
|------|-----------|
| Parliament turns off the data tap | SHA-256 archive of all source documents, data resilience plan, degrade gracefully with "Source delayed" status |
| Legal exposure | Factual framing only ("voted differently from stated position"), pro-bono legal partnerships (Katiba Institute, ARTICLE 19, ICJ-Kenya) |
| Personal targeting of team | Register as organization, multiple admins, team email, no single point of failure |
| Electoral weaponization | 90-day pre-election lockdown protocol |
| AI hype vs reality gap | Honest positioning: rule-based MVP (~70% recall), BERT is Phase 2. Show the working demo. |
| It works and nobody cares | Lead with Kibera (580+ days), prove outcomes not just transparency |
| Zero real user testing | 15 structured interviews planned post-hackathon before production code |

> *What keeps us up at night? That it works well enough to threaten powerful people, but isn't yet resilient enough to survive their response. That's why we built for verification, auditability, and institutional trust from day one -- not as features, but as survival infrastructure.*

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
|-- README.md
|-- ARCHITECTURE.md
|-- LICENSE                          # AGPL-3.0
|-- CONSTITUTIONAL_EDUCATION.md      # 19-article education library
|-- docker-compose.yml
|-- .env.example
|
|-- laravel/                         # Steve Maloba
|   |-- app/
|   |   |-- Http/Controllers/
|   |   |-- Models/
|   |   +-- Services/
|   |-- database/migrations/
|   |-- resources/views/             # 10-tab dashboard (Blade templates)
|   |-- routes/
|   +-- Dockerfile
|
|-- fastapi/                         # Derick Ochieng
|   |-- app/
|   |   |-- api/
|   |   |-- models/
|   |   |-- nlp/
|   |   |   |-- entity_extraction.py
|   |   |   |-- commitment_detection.py
|   |   |   |-- semantic_matching.py
|   |   |   |-- verification_engine.py
|   |   |   +-- anomaly_detection.py
|   |   |-- celery_tasks.py
|   |   +-- whatsapp/
|   |-- alembic/
|   +-- Dockerfile
|
|-- n8n/
|   +-- workflows/                   # Ingestion + orchestration flows
|
|-- docs/
|   |-- API.md
|   |-- DEPLOYMENT.md
|   |-- LEGAL.md
|   |-- PREDICTION_POLICY.md
|   +-- ELECTORAL_INTEGRITY.md
|
+-- demo/
    |-- screenshots/
    |-- sample-data/                 # Real Feb 12, 2026 committee data
    +-- video/
```

---

## Roadmap

### 11 Milestones -- 39 Days -- Feb 16 to Mar 26, 2026

| # | Milestone | Dates | Priority | Owner |
|---|-----------|-------|----------|-------|
| 1 | Infrastructure & Scaffolding | Feb 16-18 | CRITICAL | All |
| 2 | Data Ingestion & Document Processing | Feb 18-21 | CRITICAL | Steve + Derick |
| 3 | NLP Engine -- Entity Extraction & Commitment Detection | Feb 18-22 | CRITICAL | Derick |
| 4 | Cross-Source Verification & Anomaly Detection | Feb 21-24 | HIGH | Derick |
| 5 | Admin Review Console (Human-in-the-Loop) | Feb 23-25 | HIGH | Steve + Gerald |
| 6 | Dashboard -- 10-Tab Navigation & Core Components | Feb 26-Mar 5 | CRITICAL | Steve + Gerald |
| 7 | Pattern Detection & Ministry Responsiveness | Mar 6-9 | HIGH | Derick |
| 8 | WhatsApp Bot -- 9 Kiswahili Commands & Poll System | Mar 10-14 | HIGH | Derick + Gerald |
| 9 | Constitutional Education Layer (19 Articles) | Mar 15-16 | MEDIUM | Gerald + Steve |
| 10 | Real Data Integration & Kibera Project | Mar 17-20 | CRITICAL | All |
| 11 | Demo Video, Documentation & Submission | Mar 21-26 | CRITICAL | All |

Milestones 2 & 3 run in parallel (Steve handles ingestion while Derick builds NLP). Same for M4 & M5.

**Deadline: March 26, 2026** -- Demo video + working system + technical documentation.

---

## Gap Brief -- 21 Items Across 6 Themes

<details>
<summary><strong>View Complete Gap Brief</strong></summary>
<br>

**Theme 1: Bicameral Parliament & Committees**
- 1.1 Add Senate (67 Senators, Senate votes, committee summons) -- judges will notice if absent
- 1.2 Committee-level tracking (names, members, schedules, reports as UI components)
- 1.3 Joint committee badge (both chambers sitting together -- strong differentiator)

**Theme 2: Citizen Experience & Inclusion**
- 2.1 Citizen feedback loop ("What did this alert make you do?")
- 2.2 SMS fallback for non-smartphone users
- 2.3 Multilingual (Kiswahili minimum; Turkana/Luo/Kikuyu for county alerts -- roadmap)
- 2.4 WCAG 2.1 AA accessibility (screen readers, high contrast, voice notes)

**Theme 3: Devolution & County Governance**
- 3.1 County-level data views (filter everything by constituency/county)
- 3.2 County budgets (revenue division, conditional grants, CDF tracking)
- 3.3 Projects view (FLLoCA as demo data: allocation > debate > vote > implementation)

**Theme 4: Power Mapping & Executive Accountability**
- 4.1 Summons Tracker -- CS/PS attendance vs expectation (MVP killer feature)
- 4.2 Proxy detection -- who speaks on behalf of whom, how often
- 4.3 Unanswered questions tracker -- deferred questions by ministry with aging
- 4.4 County Radar -- multi-committee geographic clustering (Turkana 3 committees same day)
- 4.5 Expanded entity types -- Governors, statutory bodies, private sector in Summons

**Theme 5: Data Integrity & Verification**
- 5.1 Verification UI -- triple-source comparison shown visually
- 5.2 Immutable audit trail -- every decision logged, SHA-256 hashed, tamper-proof
- 5.3 Data source health dashboard -- uptime, freshness, last sync per source

**Theme 6: Sustainability & Safety**
- 6.1 Revenue model -- citizen access free forever; paid newsroom/CSO/industry tiers
- 6.2 Electoral integrity policy -- 90-day pre-election protocol
- 6.3 Legal shield -- disclaimers, factual framing, pro-bono legal partnership
- 6.4 Venue disclosure policy -- tiered by audience for physical safety

</details>

---

## Philosophical Foundations

Two frameworks that shaped every design decision:

**Dr. David Dixon's MIT Framework -- AI as Teammate** (NIRU AI Symposium, January 2026): AI accelerates human capability 100x faster than manual methods, but humans retain final authority over all high-stakes outputs that could impact institutional stability, political tensions, or citizen mobilization. This produced BungePulse's Golden Rule: AI flags and drafts. Humans approve all high-stakes outputs. AI is the engine. Humans are the steering wheel and the brakes.

**Lorna Okola's Three Pillars -- Google DeepMind Africa:**
- **Stay Curious** -- Process 400 pages daily because patterns hide in Hansard
- **Build With Empathy** -- WhatsApp-first because that's where 29M Kenyans are, not Silicon Valley. Build for your mothers, aunties, fathers -- not for tech conferences.
- **Turn Constraints Into Advantages** -- Kenya's constraints are prompt designs. The zero-cost stack isn't a limitation -- it's what makes the system replicable by any country at zero cost.

---

## Licensing

**GNU Affero General Public License v3.0 (AGPL-3.0)**

BungePulse is a network service. The AGPL ensures:
- Anyone can use, modify, and distribute the source code
- Modified versions run as public services must share source code
- National security infrastructure stays open -- no proprietary parliamentary trackers from this codebase

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
| **Dev A -- Laravel** | Steve Maloba | Laravel 11 dashboard, n8n orchestration, MySQL, Meilisearch |
| **Dev B -- FastAPI** | Derick Ochieng | FastAPI, Celery, spaCy, MariaDB, WhatsApp API, NLP pipeline |

---

<div align="center">

**NIRU AI Hackathon 2026**

*AI processes. Humans approve. Citizens know.*

*Parliament makes decisions about all of them. We make sure all of them know.*

Built in Nairobi, Kenya

</div>
