---
layout: page
title: "🏬 Big W Sales Forecasting Project"
permalink: /Projects/bigw-sales-prediction/
---

## 📘 Project Overview

This repository presents a machine learning project focused on **sales forecasting and profitability optimization** for Big W, a major Australian discount department store.

> 📍 Completed as part of the **QBUS6600 Data Analytics for Business Capstone** at the University of Sydney.

---

## 🎯 Objective

To help Big W optimize its pricing and promotional strategies through:

- Exploratory Data Analysis (EDA)
- Feature Engineering
- Predictive Modeling
- Business-driven recommendations

---

## 📂 Project Files

- [`QBUS6600_Group 74_ Version 1.pdf`](./Big_W_report.pdf) — Full project report with methodology, visualizations, and recommendations  
- [`Data Wrangling_final.ipynb`](./Data_Wrangling_final.ipynb) — Jupyter notebook with data preprocessing, feature engineering, and model implementation

---

## 🔍 Key Features Analyzed

- Impact of **price sensitivity**, **scanback promotions**, and **seasonality**
- Competitor pricing effects across multiple retail chains
- Sales uplift factors based on **day of week**, **subcategory**, and **promotion timing**

---

## 🤖 Models Applied

**1. Elastic Net**  
- RMSE (Train): 45.70  
- RMSE (Test): 47.64  
- ✅ Linear baseline model with LASSO-dominated regularization  
- ❗ Limitations: Moderate explanatory power (Adjusted R² = 0.4571)

**2. Random Forest**  
- RMSE (Train): 39.11  
- RMSE (Test): 42.75  
- ✅ Best performance among models; explained variance ~56%  
- ❗ Limitations: Harder to interpret; sensitive to feature noise

**3. XGBoost**  
- RMSE (Test): Higher than RF; Adjusted R² = 0.66  
- ✅ Captures complex non-linear interactions  
- ❗ Sensitive to outliers; needs more tuning

---

## 💡 Business Insights

- **Inventory Strategy**: Use weekday trends to optimize regional stock levels  
- **Promotion Optimization**: Adjust based on SKUs on sale, days since last promotion  
- **Product Mix**: Reduce focus on underperforming subcategories like tanning  
- **Customer Retention**: Implement loyalty programs to support long-term profitability

---

## 📝 Takeaways

- Tree-based models outperform linear ones for sales forecasting under complex market conditions.
- Feature engineering (e.g., `promo_power`, `competition_level`, `days_since_last_promo`) played a critical role in improving prediction accuracy.
- Demand and profitability are **not always aligned** — models need to account for both.

---
