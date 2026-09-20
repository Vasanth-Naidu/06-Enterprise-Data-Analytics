# Case Study: iTrack — Near Real-Time Operational Health & Productivity Analytics Suite

## Executive Overview:
* **Enterprise Context:** Enterprise Financial & Operations Technology (Cross-Company Deployment)
* **Role:** Lead Data Analytics Architect & BI Engineering Lead
* **Impact:** Designed and deployed **iTrack**, an enterprise near real-time data visualisation and operational health reporting platform.
  * Partnered with Core Technology — who established a dedicated, read-only reporting staging platform to protect live production databases — to build Tableau Server dashboards tracking incoming volumes, inventory ageing, employee productivity, and historical volume trends.
  * Reduced operational triage latency by 90% and provided self-service raw dataset exports for floor-level root-cause analysis.
* **Core Stack:** Tableau Server/ Desktop (Executive Dashboard Suite), Read-Only SQL Reporting Staging Database, T-SQL (Reporting Views), Self-Service CSV/ Excel Export Engine.

---

## 1. Operational Challenge & Governance Guardrails:

### Baseline Operational Friction:
Operational leaders across multiple business units lacked a unified, near real-time view of daily floor performance:

* **Fragmented Data Across Core Production DBs:** Production data was split across disparate transactional databases, making cross-functional visibility impossible without manual data pulls.
* **Database Performance & Live Read-Lock Risks:** Direct, high-frequency querying against live production databases posed severe query lock risks and system degradation for core operational workflows.
* **Lagging Inventory & Ageing Visibility:** Supervisors relied on EOD (End of Day) static reports, leaving them blind to intra-day volume spikes, ageing backlog accumulation, and SLA breach risks.
* **Manual Data Extraction Overhead:** Floor leads and analysts spent hours manually pulling, joining, and cleansing raw data dumps to perform weekly root-cause reviews and productivity audits.

---

## 2. Tech-Ops Partnership & Solution Architecture:
To deliver near real-time operational health tracking while safeguarding live production systems, a clear division of responsibility was established between Core Technology and the Analytics team:

```text
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                        CORE PRODUCTION TRANSACTIONAL DATABASES                         │
│  ┌─────────────────────────┐   ┌───────────────────────────┐   ┌────────────────────┐  │
│  │ Main Operations DB      │   │ Telemetry & Queue DB      │   │ User & Roster DB   │  │
│  └────────────┬────────────┘   └─────────────┬─────────────┘   └─────────┬──────────┘  │
└───────────────┼──────────────────────────────┼───────────────────────────┼─────────────┘
                │                              │                           │
                └──────────────────────┬───────┴───────────────────────────┘
                                       ▼ (Tech-Managed Porting & Staging)
┌────────────────────────────────────────────────────────────────────────────────────────┐
│               TECH-MANAGED REPORTING STAGING PLATFORM (READ-ONLY)                      │
│  ┌──────────────────────────────────────────────────────────────────────────────────┐  │
│  │ • Tech-built staging layer to isolate live transactional databases               │  │
│  │ • Automated data ingestion & consolidation from core DBs                         │  │
│  │ • Read-Only reporting platform ensuring zero risk to operational systems         │  │
│  └────────────────────────────────────────┬─────────────────────────────────────────┘  │
└───────────────────────────────────────────┼────────────────────────────────────────────┘
                                            ▼ (Analytics & Tableau Ownership)
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                      iTRACK TABLEAU EXECUTIVE CONTROL SUITE                            │
│  ┌──────────────┬──────────────┬──────────────┬──────────────────┬──────────────────┐  │
│  │   VIEW 1     │    VIEW 2    │    VIEW 3    │      VIEW 4      │      VIEW 5      │  │
│  │ Near Real-   │ Inventory    │ Employee     │ Volume Trend &   │ Self-Service     │  │
│  │ Time Volume  │ Aging & SLA  │ Productivity │ Predictive       │ Raw Data Export  │  │
│  │ Monitor      │ Triage       │ & Stack Rank │ Forecasting      │ Triage Hub       │  │
│  └──────────────┴──────────────┴──────────────┴──────────────────┴──────────────────┘  │
└────────────────────────────────────────────────────────────────────────────────────────┘

```

### Architecture & Responsibility Breakdown:

