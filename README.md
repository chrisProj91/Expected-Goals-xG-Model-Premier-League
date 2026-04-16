# Expected-Goals-xG-Model-Premier-League
A machine learning project that builds an Expected Goals (xG) model using StatsBomb event data. Includes feature engineering (distance, angle), logistic regression modeling, and visualizations such as xG heatmaps and player/team comparisons.


# Expected Goals (xG) Modeling with StatsBomb Open Data

## 📌 Project Overview
This project builds an end-to-end **Expected Goals (xG) modeling pipeline** using
**StatsBomb Open Data**, focusing on the **2015/16 Premier League season**.

The objective is to:
- Model shot-level goal probability (xG)
- Compare multiple ML approaches
- Calibrate predictions
- Produce team- and player-level xG analytics
- Visualize spatial shot quality on the pitch

This project is designed as a **portfolio-quality football analytics case study**.

---

## 🗂 Data
- **Source:** StatsBomb Open Data
- **Competition:** Premier League
- **Season:** 2015/16
- **Matches:** 380
- **Shots:** 9,908

Only event-level data available publicly was used.

---

## 🛠 Feature Engineering
Core features:
- Shot distance to goal
- Shot angle
- Body part (foot, head)
- Shot technique (volley, header, lob, etc.)

Target variable:
- `goal` (binary outcome)

---

## 🤖 Models Implemented

| Model               | ROC-AUC |
|--------------------|--------|
| Logistic Regression | 0.773  |
| Random Forest       | 0.764  |
| XGBoost             | 0.738  |

- Random Forest showed the best balance of discrimination and calibration.
- Severe class imbalance (goals ≈ 10%) handled via probability-based evaluation.

---

## 🎯 Calibration
Predicted probabilities were calibrated using **isotonic regression**.

| Metric | Before | After |
|------|--------|-------|
| Mean xG | 0.0976 | 0.0991 |

Calibration significantly improved:
- Team-level xG totals
- Player-level aggregation reliability

---

## 📊 Feature Importance (Random Forest)

| Feature | Importance |
|------|-----------|
| Shot angle | ~43% |
| Shot distance | ~42% |
| Body part | ~9% |
| Technique | ~6% |

**~85% of xG is explained by shot geometry**, aligning with modern football analytics literature.

---

## 📈 Visualizations
- xG heatmaps on a full pitch
- Team xG vs actual goals comparison
- Calibration (reliability) curves
- Feature importance plots

Examples are available in the `figures/` directory.

---

## 🧠 Key Football Insights
- Shot location dominates chance quality
- Centrality (angle) is as important as proximity (distance)
- Headers and techniques refine but do not define xG
- xG is reliable in aggregate, not for individual shot prediction

---

## 🚀 Tools & Libraries
- Python
- statsbombpy
- pandas, numpy
- scikit-learn
- xgboost
- matplotlib, seaborn

---

## 📌 Disclaimer
This project uses **public StatsBomb Open Data** and is for educational and portfolio purposes only.

---
