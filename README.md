# Portfolio Module 06: Enterprise Data Analytics & Executive Dashboards (Cross-Company)

## Executive Summary:
* **Domain:** Enterprise Data Engineering, Multi-Source SQL/ETL Architecture, Executive RAG Control Suites, Tableau Server Analytics & Capacity Planning
* **Company Context:** Enterprise Analytics across JPMorgan Chase, Dell Technologies, and Global Financial Services
* **Role:** Lead Data Analytics Executive & BI Architect
* **Core Value Delivered:** Designed, engineered, and deployed enterprise-grade operational health dashboards and data pipelines. Combined Alteryx direct SQL ETL workflows with multi-tab Tableau Executive Control Suites to provide real-time visibility into workload burndowns, developer capacity, legal entity compliance risks, and operational queue telemetry—eliminating manual reporting overhead and driving C-suite decision transparency.

---

## 1. Operational Challenge & Scope:

* **Data Fragmentation Across Siloed DBs:** Key performance indicators, developer velocity, and compliance metrics were trapped across disconnected sources (JIRA APIs, central SQL databases, static Excel extracts, and telephony dumps).
* **Lack of Predictive Capacity Modeling:** Leadership lacked visibility into team bandwidth, developer burn rates, and resource bottlenecks, resulting in inaccurate project timeline projections.
* **Manual Executive Reporting Overhead:** Team leads spent significant weekly hours manually collating spreadsheets to produce RAG (Red/Amber/Green) status updates for executive reviews.

---

## 2. Analytics & Executive Visualization Architecture:

1. **Multi-Source ETL Pipeline (Alteryx & Direct SQL):** Engineered automated Alteryx workflows ingesting JIRA post analytics, relational database extracts, and central control logs—performing fuzzy matching, timestamp delta analytics, and data cleansing.
2. **Tableau Executive Control Suite Build:** Architected multi-tab Tableau dashboards providing drill-down visibility from macro-level enterprise burndowns to micro-level task statuses.
3. **Predictive Capacity & Velocity Modeling:** Modeled weekly sprint velocity and burndown curves to project completion dates dynamically against firmwide deadlines.
4. **Automated Lineage & Risk Triage:** Implemented anomaly detection logic within ETL layers to automatically flag missing artifacts, broken entity linkages, and overdue compliance items.

---

## 3. Core Analytics & Dashboard Suite Built:

* **CCOR 2LOD Intelligent Automation Control Suite:** 5-tab Tableau control suite tracking developer capacity, JIRA sprint burndowns, and IS compliance.
* **Legal Entity Risk & Control Audit Matrix:** Regional compliance dashboard breaking down audit readiness across Legal Entities and global time zones.
* **Telemetry Reporting Suite:** Predictive time-series analytics and real-time operational health dashboards (iTrack).

---

## 4. Measurable Business Results & Impact:

| 📌 STRATEGIC PILLAR | 🛠️ OPERATIONAL & TECHNICAL ENABLEMENT IMPACT | 🎯 BUSINESS & FINANCIAL OUTCOME |
| :--- | :--- | :--- |
| **ETL Automation** | Replaced manual spreadsheet collation with automated Alteryx direct SQL pipelines. | **90%+ reduction in reporting lead time**, delivering real-time metric updates. |
| **Capacity Planning** | Deployed predictive burndown and velocity forecasting models. | **Optimized developer allocation** and improved project delivery predictability. |
| **Executive Visibility** | Implemented interactive Tableau Server RAG dashboards with RBAC security. | **Empowered C-suite decision-making** with audit-proof operational health tracking. |

---

## 5. Key Competencies Demonstrated:

* **Enterprise BI Architecture:** Building scalable Tableau dashboards and Alteryx ETL pipelines connected to enterprise SQL/API endpoints.
* **Predictive Data Modeling:** Utilizing statistical time-series and velocity forecasting algorithms for operational decision-making.
* **Executive Data Storytelling:** Designing intuitive RAG control suites that translate complex technical data into actionable executive insights.

---

### Key Project Case Studies:
* ⚙️ **[CCOR 2LOD M&T Intelligent Automation & Audit Analytics Control Ecosystem](./06-CCOR-2LOD-Intelligent-Automation-Ecosystem/Case-Study.md)**  
  *Architected a multi-source Alteryx ETL and 5-tab Tableau Executive Control Suite to ring-fence the full IA Automation and Analytics Book of Work for CCOR 2LOD M&T India. Standardised JIRA tracking, deployed predictive developer capacity modelling, migrated legacy assets to Tableau Server, and enforced 100% Firmwide IS registration and artifact compliance.* <br>
  `Alteryx` • `Tableau Server` • `JIRA API` • `Firmwide IS Governance` • `Capacity Planning` • `Jaro-Winkler Fuzzy Matching`
