# Jumia Customer Segmentation Project — Team Roles & Task Breakdown

**Client/Stakeholder:** Mr. Kaloki Joel Nzau, Jumia <br>
**Project Type:** Unsupervised Machine Learning — Customer Segmentation <br>
**Framework:** CRISP-DM (Cross-Industry Standard Process for Data Mining)<br>
**Dataset:** [UCI Online Retail Dataset](https://archive.ics.uci.edu/dataset/352/online%2Bretail) <br>
**Team Size:** 6


## 1. Project Objective

Jumia has thousands of customers but lacks a clear understanding of their purchasing behavior. This project applies unsupervised learning (clustering) on transactional data to answer:

- Who are our customers?
- Which customers are the most valuable?
- Which customers are at risk of churn?
- How should marketing treat each segment differently?

The focus is **not** on the number of clusters produced, but on translating each segment into a clear, actionable business narrative.

---

## 2. Team Members

| # | Name | Primary Phase(s) Owned | Role Title |
|---|------|------------------------|-------------|
| 1 | Trevor | Business Understanding (Problem & Solution) |  Business Analyst |
| 2 | Ibrahim | Data Understanding & Data Preparation | Data Engineer |
| 3 | Mary | Exploratory Data Analysis (EDA) | Data Analyst |
| 4 | Godwin | Modelling (RFM & Clustering) | Project Lead/ Machine Learning Engineer |
| 5 | Elvis | Evaluation & Model Validation | ML Evaluation Lead |
| 6 |Mohamed | Recommendations, Conclusion & Documentation | Insights & Reporting Lead |

The six roles map directly onto the CRISP-DM stages requested (Problem, Solution, Data, Data Preparation, EDA, Modelling, Evaluation, Recommendations, Conclusion), grouped into **six balanced workstreams** so that each person owns a full, meaningful slice of the pipeline rather than a fragment.

---

## 3. Detailed Role Breakdown

### 3.1 Trevor — Project Lead / Business Analyst
**CRISP-DM Phase(s):** Business Understanding (Problem Statement + Proposed Solution)

**Responsibilities:**
- Translate Mr. Kaloki's brief into a formal problem statement (business objectives, data mining objectives, success criteria).
- Define what "customer value" and "customer risk" mean in business terms before any modelling begins.
- Draft the proposed solution approach (why clustering/RFM is the right method).



**Deliverables:**
- `01_business_understanding.md` — Problem statement, business objectives, success criteria, constraints.
- Project charter (goals, scope, timeline, risks).

---

### 3.2 Ibrahim — Data Engineer
**CRISP-DM Phase(s):** Data Understanding + Data Preparation

**Responsibilities:**
- Acquire and load the UCI Online Retail dataset; document schema, size, and data dictionary.
- Assess data quality: missing values (e.g., missing `CustomerID`), duplicates, cancelled orders (`InvoiceNo` starting with "C"), negative quantities/prices.
- Handle data cleaning: remove/flag invalid transactions, treat outliers, handle returns.
- Engineer base features required downstream (e.g., `TotalPrice = Quantity * UnitPrice`, date parsing).
- Prepare the clean, analysis-ready dataset and freeze it as a versioned artifact for the rest of the team.

**Deliverables:**
- `02_data_understanding.ipynb` — data profiling, quality report, data dictionary.
- `03_data_preparation.ipynb` — cleaning pipeline, transformation logic.
- `data/processed/online_retail_clean.csv` — the shared clean dataset used by all downstream notebooks.
- Data quality report (`data_quality_report.md`) summarizing issues found and how they were resolved.

---

### 3.3 Mary — Data Analyst (EDA)
**CRISP-DM Phase(s):** Exploratory Data Analysis

**Responsibilities:**
- Explore purchasing patterns: frequency distributions, seasonality, top products/countries, order value distributions.
- Investigate customer-level behavior patterns (recency of last purchase, order frequency, spend variability).
- Visualize relationships that hint at natural customer groupings (e.g., spend vs. frequency scatter plots).
- Surface early business hypotheses to hand off to the modelling team (e.g., "a large group of customers buy once and never return").
- Produce clear, presentation-ready charts for the final report.

**Deliverables:**
- `04_exploratory_data_analysis.ipynb` — full EDA with visualizations and narrative commentary.
- `figures/` folder of exported charts used in the final report.
- EDA summary (`eda_key_findings.md`) — 8–10 key observations feeding into modelling and recommendations.

---

### 3.4 Godwin — Machine Learning Engineer
**CRISP-DM Phase(s):** Modelling

**Responsibilities:**
- Engineer RFM (Recency, Frequency, Monetary) features at the customer level, building on Ibrahim's cleaned dataset.
- Scale/transform features appropriately (log transforms, standardization) for clustering.
- Test and compare clustering approaches (e.g., K-Means, Hierarchical Clustering, DBSCAN) and determine an appropriate number of segments (elbow method, silhouette analysis) — while keeping in mind the client's note that the cluster *count* is secondary to cluster *meaning*.
- Assign each customer to a final segment.

**Deliverables:**
- `05_modelling.ipynb` — RFM feature engineering, model selection, clustering pipeline.
- `models/` folder with saved model artifacts (e.g., pickled scaler + clustering model).
- `data/processed/customer_segments.csv` — final dataset with cluster labels per customer.

---

### 3.5 Elvis — ML Evaluation Lead
**CRISP-DM Phase(s):** Evaluation

**Responsibilities:**
- Validate cluster quality using quantitative metrics (silhouette score, Davies–Bouldin index, within-cluster sum of squares) and qualitative business-sense checks.
- Profile each segment statistically (mean/median Recency, Frequency, Monetary per cluster) and check for stability/robustness (e.g., re-running with different seeds or subsets).
- Name and characterize each segment in plain business language (e.g., "Champions," "At-Risk," "One-Time Buyers," "Loyal Low-Spenders").
- Sanity-check that segments are actionable and distinguishable — not just statistically valid but business-meaningful, directly answering the client's four core questions.

**Deliverables:**
- `06_evaluation.ipynb` — cluster validation metrics, segment profiling tables/charts.
- `segment_profiles.md` — one-page profile per segment (who they are, size, value, risk level).
- Evaluation summary confirming which model/segmentation was selected as final, and why.

---

### 3.6 Mohamed — Insights & Reporting Lead
**CRISP-DM Phase(s):** Recommendations + Conclusion (+ final documentation/QA)

**Responsibilities:**
- Translate each validated segment (from Elvis) into concrete, actionable marketing recommendations (e.g., retention campaigns for at-risk customers, loyalty perks for high-value customers, win-back offers for one-time buyers).
- Write the project conclusion tying all CRISP-DM phases back to the original business questions.
- Assemble the final end-to-end report/notebook combining everyone's outputs into one coherent narrative.
- Perform final QA pass on the repository: check notebooks run top-to-bottom, check consistent formatting, verify all deliverables are present.
- Prepare a short executive summary / stakeholder-facing slide or one-pager suitable for presenting to Mr. Kaloki.

**Deliverables:**
- `07_recommendations.md` — per-segment marketing strategy recommendations.
- `08_conclusion.md` — project conclusion linking back to business objectives.
- `Final_Report.ipynb` or `Final_Report.md` — consolidated end-to-end CRISP-DM report.
- Executive summary (1-page PDF or slide) for stakeholder presentation.
- Final repository QA checklist (sign-off before submission).

---

## 4. Repository Structure

```
jumia-customer-segmentation-crispdm/
│
├── README.md
├── requirements.txt
│
├── data/
│   ├── raw/                     # Original UCI dataset (untouched)
│   └── processed/                # Cleaned data + final segmented dataset
│
├── notebooks/
│   ├── 01_business_understanding.md
│   ├── 02_data_understanding.ipynb
│   ├── 03_data_preparation.ipynb
│   ├── 04_exploratory_data_analysis.ipynb
│   ├── 05_modelling.ipynb
│   ├── 06_evaluation.ipynb
│   ├── 07_recommendations.md
│   ├── 08_conclusion.md
│   └── Final_Report.ipynb
│
├── figures/                      # All exported charts/visuals
├── models/                       # Saved model artifacts
├── reports/
│   ├── data_quality_report.md
│   ├── eda_key_findings.md
│   ├── segment_profiles.md
│   └── executive_summary.pdf
│
└── docs/
    └── project_charter.md
```

---



## 5. Collaboration Guidelines

- **Branching:** Each member works on a feature branch named `feature/<name>-<phase>` (e.g., `feature/mohamed-modelling`) and merges into `main` via Pull Request.
- **Code Review:** At least one other team member reviews each PR before merging.
- **Data Contract:** Ibrahim's cleaned dataset (`data/processed/online_retail_clean.csv`) is the single source of truth — no one re-cleans data independently.
- **Notebook Standards:** Every notebook starts with a markdown cell stating its CRISP-DM phase, owner, and objective.
- **Communication:** Timely async stand-up (Mattermost/WhatsApp).
