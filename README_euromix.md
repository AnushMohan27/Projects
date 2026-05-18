# EuroamIX Telecom Pricing Simulation

**Group project — Business Analytics coursework**
Hamburg, Germany · March 2025 · Team: Anush, Azadeh, Chinmay & Josua

---

## The Business Problem

EuroamIX, a telecom roaming provider, faces a threat: a competitor has launched a new package-based pricing model (S / M / L tiers). If customers switch rationally — choosing whichever plan costs them less based on their actual usage — what happens to EuroamIX's revenue?

This project quantifies that impact and recommends a counter-strategy.

---

## Key Finding

> Adopting the competitor's model would reduce EuroamIX's annual revenue from **€629,316** to **€156,577** — a loss of roughly **75%**.
>
> The recommended response: a lower pay-as-you-go tariff (€0.003/MB, €0.10/min) that retains all 1,000 customers and generates **€131,342** — only ~€25K less than matching the competitor, but with far lower churn risk and complexity.

---

## Repository Structure

```
euromix-telecom-analysis/
│
├── Data_wrangling_euromix_Final.ipynb   # Full Python pipeline (cleaning → merging → analysis)
├── final_merged_data_1.xlsx             # Combined customer dataset (billing + usage + tariff)
├── Final_presentation_EuromIX.pdf       # Original presentation slides with all charts
└── README.md
```

---

## What the Notebook Does

The Jupyter notebook covers the complete data pipeline in five stages:

**1. Data ingestion and translation**
- Reads three raw source files: `billing.csv` (12 months, French column headers), `subscribers_tariff.csv`, and `usage_data.xlsx`
- Translates French column names and tariff labels to English using a manual mapping dictionary and the `deep_translator` library

**2. Missing value treatment**
- Empty cells surrounded by data → filled with `0` (assuming continuity of service)
- Consecutive empty cells at the start or end of a customer's record → kept as `NULL` (indicating contract start/end mid-year)

**3. Data merging**
- Pivots billing data from long to wide format (one row per customer per month)
- Merges billing, usage (data in KB + call time in seconds), and tariff data into a single flat file: `final_merged_data_1.xlsx`

**4. Revenue calculation**
- Computes actual revenue per customer per month under both current tariffs (pay-as-you-go and reduced)
- Separates revenue contribution from data usage vs. calling vs. monthly fixed fees

**5. Competitor scenario modelling**
- Simulates which competitor package (S/M/L) each customer would rationally choose based on their usage
- Calculates resulting revenue under each scenario and under three proposed counter-strategies

---

## Results Summary

| Scenario | Customers retained | Annual revenue |
|---|---|---|
| Current tariffs (baseline) | 1,000 | €629,316 |
| Competitor's model (if adopted) | 1,000 | €156,577 |
| **Recommended: lower pay-as-you-go** | **1,000** | **€131,342** |

Additional findings:
- 88% of current revenue comes from **data usage** — calling contributes only 0.56%
- The median customer bill is **€39.39/month**
- The top 10% of bills (€112–€566/month) account for **30% of total revenue**
- Under rational switching assumptions, **98% of customers would move to the competitor's M Package**

---

## Tools and Libraries

| Tool | Purpose |
|---|---|
| Python 3 | Core language |
| pandas | Data wrangling, merging, pivot tables |
| numpy | Numerical calculations |
| matplotlib / seaborn | Visualisation |
| deep_translator | French → English translation of source data |
| openpyxl | Excel file read/write |

---

## How to Run

1. Clone the repository
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn deep-translator openpyxl
   ```
3. Place the three source data files (`billing.csv`, `subscribers_tariff.csv`, `usage_data.xlsx`) in the same directory as the notebook
4. Run all cells in `Data_wrangling_euromix_Final.ipynb`

> **Note:** The merged output file (`final_merged_data_1.xlsx`) is already included in the repo — you can skip straight to the analysis section of the notebook if you don't need to re-run the wrangling steps.

---

## Strategic Recommendations Modelled

Three counter-strategies were built and compared against the competitor's offering:

1. **Packages with fixed excess bundles** — new S/M/L tiers with tiered overage pricing
2. **Packages with pay-as-you-go excess** — base packages with per-MB/per-minute overages
3. **Pure pay-as-you-go at reduced rates** — €0.003/MB and €0.10/min ← *recommended*

The pure pay-as-you-go option was preferred by customers across all three usage segments and preserves EuroamIX's existing brand positioning.

---

## About

**Anush Mohan**
MSc Digital Transformation Management, Hamburg
[LinkedIn](https://linkedin.com) <!-- replace with your actual URL -->

*See also:*
- [`analytics-execution-thesis`](https://github.com) — MSc thesis: 7-stage model for translating analytics insights into organizational execution <!-- replace with actual URL -->
