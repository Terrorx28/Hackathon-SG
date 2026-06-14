# SentinelIQ

### AI-Powered Insider Threat Intelligence & Data Exfiltration Defense Platform

> *Detect the breach that comes from inside. SentinelIQ turns raw access logs into ranked, explainable, board-ready threat intelligence — in real time.*

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [The Problem We Solve](#2-the-problem-we-solve)
3. [The Solution](#3-the-solution)
4. [Product Tour — What You Actually Get](#4-product-tour--what-you-actually-get)
5. [How It Works — The Intelligence Engine](#5-how-it-works--the-intelligence-engine)
6. [Risk Scoring Model](#6-risk-scoring-model)
7. [The AI Analyst](#7-the-ai-analyst)
8. [Security & Privacy by Design](#8-security--privacy-by-design)
9. [Proven Performance](#9-proven-performance)
10. [System Architecture](#10-system-architecture)
11. [Technology Stack](#11-technology-stack)
12. [Data Model](#12-data-model)
13. [Backend API Reference](#13-backend-api-reference)
14. [Getting Started](#14-getting-started)
15. [Project Structure](#15-project-structure)
16. [Roadmap](#16-roadmap)
17. [Glossary](#17-glossary)

---

## 1. Executive Summary

**SentinelIQ** is an insider-threat detection and investigation platform that watches *how your own people use your data* and flags the moments that matter — a finance analyst exporting 50,000 rows from the customer vault at 3 AM, a stale admin account suddenly reaching into systems it has never touched, sensitive records quietly routed to a personal email address.

Traditional security tools are built to keep outsiders out. **But the most expensive breaches come from the inside** — trusted users, valid credentials, normal-looking sessions. SentinelIQ closes that gap by combining:

- **Unsupervised machine learning** (Isolation Forest) that learns each organization's "normal" and surfaces statistical anomalies — no labeled attack data required.
- **A transparent, explainable risk score (0–100)** that fuses ML anomaly signals with behavioral context: *where* data is going, *whether* it's the first time a user touched a resource, *when* it happened, and *how much* data moved.
- **An AI Analyst** that lets a security team interrogate the entire dataset in plain English and instantly generate CISO briefs, forensic incident files, and GDPR/SOX/NIST compliance reports.

The result is a single pane of glass that takes a security analyst from **"something feels wrong"** to **"here is exactly who, what, when, where, and what to do about it"** — in seconds, with evidence attached.

**At a glance (current demo dataset):**

| Metric | Value |
|---|---|
| Access events analyzed | **1,200** |
| Unique users monitored | **100** |
| Protected resources | **10** |
| Departments covered | **12** |
| Detection precision | **87.5%** |
| Detection recall | **75.9%** |
| F1 Score | **81.3%** |

---

## 2. The Problem We Solve

Insider threats are the blind spot of modern security:

- **They use legitimate access.** No firewall or antivirus fires when an authorized user reads, exports, or emails data they technically have permission to touch.
- **They are rare and varied.** You can't write a static rule for every malicious pattern, and you usually have *no labeled examples* of past insider attacks to train on.
- **They hide in volume.** A SOC analyst drowning in thousands of daily access logs cannot manually spot the one export that signals data theft.
- **They carry massive cost and compliance exposure.** A single exfiltration event from a system like an HRIS or customer vault can trigger GDPR breach reporting, SOX control failures, lawsuits, and reputational damage.

The market need is clear: **a way to rank the riskiest human behavior, explain *why* it's risky, and prove it to auditors — without needing a pre-existing catalog of attacks.**

---

## 3. The Solution

SentinelIQ is built on three pillars:

### Pillar 1 — Detect (Machine Learning)
An **Isolation Forest** model learns the multi-dimensional shape of normal access behavior across nine engineered features. Because it's *unsupervised*, it needs no labeled attacks — it simply isolates the events that don't fit, making it ideal for catching novel insider behavior.

### Pillar 2 — Contextualize (Explainable Risk Scoring)
A raw anomaly score isn't actionable on its own. SentinelIQ layers **human-meaningful behavioral signals** on top:
- **Destination awareness** — data headed to a personal email or USB drive is far riskier than data staying on a local machine.
- **First-time resource access** — a user reaching for data they've *never* touched before is a classic precursor to exfiltration.
- **Temporal and volume context** — off-hours activity and abnormal data volumes escalate risk.

Every score is **decomposable and explainable** — analysts and auditors see exactly which factors contributed.

### Pillar 3 — Investigate (AI Analyst)
A built-in **conversational AI analyst** lets the team query the data in natural language ("Who is the most dangerous user?"), and auto-generates executive summaries, forensic incident reports, and compliance documentation — turning hours of manual triage into seconds.

---

## 4. Product Tour — What You Actually Get

SentinelIQ ships as a polished, dark-themed security operations console with **nine dedicated workspaces**:

### Overview Dashboard
The command center. At-a-glance counts of **critical threats, high-risk events, flagged users, and total events**, plus a live banner showing the ML model's evaluated **precision / recall / F1** against ground truth. Includes threat-activity-over-time charts, severity distribution, action breakdowns, and a ranked list of top alerts — each clickable straight into a full incident view.

### Active Alerts
A searchable, filterable triage queue of every anomalous access. Filter by **severity, action type, and time classification**, search by user or resource, and paginate through the full event stream. This is where an analyst lives during a shift.

### Event Timeline
A chronological, date-grouped stream of access events with two analytics panels:
- **Risk Concentration by Hour** — a composed chart overlaying event volume against *average risk*, revealing that off-hours often carry disproportionate risk even at low volume.
- **Most Targeted Resources** — a ranked, filter-aware view of which resources draw the most activity, with average risk and alert counts.

Selecting any incident opens an **Investigation Timeline**: an ordered, forensic reconstruction of that user's activity (login → access → download → exfiltration → alert), showing timestamp, user, resource, action, destination, and risk score at each step.

### Case Files
Automatically promoted profiles of the highest-risk users, classified by anomaly scoring — the people a team should be watching right now. One click hands a case directly to the AI Analyst for deep investigation.

### User Profiles
A searchable directory of all 100 monitored users with department filtering, privilege level, activity status, and per-user risk rollups.

### Access Heatmap
An **Hour × Day Risk Matrix** with a mode toggle:
- **Avg Risk** — cell color encodes average risk severity, brightness encodes volume, so genuine high-risk hotspots pop instead of a uniform wall of color.
- **Alerts** — intensity by number of HIGH/CRITICAL alerts.
- **Volume** — raw access baseline.

Topped with **"Riskiest Window"** and **"Off-Hours Alerts"** insight cards that quantify how much risk concentrates outside business hours.

### Analytics
Feature-level analysis of access patterns — business-hours vs. off-hours splits, high-sensitivity access counts, total data volume moved — plus a **DLP (Data Loss Prevention) policy panel** that models blocking sensitive exports, off-hours exports, and stale-account exports.

### AI Analyst
The conversational brain (see [Section 7](#7-the-ai-analyst)).

### Reports
One-click generation of three board-ready document types:
- **Executive Summary** — CISO-ready threat posture.
- **Forensic Incident Reports** — detailed, evidence-backed write-ups.
- **Compliance Reports** — mapped to **GDPR Article 32, SOX 302, and NIST IR-4**.

---

## 5. How It Works — The Intelligence Engine

### Step 1 — Feature Engineering
Each raw access event is converted into a **9-dimensional feature vector** that captures the behavioral fingerprint of the action:

| Feature | Source | Why it matters |
|---|---|---|
| `hour_of_day` | timestamp | Unusual hours correlate with malicious intent |
| `sensitivity_score` | resource sensitivity | High-sensitivity data raises stakes |
| `volume_deviation` | rowcount vs. user average | Sudden large pulls signal exfiltration |
| `rowcount` | event data | Absolute volume of data touched |
| `privilege_score` | privilege level | admin=3, user=1, guest=0 |
| `days_inactive` | user profile | Dormant accounts springing to life are suspicious |
| `time_class_score` | time classification | business=0 → night=2 → unusual=3 |
| `action_score` | action type | export/admin=3, query=2, login=0 |
| `ml_anomaly_score` | pre-computed signal | Prior model intelligence |

Features are standardized with a fitted `StandardScaler` so no single dimension dominates.

### Step 2 — Anomaly Detection
An **Isolation Forest** (100 estimators, contamination auto-estimated from the data, fixed random seed for reproducibility) is trained on the scaled features. The algorithm works by randomly partitioning the feature space — anomalies, being "few and different," get isolated in far fewer splits than normal points. This makes it fast, scalable, and effective at catching the rare insider events that rule-based systems miss.

### Step 3 — Score Normalization
The raw Isolation Forest anomaly score is converted to an intuitive **0–100 risk scale** using z-score normalization against baseline statistics learned at training time:

$$\text{risk} = \text{clip}\Big(50 + 15 \cdot \frac{s - \mu}{\sigma + \epsilon},\ 0,\ 100\Big)$$

where $$s$$ is the event's anomaly score and $$\mu, \sigma$$ are the training-set mean and standard deviation.

### Step 4 — Behavioral Risk Layering
Two explainable behavioral signals are blended on top of the ML base score (see [Section 6](#6-risk-scoring-model)).

### Step 5 — Investigation & Visualization
Scored events flow into the dashboards, the AI Analyst, and the report generators — each event carrying its full evidence trail so any score can be traced back to its cause.

---

## 6. Risk Scoring Model

SentinelIQ's headline risk score is deliberately **transparent and additive** — the ML model provides the dominant signal, and human-meaningful context escalates it. Critically, **the behavioral layers never alter the underlying model's behavior**; they augment its output.

```
final_risk = clip( base_ML_risk  +  destination_risk  +  first_time_access_risk , 0, 100 )
```

### Destination-Aware Risk
*Where* data goes is one of the strongest exfiltration signals. SentinelIQ normalizes any destination string (with a wide alias map) into a canonical type and adds a calibrated contribution:

| Destination | Risk Contribution |
|---|---|
| Local machine | +2 |
| Corporate email | +5 |
| Internal fileshare | +8 |
| Cloud storage | +15 |
| External FTP | +18 |
| USB drive | +20 |
| **Personal email** | **+25** |

Unknown or missing destinations default safely to **local machine** (lowest risk), so the system never over-escalates on incomplete data.

### First-Time Resource Access
A user reaching for data they have **never accessed before** is a hallmark of reconnaissance and staging. SentinelIQ maintains a **historical access index per user**, built entirely from existing data (no database required), and flags the feature `is_first_time_resource_access`. A first-time access adds **+12** to the risk score and is surfaced everywhere — API responses, dashboard evidence, and investigation summaries.

### Severity Bands

| Risk Score | Band | Meaning |
|---|---|---|
| 0–20 | **Low** | Normal behavior |
| 21–50 | **Medium** | Unusual but within bounds |
| 51–75 | **High** | Significant deviation — investigate |
| 76–100 | **Critical** | Major anomaly — immediate action |

Because the score is additive, every number on screen is **fully explainable**: an analyst (or auditor) can see that an 82 came from, say, a base ML risk of 65, +12 for first-time access, and +5 for a corporate-email destination.

---

## 7. The AI Analyst

The AI Analyst transforms SentinelIQ from a dashboard into an **investigation partner**. Ask it anything about the data in natural language and get structured, evidence-backed answers.

### Dual-Brain Design
- **Built-in reasoning engine (always available):** A sophisticated rule-based analytics engine answers questions instantly with no external dependency — top threats, most dangerous users, exfiltration risk, department breakdowns, compliance exposure, and more. The product is **fully functional with zero API keys**.
- **Optional LLM augmentation:** Connect a large language model for richer natural-language summaries. SentinelIQ supports multiple providers out of the box:
  - **Server-side key (recommended)** — the token lives in the `HUGGINGFACE_ACCESS_TOKEN` environment variable on the server and is *never* exposed to the browser.
  - **Hugging Face, OpenAI, Groq, or any OpenAI-compatible custom endpoint** — configurable directly in the UI.
- Responses **stream token-by-token** for a responsive, modern chat experience.

### Guided Investigation
Curated quick-prompt categories (Critical, Compliance, and more) give analysts one-click access to high-value questions like *"Top 5 critical threats,"* *"Most dangerous user,"* *"GDPR exposure,"* and *"SOX controls check."*

### Auto-Generated Intelligence Products
The analyst can produce, on demand:
- **CISO Executive Brief** — threat summary, top incidents, compliance exposure, remediation plan.
- **Forensic Incident Reports** — full who/what/when/where/why with blast-radius analysis.
- **Compliance Reports** — GDPR Art. 32, SOX 302, NIST IR-4 mappings.

---

## 8. Security & Privacy by Design

Security software must hold itself to the highest standard. SentinelIQ does:

- **Built-in DLP redaction.** Before *any* text is sent to a third-party LLM, an outbound Data Loss Prevention scanner automatically detects and redacts sensitive data — **emails, SSNs, credit card numbers, phone numbers, AWS keys, API tokens, JWTs, and private IPs** — preventing accidental data exfiltration to external AI providers.
- **Server-side secret management.** The recommended LLM mode keeps API tokens entirely server-side via environment variables. Keys are never embedded in client code or transmitted to the browser.
- **No mandatory cloud dependency.** The core detection, scoring, and analytics run locally. No data has to leave the environment for the product to deliver its primary value.
- **Reproducible, auditable ML.** Fixed random seeds and persisted model statistics make every score reproducible and defensible.
- **Explainable decisions.** Every risk score decomposes into named, inspectable factors — essential for audit, compliance, and analyst trust.

---

## 9. Proven Performance

SentinelIQ's detection model is evaluated against ground-truth anomaly labels, not just asserted:

| Metric | Result | Target | Status |
|---|---|---|---|
| **Precision** | **87.5%** | > 75% | ✅ Exceeds |
| **Recall** | **75.9%** | > 70% | ✅ Exceeds |
| **F1 Score** | **81.3%** | > 0.72 | ✅ Exceeds |

**Confusion matrix (1,200 events, 552 ground-truth anomalies):**

| | Predicted Positive | Predicted Negative |
|---|---|---|
| **Actual Positive** | TP = 419 | FN = 133 |
| **Actual Negative** | FP = 60 | — |

- **High precision (87.5%)** means when SentinelIQ raises an alert, it's right ~7 out of 8 times — minimizing the alert fatigue that plagues most security tools.
- **Strong recall (75.9%)** means it catches roughly three-quarters of true anomalies while remaining unsupervised.

---

## 10. System Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                          BROWSER (Client)                          │
│                                                                    │
│   React + TypeScript SPA (Vite)                                    │
│   ┌────────────┬───────────┬───────────┬────────────┐             │
│   │  Overview  │  Alerts   │ Timeline  │  Heatmap   │  …9 views   │
│   └────────────┴───────────┴───────────┴────────────┘             │
│   • In-browser data pipeline (feature derivation, risk layering)   │
│   • Recharts visualizations                                        │
│   • AI Analyst (rule engine + streaming LLM client)                │
│   • DLP redaction (pre-send)                                       │
└───────────────┬───────────────────────────────┬──────────────────┘
                │                                 │
        (dev proxy /api/llm/chat)        (optional direct)
                │                                 │
                ▼                                 ▼
┌───────────────────────────┐         ┌────────────────────────────┐
│   FLASK API (Python)       │         │   LLM PROVIDERS             │
│                            │         │   • Hugging Face            │
│   • /health  /score        │  ◀────▶ │   • OpenAI                  │
│   • /batch-score           │         │   • Groq / custom           │
│   • /investigate           │         └────────────────────────────┘
│   • /model-stats           │
│   • /llm/chat (token-safe) │
│                            │
│   ┌──────────────────────┐ │
│   │  Isolation Forest     │ │
│   │  + StandardScaler     │ │   ◀── trained by train_model.py
│   │  + destination.py     │ │
│   │  + history.py         │ │
│   │  + investigate.py     │ │
│   └──────────────────────┘ │
└───────────────────────────┘
```

**Two deployment modes:**
1. **Static frontend (zero-backend demo):** The React app ships with a pre-scored dataset and runs the full risk-layering pipeline *in the browser* — perfect for instant demos and static hosting (Vercel, GitHub Pages).
2. **Full-stack (live ML):** The Flask API serves live Isolation Forest scoring and token-safe LLM investigations for production-style operation.

---

## 11. Technology Stack

**Frontend**
- React 18 + TypeScript
- Vite 6 (build tool & dev server, with a custom server-side LLM proxy plugin)
- Recharts (data visualization)
- Radix UI + Material UI icon set, Tailwind CSS v4
- Streaming chat client (Server-Sent Events)

**Backend**
- Python 3.9+
- scikit-learn (Isolation Forest, StandardScaler)
- Flask + Flask-CORS
- pandas / numpy
- Hugging Face Inference API (LLM), OpenAI-compatible fallback

**Machine Learning**
- Unsupervised anomaly detection (Isolation Forest, 100 estimators)
- 9-feature engineered vector, standardized
- Z-score risk normalization to 0–100
- Additive, explainable behavioral risk layers

---

## 12. Data Model

Each access event is a rich, fully-attributed record. Key fields:

| Field | Description |
|---|---|
| `user_id`, `username`, `email` | User identity |
| `department`, `job_title`, `privilege_level` | Organizational context |
| `systems_access` | Approved systems for the user |
| `timestamp`, `time_classification` | When, and its risk class (business/off-hours/night/unusual) |
| `action` | login, file_access, sql_query, api_call, admin_operation, export_data |
| `resource`, `resource_sensitivity` | What was accessed and how sensitive |
| `status`, `source_ip` | Outcome and origin |
| `rowcount`, `user_avg_rowcount`, `deviation_from_user_avg_rowcount` | Data volume and deviation |
| `days_inactive`, `is_active`, `last_login`, `hire_date` | Account lifecycle signals |
| `ml_anomaly_score`, `rule_score`, `predicted_anomaly` | Detection signals |
| `risk_score`, `severity` | Final scored output |
| `rules_triggered`, `explanation` | Human-readable evidence |

**Dataset coverage:** 1,200 events · 100 users · 10 resources (PROD_DB, SIEM, GL_System, File_Share, Admin_Console, Data_Lake, HRIS, Email_Archive, Customer_Vault, BI_Tool) · 12 departments · 6 action types.

---

## 13. Backend API Reference

Base URL: `http://localhost:5000`

### `GET /health`
Health check. Returns model load status and baseline statistics.

### `POST /score`
Score a single access event. Returns the blended risk score plus its full decomposition:
```json
{
  "risk_score": 82,
  "base_risk_score": 65,
  "destination_type": "PERSONAL_EMAIL",
  "destination_score": 25,
  "is_first_time_resource_access": true,
  "first_time_score": 12,
  "anomaly_detected": true,
  "anomaly_score": -0.62,
  "investigation": "[HIGH] - zainab.jo export_data with first-time access to Customer_Vault; accessed high-sensitivity Customer_Vault; data routed to personal email (destination risk +25). Schedule investigation within 24 hours.",
  "user_id": "USR00057",
  "username": "zainab.jo",
  "resource": "Customer_Vault"
}
```

### `POST /batch-score`
Score many events at once. Body: `{ "events": [ ... ] }`. Returns an array of scored results.

### `POST /investigate`
Generate an LLM (or rule-based fallback) investigation summary for an event without scoring it.

### `GET /model-stats`
Returns baseline statistics, the full feature list, the destination risk map, and the first-time-access risk constant.

### `POST /llm/chat`
Token-safe server-side LLM proxy. Reads `HUGGINGFACE_ACCESS_TOKEN` from the server environment, supports streaming (Server-Sent Events), and never exposes the key to the browser.

---

## 14. Getting Started

### Option 1 — One-Click Launcher (recommended for demos)
```bash
python launcher.py
```
Trains the model, starts the Flask API, launches the Vite dev server, and opens the dashboard automatically.

### Option 2 — Manual Setup

**Backend (Terminal 1):**
```bash
cd backend
python -m venv venv
source venv/bin/activate        # Windows: .\venv\Scripts\activate
pip install -r requirements.txt
python train_model.py           # Train the Isolation Forest (~seconds)
python app.py                   # Flask API on http://localhost:5000
```

**Frontend (Terminal 2):**
```bash
npm install
npm run dev                     # Vite on http://localhost:5173
```

### Optional — Enable LLM Investigations
Set a Hugging Face token server-side (kept out of the browser):
```bash
export HUGGINGFACE_ACCESS_TOKEN=hf_your_token_here
```
Or configure Hugging Face / OpenAI / Groq / a custom endpoint directly in the AI Analyst UI. **Without any key, the built-in rule-based analyst remains fully functional.**

### Production Build
```bash
npm run build                   # Outputs static assets to dist/
```
Deploy `dist/` to any static host; run the Flask API alongside for live ML scoring.

---

## 15. Project Structure

```
.
├── src/
│   ├── app/
│   │   ├── App.tsx                  # Main SPA: data pipeline + 9 dashboard views
│   │   └── components/
│   │       ├── AIAnalystPage.tsx    # AI Analyst: rule engine, LLM client, DLP
│   │       └── ui/                  # Reusable UI component library
│   ├── imports/
│   │   ├── anomaly_predictions.json # Scored access dataset (1,200 events)
│   │   └── evaluation_metrics.json  # Model evaluation results
│   └── styles/                      # Theming and global styles
│
├── backend/
│   ├── train_model.py               # Isolation Forest training pipeline
│   ├── app.py                       # Flask API server
│   ├── investigate.py               # LLM-powered investigation generator
│   ├── destination.py               # Destination-aware risk scoring
│   ├── history.py                   # First-time resource access detection
│   ├── models/                      # Persisted model, scaler, and stats
│   └── requirements.txt
│
├── launcher.py                      # One-click full-stack startup
├── vite.config.ts                   # Vite config + server-side LLM proxy
├── DOCUMENTATION.md                 # This document
└── README.md
```

---

## 16. Roadmap

SentinelIQ is architected to grow from hackathon prototype to enterprise platform:

- **Live data connectors** — stream from SIEMs, cloud audit logs (AWS CloudTrail, GCP, Azure), and identity providers.
- **Persistent case management** — assign, annotate, and track investigations to resolution.
- **Automated response** — auto-suspend access, quarantine sessions, and open tickets on critical detections.
- **Peer-group analytics** — compare each user against their department/role baseline for sharper anomaly context.
- **Sequence modeling** — detect multi-step attack chains (recon → staging → exfiltration) across sessions.
- **Role-based access control & audit logging** for the console itself.
- **Multi-tenant SaaS deployment** with per-organization model training.

---

## 17. Glossary

- **Insider threat** — a security risk originating from people with legitimate access (employees, contractors, partners).
- **Isolation Forest** — an unsupervised ML algorithm that detects anomalies by how easily a point can be isolated from the rest of the data.
- **Anomaly score** — the raw model output indicating how unusual an event is.
- **Risk score** — SentinelIQ's normalized, context-enriched 0–100 measure of how concerning an event is.
- **Exfiltration** — the unauthorized transfer of data out of an organization.
- **DLP (Data Loss Prevention)** — controls that detect and block sensitive data from leaving a trusted boundary.
- **Precision** — of the events flagged as threats, the fraction that truly are.
- **Recall** — of all true threats, the fraction the system catches.
- **F1 Score** — the harmonic mean of precision and recall.
- **GDPR Art. 32 / SOX 302 / NIST IR-4** — data-protection, financial-controls, and incident-response compliance frameworks SentinelIQ reports against.

---

*SentinelIQ — see the threat before it leaves the building.*
