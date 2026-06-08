# Eighth_Project_Devlab

# 🏢 HR Attrition Analytics — Capstone Project

## Overview

This end-to-end analytics project investigates **employee attrition** using the IBM HR Analytics Employee Attrition & Performance dataset (sourced from Kaggle). The goal is to identify the key drivers of employee turnover, segment high-risk employee profiles, and quantify the financial cost of attrition — providing actionable intelligence for HR and leadership teams.

---

## Dataset

| Property | Details |
|---|---|
| Source | [IBM HR Analytics — Kaggle](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) |
| File | `WA_Fn-UseC_-HR-Employee-Attrition.csv` |
| Size | 1,470 employees × 35 features |
| Target Variable | `Attrition` (Yes / No) |
| Overall Attrition Rate | ~16.1% (237 of 1,470 employees) |

---

## Project Structure

```
hr-attrition-capstone-project.ipynb
│
├── Section 0  — Setup & Dataset Download
├── Section 1  — Data Preparation (feature engineering, tenure & income groups)
├── Section 2  — KPI Summary Table (Churned vs. Retained)
├── Section 3  — Attrition Rate by Key Dimensions
├── Section 4  — Tenure & Income Group Analysis
├── Section 5  — Dual Pivot Analysis (heatmaps)
├── Section 6  — Correlation Ranking (Top 10 Drivers)
├── Section 7  — High-Risk Employee Profiles
├── Section 8  ⭐ Bonus: Cost of Attrition Estimation
├── Section 9  ⭐ Bonus: Triple-Risk Segment Analysis
└── Section 10 — Executive Summary Dashboard
```

---

## Methods & Techniques

- **Descriptive Analytics** — KPI comparison tables, group-level attrition rates
- **Feature Engineering** — Tenure grouping (0–2, 3–5, 6–10, 11+ yrs), income quartile binning
- **Pivot Analysis** — Cross-tabulation of Department × Job Satisfaction and Department × Work-Life Balance
- **Correlation Analysis** — Pearson correlation ranking of all numeric features against the binary attrition target
- **Risk Profiling** — Segment-level attrition rates for combined high-risk conditions
- **Cost Modeling** — Replacement cost estimation using a 6-month salary assumption
- **Visualization** — Matplotlib & Seaborn charts including bar plots, heatmaps, and a 6-panel executive dashboard

---

## Key Findings & Business Insights

### 1. 🏬 Attrition Varies Sharply by Department and Role
- **Sales** (21.5%) and **HR** (~19%) have the highest departmental attrition, well above the company average.
- At the role level, **Sales Representatives** top the chart at ~39.8%, followed by **Laboratory Technicians** at ~24%.
- **Implication:** Targeted retention programs should prioritize these departments and roles before general company-wide initiatives.

### 2. ⏰ Overtime is the Single Strongest Behavioral Risk Factor
- Employees working overtime leave at **30.5%** — nearly 3× the rate of non-overtime employees (10.4%).
- This is one of the top positive correlations with attrition across all features.
- **Implication:** Workload management and overtime policies deserve immediate review. Chronic overtime signals understaffing, not dedication.

### 3. 📅 New Employees Leave at an Alarming Rate
- Employees with **0–2 years** of tenure churn at **~36%** — more than double the overall average.
- Attrition drops sharply as tenure increases, falling to single digits for employees with 11+ years.
- **Implication:** Onboarding quality, early-career support, and 90-day/1-year manager check-ins are critical. The first two years are the highest-risk window.

### 4. 💰 Low Pay Drives Exits — But It's Not the Whole Story
- Employees in the **bottom income quartile (Q1)** have the highest attrition rate.
- However, even higher earners leave when combined with poor work-life balance or low satisfaction.
- **Implication:** Compensation reviews for Q1 employees are necessary, but salary alone won't solve attrition — culture and quality of work life matter equally.

