# Consumer Insights & Marketing Analytics

### Customer Segmentation, Brand Equity Analysis & Commercial Strategy — R

---

## Project Overview

Consulting-style marketing analytics project applying **RFM Modeling**, **K-Means Clustering**, and **brand equity analysis** to 500,000+ retail transactions across 4,000+ customers. Built in R to mirror the analytical workflow used in commercial performance engagements — from raw data validation through to segment-level strategic recommendations.

---

## Business Problem

Large-scale transactional datasets rarely translate directly into commercial decisions. This project builds a structured consumer insights framework to:

- Identify high-value and churn-risk customer segments
- Disaggregate revenue concentration to surface root causes
- Prioritise promotion and retention investment by segment
- Develop brand affinity profiles to guide commercial strategy

---

## Analytical Workflow

```
Data Import → Quality Validation → EDA & Revenue Variance → RFM Engineering
→ K-Means Clustering → Cluster Validation → Segment Profiling → Strategic Recommendations
```

---

## Methodology

### 1. Data Quality Validation
- Removed missing Customer IDs, cancelled orders (`^C` prefix), zero-price and negative-quantity records
- Retained ~74% of raw records after cleaning; structured remainder for analysis

### 2. EDA — Revenue Variance Analysis
- Identified top-10 products by revenue contribution
- Monthly trend analysis to surface seasonal deviations and commercial performance patterns

### 3. RFM Feature Engineering
- **Recency**: days since last transaction
- **Frequency**: distinct invoice count per customer
- **Monetary**: total revenue generated
- Scored each dimension on a 1–5 quintile scale; combined into composite RFM score

### 4. Predictive Modeling — K-Means Clustering
- Scaled RFM features prior to clustering (`scale()`)
- **Elbow Method** (k = 1–10) to identify optimal cluster count
- **Silhouette Score** (k = 2–8) for cluster cohesion validation
- Final model: **k = 4**, `nstart = 50`, `iter.max = 200`

### 5. Segment Profiling & Brand Equity Analysis
- Labelled segments: Champions, Loyal–High Value, At Risk, Lapsed
- Brand affinity proxy: frequency × monetary quantile scoring (High / Medium / Low)
- Revenue share computed per segment to prioritise retention targeting

### 6. Root-Cause Analysis — Pareto Curve
- Cumulative revenue concentration plotted against customer percentile
- Identified the customer share driving 60%+ of total revenue
- Insight used to direct promotion and loyalty programme investment

---

## Key Findings

| Segment | Avg Recency | Avg Frequency | Brand Affinity | Revenue Share |
|---|---|---|---|---|
| Champions | ≤ 30 days | High | High | Largest |
| Loyal – High Value | ≤ 90 days | Medium–High | High | Second |
| At Risk | ≤ 180 days | Declining | Medium | Third |
| Lapsed | > 180 days | Low | Low | Smallest |

- Top 2 segments (Champions + Loyal–High Value) account for ~60% of total revenue
- Pareto analysis confirmed high revenue concentration in a small customer share
- Segment-specific promotion strategy documented for each cohort

---

## Strategic Recommendations

| Segment | Action |
|---|---|
| Champions | Priority retention: loyalty programme, early access, personalised comms |
| Loyal–High Value | Upsell higher-margin SKUs; re-engage before churn window closes |
| At Risk | Win-back: time-limited discount + category-relevant recommendations |
| Lapsed | Minimal spend; monitor for natural reactivation |

---

## Tools & Technologies

| Category | Detail |
|---|---|
| Language | R |
| Libraries | dplyr, ggplot2, cluster, factoextra, scales, tidyr, readxl |
| Methods | RFM Modeling, K-Means Clustering, Elbow Method, Silhouette Score, Pareto Analysis |
| Visualisations | 8 plots — revenue variance, RFM distributions, cluster scatter, brand equity bar, Pareto curve |

---

## Repository Structure

```
├── rfm-customer-segmentation.ipynb   # Full R analysis (Kaggle notebook format)
├── README.md
└── LICENSE
```

> **Note**: The `.ipynb` file contains R kernel code — all analysis is written in R using tidyverse and clustering libraries. Kaggle notebooks use the `.ipynb` container format regardless of kernel language.

---

## Dataset

- **Source**: UCI Online Retail Dataset (via Kaggle)
- **Scale**: 500,000+ transactions, 4,000+ customers
- **Period**: ~12 months of retail transaction history
- **Key fields**: CustomerID, InvoiceDate, Quantity, UnitPrice, Description
