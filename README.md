# Healthcare Analytics for Doctor Visits

## Project Overview

This project analyzes a dataset of **5,190 individuals** to understand the patterns behind doctor visit behavior. The goal is to identify which personal, financial, health, and healthcare-support factors influence how often people visit a doctor, and to translate those findings into actionable insights for healthcare planning.

The analysis is presented as an interactive Jupyter notebook: `Healthcare_Analytics_Doctor_Visits.ipynb`

---

## Problem Statement

Doctor visits are a key indicator of healthcare demand and population health, yet visit rates vary widely across different groups of people. Some individuals visit doctors frequently, while many others rarely or never seek care, even when they may need it. Understanding why these differences exist is essential for improving healthcare access, planning medical resources, and designing effective support programs.

Key questions addressed:
- What factors — such as age, gender, income, health condition, and illness — influence how often people visit a doctor?
- How do healthcare support options (private insurance, free care for the poor, repatriation programs) affect doctor visits?
- Why do some groups, such as people with chronic conditions or older individuals, utilize healthcare services more than others?

---

## Dataset

**File:** `P2-Healthcare Analytics for Doctor Visits.csv` (5,190 records, 12 columns)

| Column | Description |
|---|---|
| `visits` | Number of doctor visits during the observation period (**target variable**) |
| `gender` | Gender of the person (male / female) |
| `age` | Age of the person (scaled decimal format) |
| `income` | Income level of the person or household |
| `illness` | Number of illnesses / health problems reported (0–5) |
| `reduced` | Days normal activities were reduced due to health problems (0–14) |
| `health` | Numerical general health-status score (0–12) |
| `private` | Has private healthcare / insurance (yes / no) |
| `freepoor` | Receives free healthcare based on financial need (yes / no) |
| `freerepat` | Receives repatriation-related healthcare support (yes / no) |
| `nchronic` | Has a chronic health condition (yes / no) |
| `lchronic` | Has a long-term chronic health condition (yes / no) |

**Column groups:** Personal Information (gender, age) · Financial (income) · Health (illness, reduced, health, nchronic, lchronic) · Healthcare Support (private, freepoor, freerepat) · Target (visits)

---

## 🛠️ Tools & Technologies

- **Python 3**
- **pandas, numpy** — data manipulation and analysis
- **matplotlib, seaborn** — data visualization
- **statsmodels** — statistical modeling (Poisson regression)

---

## Analysis Workflow

1. **Data Loading & Quality Check** — load CSV, verify shape, dtypes, and missing values
2. **Target Variable Analysis** — distribution of visit counts, zero-visit share
3. **Demographic Analysis** — visits by gender and age bands
4. **Health Factor Analysis** — illness count, reduced-activity days, health score, chronic conditions
5. **Healthcare Support Analysis** — private insurance, freepoor, freerepat comparisons
6. **Correlation Analysis** — heatmap of numeric features vs. visits
7. **Statistical Modeling** — Poisson regression with effect-size visualization
8. **Insights & Recommendations**

---

## 🔍 Key Findings

1. **Zero-inflated demand** — ~80% of people made no doctor visit; mean visits = 0.30, max = 9
2. **Health need dominates** — reduced-activity days show the strongest correlation with visits (r = 0.42)
3. **Illness count scales utilization ~6×** — any-visit rate rises from 6.8% (0 illnesses) to 41.9% (5 illnesses)
4. **Long-term chronic condition = 2× utilization** — 0.60 mean visits vs 0.26 without
5. **Women visit ~50% more than men** — 24.4% vs 15.6% any-visit rate
6. **Age matters, but mostly through health** — age loses significance once health variables are controlled
7. **Income slightly reduces visits** — higher income → marginally fewer visits
8. **Support programs diverge** — `freerepat` members visit more (0.47 vs 0.26), while `freepoor` beneficiaries visit much less (0.16 vs 0.31)
9. **Private insurance shows no effect** on visit counts

---

## Recommendations

- **Chronic-care management** — proactive follow-up programs for long-term chronic and multi-illness patients
- **Close the freepoor access gap** — only 9% of free-care beneficiaries visited a doctor; outreach and transport support may help
- **Gender-sensitive outreach** — investigate and address men's lower healthcare utilization
- **Modeling direction** — zero-inflated / hurdle count models (ZIP, Negative Binomial) suit this data better than plain Poisson

---

## How to Run

1. Clone the repository
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn statsmodels jupyter