1. **Tech-Managed Reporting Staging Layer:** Core Technology engineered the underlying staging pipeline, porting data from live production databases into a dedicated, read-only SQL reporting platform. This ensured reporting users never touched live production data and eliminated operational locks.
2. **Analytics & Tableau Architecture (Our Ownership):** Built pre-joined analytical views, data models, and Tableau Server dashboards directly on top of the Tech-provided staging layer to deliver sub-second query performance and interactive user experiences.

---

## 3. The 5 Executive Dashboard Views & Analytical Facets:
Designed from the perspective of Operations Managers, Team Leads, and C-Suite Executives, **iTrack** provides interactive, near real-time operational intelligence across 5 curated views:

### View 1: Near Real-Time Volume & Capacity Monitor:
* **Core Metrics:** Inflow volume, processed volume, open pending queue, intra-day SLA attainment %.
* **Analytical Facets:** Filter by **Region**, **Business Unit**, **Operational Queue**, and **Shift/ Hour**.
* **Strategic Value:** Gives operational leads live visibility into current work volume spikes, allowing rapid intra-day resource re-balancing.

### View 2: Inventory Ageing & SLA Risk Triage Matrix:
* **Core Metrics:** Ageing backlog breakdown (<24 hrs, 24–48 hrs, 48–72 hrs, >72 hrs/ SLA Breach).
* **Analytical Facets:** Filter by **SLA Priority Bucket**, **Legal Entity**, **Client Tier**, and **Queue Type**.
* **Strategic Value:** Highlights ageing inventory before SLAs are breached, driving priority-based task dispatch.

### View 3: Employee Productivity & Stack Ranking Framework
* **Core Metrics:** Hourly items processed per FTE, active vs. idle time, accuracy/ quality scores, weighted standard deviation productivity index.
* **Analytical Facets:** Filter by **Team Lead**, **Shift**, **Task Complexity Level**, and **Individual Contributor**.
* **Strategic Value:** Normalises team performance evaluation across varying task complexities, identifying coaching needs and top performers objectively.

### View 4: Historical Volume Trends & Predictive Workload Forecasting:
* **Core Metrics:** Week-over-Week (WoW) & Month-over-Month (MoM) volume trends, seasonal volume curves, historical completion velocities.
* **Analytical Facets:** Filter by **Historical Time Range (07d, 30d, 90d, 01y)**, **Product Line**, and **Transaction Type**.
* **Strategic Value:** Uses time-series analytics to project upcoming operational volume surges and support long-term capacity planning.

### View 5: Self-Service Joined/ Union Raw Data Download Hub:
* **Core Feature:** A dedicated Tableau export portal connected directly to the consolidated staging dataset.
* **Operational Capability:** Enables Team Leads and Quality Trainers to download standardised, pre-filtered CSV/ Excel extracts containing full transaction lineage (IDs, timestamps, user actions, error reasons).
* **Strategic Value:** Eliminates ad-hoc data pull requests to Tech and empowers floor leads to conduct immediate root-cause investigations on errors.

---

## 4. Measurable Business Results & Operational Impact:

| Performance Metric | 🛑 Baseline State (Pre-iTrack) | 🎯 Post-Deployment State (iTrack Engine) | 💡 Strategic Value |
| --- | --- | --- | --- |
| **Data Recency** | Delayed EOD static reports | **Near Real-Time Staged Refresh** | Immediate intra-day operational visibility |
| **Production System Risk** | Direct query risks on live DBs | **100% Protected via Tech Staging Layer** | Zero performance degradation on live transactional systems |
| **Backlog Ageing Management** | Reactive identification Post-SLA breach | **Proactive SLA Risk Triage (<24h to >72h)** | Drastic reduction in SLA non-compliance fees |
| **Productivity Tracking** | Subjective, un-adjusted item counts | **Multi-Factor Weighted Productivity Model** | Fair, transparent, and normalised staff stack-ranking |
| **Root-Cause Triage Time** | Days waiting for central IT data pulls | **Self-Service 1-Click Raw Data Downloads** | Accelerated floor-level defect elimination |

---

## 5. Key Competencies Demonstrated:
* **Tech-Ops Bridge & Strategic Alignment:** Partnering effectively with Core Technology to establish clean data boundary guardrails (read-only staging vs. analytics layer).
* **Executive Visualisation & Storytelling:** Building multi-perspective Tableau control suites covering volume, ageing, productivity, trends, and export capabilities.
* **Operational Health & Telemetry Analytics:** Translating complex operational floor metrics into actionable executive visual indicators.
* **Self-Service BI Enablement:** Democratising raw data access for operational leads to perform independent root-cause analysis without technical dependencies.

---
