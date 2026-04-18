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

<img width="2932" height="1512" alt="image" src="https://github.com/user-attachments/assets/38ea4208-795c-4aae-b4dd-f249d23e16ea" />


<img width="1466" height="623" alt="image" src="https://github.com/user-attachments/assets/f301458a-92ae-4241-b30d-6271cd5304f8" />






| Metric | Before | After |
|------|--------|-------|
| Mean xG | 0.0976 | 0.0991 |

Calibration significantly improved:
- Team-level xG totals
- Player-level aggregation reliability

### Calibration Curve Comparison
<img width="1399" height="919" alt="image" src="https://github.com/user-attachments/assets/dfaf1364-1019-4c6f-9632-7f058d79c73a" />



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
<img width="1166" height="666" alt="image" src="https://github.com/user-attachments/assets/3785c189-deee-444b-88f3-6be427141b01" />


<img width="1366" height="966" alt="image" src="https://github.com/user-attachments/assets/e457f692-7f4d-4ef7-b77c-83b1376a9b58" />




<img width="1466" height="605" alt="image" src="https://github.com/user-attachments/assets/85f8c805-eaf2-48d3-8ebc-bcc878c76211" />



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

<img width="2332" height="1584" alt="image" src="https://github.com/user-attachments/assets/4f99c803-54dc-4490-b2cc-6d5e6ae026ff" />


### Actual Goals vs Predicted xG per Team
<img width="1166" height="966" alt="image" src="https://github.com/user-attachments/assets/a69fab08-6df1-4fe9-9ab0-ae2bf77bd9cd" />



Examples are available in the `figures/` directory.

---

## 🧠 Key Football Insights
- Shot location dominates chance quality
- Centrality (angle) is as important as proximity (distance)
- Headers and techniques refine but do not define xG
- xG is reliable in aggregate, not for individual shot prediction

### Top 20 Players: Actual Goals vs Predicted xG
<img width="1167" height="966" alt="image" src="https://github.com/user-attachments/assets/303b65fb-6535-4436-bd3b-cf4d6210c686" />



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