### 5. 😔 Job Satisfaction and Work-Life Balance Are Compounding Factors
- Employees with the lowest job satisfaction (score = 1) and poor work-life balance (score = 1) consistently show elevated attrition across all departments.
- The heatmap analysis reveals that **Sales** employees with low job satisfaction face attrition rates exceeding **30–40%** in some cells.
- **Implication:** Regular pulse surveys tracking satisfaction and balance scores can serve as an early warning system before turnover occurs.

### 6. 🚨 Stacked Risk Factors Create Extreme Vulnerability
Three high-risk profiles were identified:

| Profile | Conditions | Attrition Rate |
|---|---|---|
| Profile 1 | Overtime + Early Tenure (0–2 yrs) | Very high |
| Profile 2 | Low Job Satisfaction (1) + Overtime | Very high |
| Profile 3 | Poor Work-Life Balance (1) + Low Income (Q1) | High |
| **Triple Risk** | Overtime + JobSat=1 + Low Income | **Highest** |

The **triple-risk segment** (overtime + lowest job satisfaction + bottom-quartile pay) leaves at a rate **significantly above the company average**. Though a small group, they represent the highest-urgency intervention target.

### 7. 💸 The Financial Exposure is Substantial
Using a conservative estimate of **6 months' salary** as the cost to replace a single employee:

- ~237 churned employees × average monthly salary × 6 = **estimated multi-million dollar annual replacement cost**
- This excludes hidden costs: lost productivity, knowledge transfer, interview time, and team disruption.
- **Implication:** Even a modest 5–10% reduction in attrition would generate significant savings that can justify investment in retention programs, compensation adjustments, or HR tooling.

---

## Top 10 Attrition Drivers (Correlation Ranking)

| Direction | Feature | Interpretation |
|---|---|---|
| Positive (↑ = more attrition) | OverTime (encoded) | Working overtime strongly predicts leaving |
| Positive | Distance from Home | Longer commutes increase turnover risk |
| Negative (↓ = more attrition) | Total Working Years | More experienced employees stay longer |
| Negative | Job Level | Senior roles have lower attrition |
| Negative | Monthly Income | Higher pay is protective |
| Negative | Years in Current Role | Stability in role reduces churn |
| Negative | Years with Current Manager | Strong manager relationships retain people |
| Negative | Age | Older employees are more likely to stay |
| Negative | Years at Company | Tenure is protective after the early period |

---

## Requirements

```
pandas
numpy
matplotlib
seaborn
kaggle
```

Install with:
```bash
pip install pandas numpy matplotlib seaborn kaggle
```

You'll also need a [Kaggle API key](https://www.kaggle.com/docs/api) configured at `~/.kaggle/kaggle.json`.

---

## How to Run

1. Clone or download this repository.
2. Set up your Kaggle credentials.
3. Open `hr-attrition-capstone-project.ipynb` in Jupyter Notebook or JupyterLab.
4. Run all cells from top to bottom (`Kernel → Restart & Run All`).

All charts are automatically saved as PNG files in the working directory:

- `attrition_by_dept_role.png`
- `attrition_tenure_income.png`
- `pivot_heatmaps.png`
- `top10_correlations.png`
- `risk_profiles.png`
- `executive_dashboard.png`

---

## Strategic Recommendations Summary

| Priority | Action |
|---|---|
| 🔴 Immediate | Audit overtime policies — cap chronic overtime and review staffing levels in Sales and R&D |
| 🔴 Immediate | Flag and engage the triple-risk employee segment (OT + low satisfaction + low pay) |
| 🟠 Short-term | Strengthen onboarding for 0–2 year employees; implement 30/60/90-day manager touchpoints |
| 🟠 Short-term | Conduct compensation benchmarking for Q1 income earners, especially in high-attrition roles |
| 🟡 Medium-term | Roll out quarterly pulse surveys tracking job satisfaction and work-life balance by department |
| 🟡 Medium-term | Build a predictive attrition model using the correlation drivers identified here |

---

