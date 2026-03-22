# 🛒 RFM Customer Segmentation — Olist E-Commerce
### K-Means Clustering | 93,358 customers | 4 segments | Looker Studio

[![Python](https://img.shields.io/badge/Python-3.11-3776AB?style=flat&logo=python&logoColor=white)](https://python.org)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.4-F7931E?style=flat&logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![Colab](https://img.shields.io/badge/Open_in_Colab-F9AB00?style=flat&logo=googlecolab&logoColor=white)](https://colab.research.google.com/drive/1HHgtJT80tzP0yy8T5MNXq-RSQBriuy0f?usp=sharing)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 🎯 Business problem

E-commerce companies lose millions every year treating all customers
the same way. A discount campaign sent to every customer wastes budget
on those who would buy anyway — and misses those who are about to churn.

**Can we segment 93,358 customers into actionable groups based purely
on their purchase behavior — and quantify the revenue opportunity
of each segment?**

This project proves we can, using RFM analysis and K-Means clustering
on real transactional data from Olist, Brazil's largest e-commerce
marketplace.

---

## 📊 Results

| Segment | Customers | % of base | Revenue | Days inactive |
|---|---|---|---|---|
| High Value | 2,801 | 3.0% | $864K (5.6%) | 199 days |
| At Risk | 32,165 | 34.5% | $9.5M (61.7%) | 255 days |
| New / Promising | 16,172 | 17.3% | $2.1M (14.0%) | 38 days |
| Lost / Inactive | 42,220 | 45.2% | $2.8M (18.7%) | 270 days |

**Model performance:** K=4 · Silhouette Score = 0.40

---

## 💡 Key insights

1. **At Risk generates 61.7% of total revenue** — 32,165 customers
   who used to buy well but have been inactive for 255 days on average.
   Reactivating just 20% of them = **+$1.9M USD** in recovered revenue.

2. **45% of the base is Lost or Inactive** — the majority of customers
   bought once and never returned. This is the #1 challenge for
   Olist's retention strategy.

3. **New / Promising = the golden window** — 16,172 customers who
   purchased in the last 38 days. The next 90 days define whether
   they become loyal or lost.

4. **High Value is only 3% of the base** — but they are the most
   valuable individually ($225 USD median spend). Losing one costs
   more than acquiring ten new customers.

5. **Average purchase frequency = 1.03** — almost every customer
   buys only once. Building repeat purchase behavior is the core
   growth lever for this business.

---

## 🗂️ Project structure
```
olist-rfm-segmentation/
│
├── 📓 olist_rfm_segmentation.ipynb    # Main notebook (Colab-ready)
├── 🖼️  rfm_clusters_3d.png            # 3D cluster visualization
├── 🖼️  rfm_distribucion_segmentos.png # Segment distribution chart
├── 🖼️  rfm_heatmap.png                # RFM heatmap by segment
├── 🖼️  rfm_seleccion_k.png            # Elbow method + Silhouette
└── 📄 README.md
```

---

## ⚙️ Tech stack

| Tool | Use |
|---|---|
| **Python 3.11** | Base language |
| **Pandas / NumPy** | Data manipulation |
| **Scikit-learn** | K-Means, StandardScaler, Silhouette Score |
| **Plotly** | Interactive visualizations + 3D scatter |
| **Seaborn / Matplotlib** | RFM heatmap |
| **Google Sheets** | Results storage |
| **Looker Studio** | Executive dashboard |

---

## 🚀 How to run

### Google Colab (recommended)
1. Click the Colab badge above ↑
2. You need a Kaggle account to download the dataset
3. Run all cells in order

### Dataset
- **Source:** [Brazilian E-Commerce Public Dataset by Olist — Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- **Records:** 96,478 delivered orders · 93,358 unique customers
- **Period:** 2016 – 2018
- **License:** CC BY-NC-SA 4.0

---

## 📐 Pipeline
```
Raw data — 9 CSV files (Olist × Kaggle)
       ↓
  Load & merge: orders + customers + payments + items
  Filter: delivered orders only (96,478 of 99,441)
       ↓
  RFM calculation per customer
  · Recency   = days since last purchase
  · Frequency = number of unique orders
  · Monetary  = total amount spent (USD)
       ↓
  RFM Scoring (1–5 per dimension via quartiles)
  Rule-based segmentation (7 segments)
       ↓
  K-Means Clustering
  · log1p transformation (reduce skew)
  · StandardScaler normalization
  · Elbow method + Silhouette Score → K=4
       ↓
  Segment profiling + business recommendations
       ↓
  Export → Google Sheets → Looker Studio
```

---

## 📋 Business recommendations

| Segment | Priority | KPI target | Key action |
|---|---|---|---|
| High Value | 🔴 Critical | Retain 90%+ in 6 months | VIP program + early access |
| At Risk | 🔴 High | Reactivate 20% = +$1.9M | Win-back campaign 15-20% off |
| New / Promising | 🟡 Medium | Convert 30% to repeat buyers in 90d | Welcome email + points program |
| Lost / Inactive | 🟢 Low | Reactivate 5-10% | Aggressive 30% discount or remove |

---

## 📈 Dashboard — Looker Studio

[🔗 View live dashboard](https://lookerstudio.google.com/reporting/1512e570-7492-4f62-af23-8cc0bbb15221) *(replace with your link)*

Dashboard includes:
- 4 KPI scorecards: total customers, revenue, avg ticket, avg recency
- Customer and revenue distribution by segment
- Executive summary table with RFM metrics
- Business recommendations table
- Rule-based RFM segmentation chart
- Global filter by segment

---

## 🤖 Note on AI usage

This project was developed with **Claude (Anthropic)** as technical
copilot — pipeline generation, debugging, documentation and README.

Business decisions, insight interpretation, segment naming and
recommendations were made by the author.

**This is how modern professionals work in 2026.**

---

## 📚 References

- [Olist Brazilian E-Commerce Dataset — Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- [RFM Analysis — Wikipedia](https://en.wikipedia.org/wiki/RFM_(market_research))
- [Scikit-learn KMeans Documentation](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)
- [SHAP: A Unified Approach to Interpreting Model Predictions](https://arxiv.org/abs/1705.07874)

---

## 👤 Author

**Jorge Velázquez Mirabal**
Senior Data Analyst & App Developer
📍 Tlaxcala, México · Open to remote worldwide

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/jorgevelazquezdata)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=flat&logo=github&logoColor=white)](https://github.com/PatoTlax)
[![Portfolio](https://img.shields.io/badge/Portfolio-jorgevelazquez.com-1D9E75?style=flat)](https://jorgevelazquez.com)

---

*If this project was useful, give it a ⭐ — it helps others find it.*
