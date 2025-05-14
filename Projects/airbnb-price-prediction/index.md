
# 🏡 Airbnb Price Prediction (East Coast Australia)

This repository showcases a predictive modeling project on Airbnb listing prices across Australia's East Coast. The goal was to identify key drivers of listing prices and compare various machine learning models to achieve optimal predictive performance.

> 📘 Completed as part of the **QBUS6810 Predictive Analytics** course at the University of Sydney (Semester 2, 2023).

---

## 📌 Project Overview

With a 25% year-over-year surge in Airbnb listings (2022–2023), optimizing nightly prices has become a challenge for hosts. This project aims to:

- Identify influential features for Airbnb pricing
- Engineer meaningful predictors from text, location, and numerical variables
- Evaluate three predictive models: ElasticNet, Decision Tree, and XGBoost

---

## 🧠 Techniques & Methodologies

### 🔍 Feature Engineering
- Text mining from `description`, `amenities`, and `neighborhood_overview`
- Geographical distance to city CBDs using lat/long
- Outlier removal and logarithmic transformation for skewed features
- Ordinal encoding for review ratings and category simplification

### 🤖 Models Applied
| Model         | Train RMSE | Validation RMSE |
|---------------|------------|-----------------|
| ElasticNet    | 144.92     | 145.19          |
| Decision Tree | 137.63     | 142.96          |
| XGBoost       | **52.16**  | **123.61**      |

**🏆 Final Model**: `XGBoost`  
**🎯 Top Predictors**: `bedrooms`, `neighborhood_quality`, `CBD_distance`, and `text_keywords`

---

## 💻 Tech Stack

- **Language**: Python 3.8+
- **Tools**: Jupyter Notebook, pandas, NumPy, Scikit-learn, XGBoost, Matplotlib, Seaborn
- **Environment**: Anaconda / JupyterLab

---

## 🧑‍🤝‍🧑 Team Contribution

This project was developed collaboratively by a team of five:

- 🔹 All team members contributed to **EDA**, modeling, and report writing  
- 🔸 **Muzhao Li** was responsible for:
  - Exploratory Data Analysis (EDA)
  - Final code integration and notebook compilation
- Other contributions:
  - Text feature engineering
  - Model tuning and validation
  - Kaggle competition submissions and methodology writing

## 📎 References

- Airbnb growth data: Khandelwal, R. (2023). *The State of Short-Term Rentals in Australia*.  
- [Scikit-learn documentation](https://scikit-learn.org/)
- [XGBoost documentation](https://xgboost.readthedocs.io/)
- Additional references and citations are available in the full [`report.pdf`](./Airbnb_report.pdf)
