# Superstore Sales Analysis — Executive Revenue Dashboard

**End-to-end analytics project | Python · PySpark · Databricks**
Hamburg · 2025

---

## The Business Question

> *Where is this retail business leaking profit, and what should leadership prioritise?*

This project analyses three years of retail sales data (2021–2023) across 4 regions, 3 product categories, 12 sub-categories, and 3 customer segments. The output is a CFO-ready set of findings and four prioritised recommendations.

---

## Key Findings at a Glance

| Metric | Value |
|---|---|
| Total revenue (3 years) | €7,430,788 |
| Total profit | €766,194 |
| Overall profit margin | 10.3% |
| Worst sub-category | Tables (negative margin) |
| Best sub-category | Copiers (28% margin) |
| Primary profit leak | Discounts ≥ 30% |

---

## Charts and Insights

### 1. Revenue and profit by year
![Revenue and profit by year](charts/chart1_revenue_profit_year.png)

Revenue grew steadily year-on-year. Profit margin remained under pressure — the gap between revenue growth and profit growth signals a structural margin problem, not a volume problem.

---

### 2. Profit margin by sub-category — the Tables problem
![Profit margin by sub-category](charts/chart2_margin_subcategory.png)

Tables are the only sub-category with a **negative profit margin**. Every table sold loses money. Copiers, Paper, and Accessories are the strongest contributors. This chart alone justifies a SKU-level pricing review.

---

### 3. Discounts are destroying profit
![Discount vs profit scatter](charts/chart3_discount_profit.png)

There is a clear negative relationship between discount depth and profit. Orders with discounts ≥ 30% are consistently loss-making across all three categories. This is a controllable lever — a discount governance policy would materially improve overall margins.

---

### 4. Furniture underperforms in every region
![Region × Category heatmap](charts/chart4_region_category_heatmap.png)

Technology is profitable everywhere. Furniture generates near-zero or negative profit in Central and South regions. This pattern points to a logistics or pricing issue specific to those regions, not a category-wide problem.

---

### 5. Monthly revenue trend — Q4 seasonality
![Monthly revenue trend](charts/chart5_monthly_trend.png)

Q4 (October–December) consistently produces the highest revenue across all three years. Inventory planning, staffing, and promotional budgets should be structured around this pattern.

---

### 6. Corporate segment: best revenue and best margins
![Segment profitability](charts/chart6_segment_profitability.png)

Corporate accounts generate the highest revenue and the strongest profit margins. Home Office is the smallest and least profitable segment. Investment in Corporate account management delivers the highest return.

---

## Executive Recommendations

| Priority | Action | Expected impact |
|---|---|---|
| 🔴 High | Cap discounts at 20%; require approval above 15% | +2–3% overall margin |
| 🔴 High | Reprice or exit negative-margin Tables SKUs | Eliminate profit destruction |
| 🟡 Medium | Grow Corporate accounts via account management | Highest-ROI customer segment |
| 🟡 Medium | Regional audit: Furniture in Central and South | Recover profit leakage |

---

## Technical Approach

The analysis is built in a single Databricks-compatible notebook (`superstore_analysis.ipynb`) covering:

1. **PySpark ingestion** — data loaded and schema-validated via Spark DataFrame
2. **Pandas transformation** — converted for analysis and visualisation
3. **Revenue analysis** — year-on-year and monthly trend decomposition
4. **Margin analysis** — sub-category and region × category profitability breakdown
5. **Discount analysis** — scatter analysis of discount depth vs. profit outcome
6. **Segment analysis** — revenue and margin comparison across customer segments
7. **Spark SQL summary** — final aggregation run via SQL query on Spark view

---

## Repository Structure

```
superstore-sales-analysis/
│
├── superstore_analysis.ipynb     # Full analysis notebook (Databricks-compatible)
├── superstore_sales.csv          # Dataset (4,500 orders, 2021–2023)
├── charts/
│   ├── chart1_revenue_profit_year.png
│   ├── chart2_margin_subcategory.png
│   ├── chart3_discount_profit.png
│   ├── chart4_region_category_heatmap.png
│   ├── chart5_monthly_trend.png
│   └── chart6_segment_profitability.png
└── README.md
```

---

## Tools and Libraries

| Tool | Purpose |
|---|---|
| Python 3 | Core language |
| PySpark | Scalable data ingestion and Spark SQL aggregation |
| pandas | Data transformation and analysis |
| matplotlib / seaborn | Visualisation |
| Databricks | Notebook execution environment |

---

## How to Run

**On Databricks:**
1. Upload `superstore_sales.csv` to DBFS
2. Import `superstore_analysis.ipynb` as a notebook
3. Run all cells — Spark session is auto-created

**Locally:**
```bash
pip install pandas numpy matplotlib seaborn pyspark
jupyter notebook superstore_analysis.ipynb
```

---

## About

**Anush Mohan**
MSc Digital Transformation Management · Databricks Certified
[LinkedIn](https://linkedin.com) <!-- replace with your actual URL -->

*See also:*
- [`euromix-telecom-analysis`](https://github.com) — Telecom pricing simulation modelling €629K revenue impact
- [`analytics-execution-thesis`](https://github.com) — MSc thesis: 7-stage model for translating analytics insights into execution
