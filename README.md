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

### Distribution of predicted xG
<img width="859" height="545" alt="image" src="https://github.com/user-attachments/assets/0dfacc20-1d09-417e-99d9-90c43db293b7" />


---


## 🎯 Calibration
Predicted probabilities were calibrated using **isotonic regression**.

| Metric | Before | After |
|------|--------|-------|
| Mean xG | 0.0976 | 0.0991 |

Calibration significantly improved:
- Team-level xG totals
- Player-level aggregation reliability

### Calibration Curve Comparison
<img width="691" height="545" alt="image" src="https://github.com/user-attachments/assets/440f8347-64c1-451b-86c1-8159f24a166d" />

---

## 📊 Feature Importance (Random Forest)

| Feature | Importance |
|------|-----------|
| Shot angle | ~43% |
| Shot distance | ~42% |
| Body part | ~9% |
| Technique | ~6% |

**~85% of xG is explained by shot geometry**, aligning with modern football analytics literature.

Body Part & Technique (~15%): While factors like body part (e.g., headers typically having lower conversion rates than footed shots) and technique (volleys vs. normal shots) do refine the xG value, their impact is secondary to "where" the shot is taken from.

### Feature Importance
<img width="1018" height="545" alt="image" src="https://github.com/user-attachments/assets/e438b7c3-68be-46ba-bb99-83cebd9bd355" />



### Group Feature Importance
<img width="691" height="524" alt="image" src="https://github.com/user-attachments/assets/e1774b9d-b645-498c-baae-ac9c57e90b49" />

---

## 📈 Visualizations

<img width="2632" height="1753" alt="image" src="https://github.com/user-attachments/assets/87f7cf80-4208-4424-a8eb-354e622662d4" />


- xG heatmaps on a full pitch
- Team xG vs actual goals comparison
- Calibration (reliability) curves
- Feature importance plots

### xG Heatmap on Football Pitch
<img width="1010" height="699" alt="image" src="https://github.com/user-attachments/assets/f9e0a0a3-dbd6-4dcb-935e-7a4221900cf2" />


### Actual Goals vs Predicted xG per Team
<img width="1004" height="651" alt="image" src="https://github.com/user-attachments/assets/88c45f27-e71f-4f61-9bd1-f26bc2195211" />


Examples are available in the `figures/` directory.

---

## 🧠 Key Football Insights
- Shot location dominates chance quality
- Centrality (angle) is as important as proximity (distance)
- Headers and techniques refine but do not define xG
- xG is reliable in aggregate, not for individual shot prediction

### Top 20 Players: Actual Goals vs Predicted xG
<img width="1170" height="786" alt="image" src="https://github.com/user-attachments/assets/9973abf8-87a1-4c48-b1e2-0677678114a7" />


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
