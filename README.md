# 📊 A Cohort-Based Customer Retention Analysis for E-Commerce Growth

**Author:** Quynh Vo
**Date:** 2026
**Tools Used:** Python (Google Colab)
- **Python:** pandas, seaborn, matplotlib, datetime

## 📋 README — Table of Contents

1. [Executive Summary](#-executive-summary)
2. [Background & Objectives](#-background--objectives)
3. [Dataset Description](#-dataset-description)
4. [Data Processing & Methodology](#-data-processing--methodology)
5. [Defining Key Questions Before Analysis](#-defining-key-questions-before-analysis)
6. [Key Insights & Visualizations](#-key-insights--visualizations)
7. [Recommendations](#-recommendations)

## 🚀 Executive Summary

This project uses **cohort analysis** on e-commerce data from 2020–2023 to measure customer retention, compare loyalty patterns between **Corporate and Consumer segments**, and identify which **income group** delivers the most sustainable profit over time.

The analysis answers three core questions:
- How well does this business retain customers after first purchase?
- Do Corporate customers behave differently from Consumer customers?
- Which income group (Low / Mid / High) is the most valuable to retain long-term?


## 📌 Background & Objectives

**Background:**

Customer retention is one of the most important drivers of sustainable e-commerce growth. Acquiring new customers is expensive — understanding how and when existing customers return is critical to designing effective re-engagement strategies.

Cohort analysis groups customers by their first purchase month and tracks how many return in subsequent months, revealing the true retention rhythm of the business.

**Three Objectives:**

1. Measure overall customer retention rates across 2022 cohorts
2. Compare retention patterns between Corporate and Consumer customer segments
3. Identify which income band (Low / Mid / High) delivers the most sustainable retention and profit over time


## 🕵🏼‍♂️ Who Is This Project For?

- **CRM & Marketing Managers** — to design re-engagement campaigns timed to the business's natural purchase cycle
- **Segment Managers** — to understand behavioral differences between Corporate and Consumer customers
- **Growth Teams** — to prioritize which customer income groups to acquire and retain


## 📂 Dataset Description

**Dataset Period:** 2020–2023 (cohort analysis focuses on 2022 acquisition cohorts)
**Format:** CSV → Python (Google Colab)

| Table | Key Fields Used |
|---|---|
| `Customer.csv` | CustomerID, AnnualIncome |
| `EcomSales.csv` | CustomerID, OrderDate, Profit, Segment |


**Income Band Definition (based on AnnualIncome distribution):**

| Band | Income Range |
|---|---|
| Low | Below $40,000 |
| Mid | $40,000 – $90,000 |
| High | Above $90,000 |

## 🔧 Data Processing & Methodology

**Cohort Setup:**
1. Identified each customer's **first-ever order date** across all years using `df_ecomsales.groupby('CustomerID').agg(first_datetime=('OrderDate','min'))`
2. Filtered to customers whose **first order was in 2022**, and tracked only their **2022 orders**
3. Calculated **month difference** (cohort index) = months elapsed since first purchase
4. Built cohort pivot tables: rows = first order month, columns = cohort index (0, 1, 2…), values = unique customers
5. Calculated **retention rate** = customers in month N ÷ customers in month 0

**Segment Analysis:**
- Split cohort into **Corporate** and **Consumer** using the `Segment` field from `EcomSales.csv`
- Built separate cohort pivot tables for each segment

**Income Band Analysis:**
- Merged cohort data with `AnnualIncome` from `Customer.csv`
- Assigned Low / Mid / High income bands
- Built separate retention heatmaps for each income band


## 🗯️ Defining Key Questions Before Analysis

- What is the Month 1 retention rate — do customers come back the very next month?
- Is there a natural purchase cycle (monthly, quarterly)?
- Which acquisition month produced the largest cohort in 2022?
- Do Corporate customers return faster or slower than Consumer customers?
- Which income group has the highest long-term retention rate?
- Which income group is the most sustainable in volume over time?


## 📊 Key Insights & Visualizations

### I. Overall Cohort Retention Analysis — 2022 Acquisition Cohorts

**📌 Key Findings:**

**Cohort Sizes:**
- Largest cohorts: **Sep 2022 (518), Jun 2022 (517), Nov 2022 (470)** — suggesting strong customer acquisition mid-to-late year
- Smallest cohort: **Jan 2022 (252)**

**Month 1 Retention:**
- Month 1 retention is very low across all cohorts — averaging around **1–3%**
- Most customers do not return the very next month after their first purchase

**Retention Pattern:**
- Retention gradually improves at **Month 3–6**, suggesting customers tend to return on a **quarterly purchase cycle** rather than monthly
- The **Jan 2022 cohort** shows the highest long-term retention at Month 10 at **3.57%** — having had the most time to return

**Overall Pattern:**
- This is a **low-frequency, non-subscription e-commerce business** — customers do not shop every month, which is normal for general merchandise
- The average retention curve stays between **1–4%** after Month 0, consistent across all cohorts


### II. Segment Analysis: Corporate vs. Consumer

**📌 Key Findings:**

**1. Corporate retains better short-term (Month 1–2)**
- Corporate customers return faster after acquisition — the May 2022 cohort reaches **4.3% at Month 1**
- Consumer's best Month 1 performance is **2.9% (July cohort)**
- This likely reflects recurring business procurement behavior rather than personal shopping decisions

**2. Consumer overtakes at Month 5–6**
- Consumer cohorts show stronger late-stage retention — the March 2022 cohort reaches **5.2% at both Month 5 and Month 9**
- Once re-engaged, Consumer customers tend to stay active longer than Corporate counterparts

**3. Corporate return pattern is more irregular**
- Corporate shows more scattered blank cells across the matrix, indicating unpredictable purchase timing
- Consumer retention, while similarly low, is more evenly distributed across months

**4. Both segments follow a quarterly purchase cycle**
- Retention peaks consistently appear at **Month 3 and Month 5–6** for both groups
- This confirms a **60–90 day re-engagement window** as the natural rhythm of this business


### III. Income Group Analysis: Low / Mid / High

**📌 Key Findings:**

**1. High-income (>$90K) — Strongest retention rate over time**
- The smallest group but the most loyal
- Retention climbs to **6.9% at Month 10** (Jan cohort) and **6.7% at Month 7** (May cohort)
- The only group where late-stage retention **consistently improves** rather than fades

**2. Mid-income ($40K–$90K) — Most sustainable in volume**
- Largest cohort sizes: **129–313 customers per month**
- Retention activity visible across all 11 months
- Not the highest rate, but the most **consistent and long-lasting** presence across the full observation window

**3. Low-income (<$40K) — Fades after Month 6**
- Decent early retention but activity drops sharply after Month 6
- Most cohorts show no returns beyond Month 8
- Engages early but does not sustain long-term


## 💡 Recommendations

| Who | Strategy | Insight | Recommendation |
|---|---|---|---|
| Marketing Manager | ⏱️ Time Corporate Re-engagement at 30 Days | Corporate customers show highest return intent at Month 1 (up to 4.3%) | Apply **30-day follow-up campaigns** for Corporate customers to capitalize on their short-term return window |
| Marketing Manager | 🔁 Time Consumer Re-engagement at 90 Days | Consumer retention peaks at Month 3 and Month 5–6 | Use **90-day re-engagement sequences** for Consumer customers — earlier outreach misses their natural purchase cycle |
| CRM Manager | 💎 Invest in Retaining Mid-income Customers | Mid-income ($40K–$90K) is the largest group (129–313 per cohort) with consistent retention across all 11 months | Prioritize Mid-income as the **revenue foundation** — they deliver the most sustainable profit volume over time |
| Growth Team | 📈 Grow the High-income Base | High-income (>$90K) shows the strongest loyalty (up to 6.9% at Month 10) but is too small to drive volume alone | Invest in **acquiring more High-income customers** to build long-term retention upside alongside the Mid-income base |
| Marketing Manager | 🚫 Limit Budget on Low-income After Month 6 | Low-income customers fade sharply after Month 6 with minimal returns beyond Month 8 | Focus Low-income re-engagement within the first 6 months only — do not invest in long-term retention campaigns for this group |


## 🗂️ Project Structure

```
├── Customer_Retention_Analysis.ipynb    # Main analysis notebook
├── Customer.csv                          # Customer demographics & income
├── EcomSales.csv                         # Transaction data with segment labels
├── Product.csv                           # Product catalog
├── Region.csv                            # Geographic data
└── README.md                             # Project documentation
```

