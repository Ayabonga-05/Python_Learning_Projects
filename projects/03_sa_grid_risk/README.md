# ⚡ SA Grid Risk — Loadshedding Stage Classifier & Anomaly Detector

**Project 03 | python_learning_projects**  
**Author:** Aya Mthimde  
**Stack:** Python · Pandas · Scikit-Learn · XGBoost · Google Colab  
**Data:** Real Eskom System Operator data (Mar 2025 – Jun 2026)

---

## What This Project Does

South Africa's electricity grid is managed by a System Operator who must balance supply and demand every second of the day. When supply falls short, **loadshedding** is implemented in stages (0–...)

This project uses **real Eskom grid data** to build two machine learning models:

| Model | Type | What It Does |
|---|---|---|
| **Loadshedding Stage Classifier** | Supervised ML | Predicts the loadshedding risk stage (0–6) from grid metrics |
| **Grid Anomaly Detector** | Unsupervised ML | Flags weeks where grid behaviour was abnormal |

---

## Repo Structure

```
03_sa_grid_risk/
├���─ README.md                          ← You are here
├── requirements.txt                   ← Python libraries needed
├── data/
│   └── sa_grid_risk_dataset.xlsx      ← Master dataset (4 sheets)
├── notebooks/
│   ├── 01_eda.ipynb                   ← Exploratory Data Analysis
│   ├── 02_classifier.ipynb            ← Stage Classifier (RF + XGBoost)
│   └── 03_anomaly_detector.ipynb      ← Anomaly Detector (Isolation Forest)
└── models/
    ├── stage_classifier_rf.pkl        ← Saved Random Forest model
    ├── stage_classifier_xgb.pkl       ← Saved XGBoost model
    ├── anomaly_detector.pkl           ← Saved Isolation Forest model
    └── scaler.pkl                     ← Saved StandardScaler
```

---

## Dataset

The dataset (`sa_grid_risk_dataset.xlsx`) contains **65 weekly observations** across 4 sheets:

- **Sheet 1 — Master Dataset:** 14 columns including EAF, UCLF, demand, renewables, OCGT, engineered features, and the derived Stage label
- **Sheet 2 — Data Dictionary:** Every column explained
- **Sheet 3 — Stage Rules:** How the Stage label was derived from EAF + UCLF + OCGT thresholds
- **Sheet 4 — Stage Distribution:** Row counts per class

### Features (X)

| Column | Abbreviation | Description |
|---|---|---|
| EAF | X1 | Energy Availability Factor — % of capacity available |
| UCLF | X2 | Unplanned Capability Loss Factor — % lost to breakdowns |
| PCLF | X3 | Planned Capability Loss Factor — scheduled maintenance |
| OCLF | X4 | Opportunistic maintenance losses |
| Peak Demand | X5 | Weekly peak demand in MW |
| Avg Wind LF | X6 | Wind turbine load factor % |
| RE Contribution | X7 | Total renewable energy in MW |
| OCGT Usage | X8 | Emergency diesel usage in GWh |
| Supply Gap | X9 | Demand minus RE (engineered) |
| RE Penetration | X10 | RE as % of demand (engineered) |
| Grid Stress Index | X11 | Composite risk score (engineered) |
| Season | X12 | Summer / Autumn / Winter / Spring |

---

### Target (y)

| Stage | Label | Grid State |
|---|---|---|
| 0 | STABLE | No loadshedding |
| 1 | LOW RISK | Stage 1 possible |
| 2 | MODERATE | Stage 1–2 likely |
| 3 | ELEVATED | Stage 2–3 loadshedding |
| 4 | HIGH | Stage 3–4 loadshedding |
| 5 | SEVERE | Stage 4–5 loadshedding |
| 6 | CRITICAL | Stage 6+ / blackout risk |

---

## How to Run (Google Colab)

1. Go to [colab.research.google.com](https://colab.research.google.com)
2. Click **File → Open notebook → GitHub**
3. Paste this repo URL
4. Open each notebook in order: `01_eda` → `02_classifier` → `03_anomaly_detector`
5. Upload `sa_grid_risk_dataset.xlsx` when prompted

---

## Key Results

> Results populate after you run the notebooks.

| Model | Accuracy | F1 Score |
|---|---|---|
| Random Forest | TBD | TBD |
| XGBoost | TBD | TBD |
| Anomaly Detector | — | TBD anomalies flagged |

---

## What I Learned

- How to engineer a target label from raw operational data when no label column exists
- How to build and compare two classification algorithms (Random Forest vs XGBoost)
- How Isolation Forest detects abnormal patterns without labelled data
- How real South African energy data reflects the grid recovery from 2025 to 2026

---

## Data Source

Eskom System Operator public reporting data — Google Drive dataset  
Covers: March 2025 – June 2026 | Weekly granularity

---

## Embedded: South Africa Energy Usage Analysis (Project 03 — compact overview)

This project also contains an embedded overview from a related analysis focused on South African energy consumption and generation. The embedded overview makes Project 03 self-contained by summar...

### Overview (embedded)

Exploratory data analysis on real South African energy consumption and generation datasets. The notebooks demonstrate data cleaning, transformation, visualization, and basic reporting using Jupyt...

Key skills: Pandas, Matplotlib, Seaborn, exploratory data analysis, data cleaning, storytelling with plots

#### Project Contents

- Notebooks:
  - EDA notebook(s) that load the datasets, clean and transform them, and produce figures and tables used in the report.
- Data:
  - CSVs or sourced raw files used for the analysis (where licensing allows). See the notebooks for download links or data-import steps.
- Scripts:
  - Small helper scripts for preprocessing or plotting (if included).
- README (this file): project overview, how to run, and links to related resources.

#### How to run (Google Colab)

Follow the same Colab steps above. The notebooks include setup cells that install any small dependencies and download data when needed.

#### Learning Path & Tech (project-aligned)

- Python fundamentals and problem solving from CS50P (Harvard)
- Data manipulation and analysis with Pandas
- Visualizations with Matplotlib and Seaborn
- Basic machine learning concepts (Scikit-Learn — used sparingly for exploratory models)
- MATLAB & Simulink for engineering/simulation concepts (background learning)

Platform: Google Colab — run everything in the browser.  
Tools: Git, GitHub

#### Certifications (author background)

| Certificate | Issuer | Date |
|---|---|---|
| CS50P | Harvard | Ongoing |
| Python (5-Star) | Kaggle | Nov 2025 |
| Intro to Machine Learning | Kaggle | Mar 2026 |
| Intro to Python | DataCamp | Jun 2026 |
| MATLAB Onramp + Desktop Tools | MathWorks | 2025 |
| Simulink Onramp | MathWorks | Oct 2025 |

#### About the analysis

Goal: Explore energy consumption and generation trends in South Africa, identify seasonal and longer-term patterns, and produce visualizations that support insights for policy or engineering disc...

Typical analysis steps in the notebooks:
- Data ingestion and validation
- Time-series resampling and aggregation (hourly/daily/monthly)
- Identification of peaks and demand patterns
- Correlation analysis between generation sources and consumption
- Clear, annotated visualizations suitable for inclusion in a short report or presentation

---

## Contact & Feedback

I'm a self-directed learner focusing on Python, data analysis, report writing, and simulations while preparing for a BSc in Computer Science (targeting 2027). Projects are updated regularly; feed...

LinkedIn: https://www.linkedin.com/in/ayabonga-mthimde-abbb85350
Email: ayamthimde005@gmail.com

---

*This README embeds the main repository overview so that Project 03 is self-contained.*
