# LaLiga 25/26 Prediction 🏆📊
Predicting the **LaLiga 2025/26 league table** (champion + relegation candidates) using **historical data** and **machine learning**.

This project uses the last ~11+ seasons of LaLiga team performance data to train a model and generate predictions/probabilities for the 2025/26 season.

---

## Repo Contents
- `data_scrapping.ipynb` → collects / prepares LaLiga data (scraping + cleaning)
- `laliga_data_analysis.ipynb` → analysis + feature engineering + model training + predictions
- `laliga_2014_2026.csv` → compiled dataset used for training and testing  
- `README.md` + `LICENSE` (MIT)

---

## Goal (Simple Explanation)
Think of this like teaching a model:

- **Input (features)**: stats like points per match, wins, goal difference, etc.
- **Output (target)**: whether a team becomes **champion** (1) or not (0)

The model learns patterns from older seasons and then predicts probabilities for the target season (2025/26).

---

## Dataset
File: `laliga_2014_2026.csv` (all the data were imported from wikipedia.

Each row represents a **team in a season**, with season-level summary stats.

Target column:
- `is_champion`  
  - `1` = champion
  - `0` = not champion

---

## Features Used (Model Inputs)
The model trains using:

- `pts_per_match` (points per match)
- `gd` (goal difference)
- `pld` (played matches)
- `w` (wins)
- `l` (losses)
- `estimated_final_pts` (estimated final points)

---

## Model
**Random Forest Classifier**
- `n_estimators = 200` (uses 200 decision trees)
- `random_state = 42` (same results every run)

Why Random Forest?
- Works well for structured data
- Handles non-linear patterns
- Usually strong performance without heavy tuning

---

## Workflow (What the notebook does)
1. Load dataset  
2. Select features  
3. Split data:
   - Train = all seasons except `2025-2026`
   - Test = only `2025-2026`
4. Train the model:
   - `model.fit(X_train, y_train)`
5. Evaluate model performance (training metrics):
   - Accuracy, ROC AUC, Log Loss
   - Classification report, Confusion matrix
6. Predict champion probability for 2025/26:
   - `predict_proba()` → probability for each team

---

## How to Run
### 1) Install dependencies
```bash
pip install pandas numpy scikit-learn matplotlib
