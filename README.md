# Heart Attack Risk Analysis

A data analytics and machine learning project to predict heart attack risk based on clinical and lifestyle factors.

---

## Problem Statement

Heart disease remains one of the leading causes of death globally. This project aims to identify which clinical and lifestyle factors are most associated with heart attack risk, and to build a predictive model that can classify a patient's risk level based on those features.

---

## Dataset

- **Source:** Heart Attack Dataset (CSV)
- **Size:** 7,000 patient records
- **Features:** 21 features covering clinical data (age, resting BP, cholesterol, ECG results, etc.) and lifestyle data (smoking status, alcohol consumption, physical activity, stress level, etc.)
- **Target:** `heart_attack_risk` (binary: 0 = low risk, 1 = high risk)
- **Class distribution:** ~58% low risk, ~42% high risk

---

## Workflow

1. Data loading and exploration
2. Data cleaning (handling missing values via median/mode imputation)
3. Exploratory Data Analysis (EDA) — numeric and categorical features vs risk
4. Feature engineering and preprocessing (one-hot encoding, standardization)
5. Model training — Logistic Regression and Random Forest
6. Model evaluation and comparison

---

## Key EDA Findings

- **Age** and **max heart rate** are the two strongest numeric predictors. High-risk patients tend to be older and have lower maximum heart rates.
- **Max heart rate** has the highest magnitude correlation with risk at -0.32, meaning lower max heart rate is associated with higher risk.
- **Smoking status** shows a clear gradient: current smokers have the highest risk rate (~52%), followed by former smokers (~43%), and non-smokers (~36%).
- **Clinical categorical features** such as `chest_pain_type` (Typical Angina ~50% risk rate), `st_slope` (Down ~51%), and `thalassemia` (Reversible Defect ~49%) separate risk better than lifestyle features.
- **Gender, resting ECG, and alcohol consumption** showed weak or nearly flat signal across categories and are not strong standalone predictors in this dataset.

---

## Model Results

| Model               | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
| ------------------- | -------- | --------- | ------ | -------- | ------- |
| Logistic Regression | 0.780    | 0.745     | 0.720  | 0.732    | 0.871   |
| Random Forest       | 0.761    | 0.744     | 0.651  | 0.695    | 0.847   |

**Winner: Logistic Regression** — performs better across all metrics, particularly in Recall (0.720 vs 0.651) and ROC-AUC (0.871 vs 0.847). A higher recall is important in a medical context because it means fewer high-risk patients are missed.

---

## Feature Importance

**Logistic Regression (top positive risk drivers):**

- `chest_pain_type_Typical Angina`
- `num_major_vessels`
- `physical_activity_Low`
- `oldpeak`
- `diabetes` and `family_history`

**Random Forest (top features by importance):**

- `age`
- `max_heart_rate`
- `oldpeak`
- `cholesterol`
- `resting_bp`

Both models agree that age, max heart rate, and oldpeak are among the most important features, which is consistent with the EDA findings.

---

## Limitations

- Missing values were imputed using median and mode, not actual patient data
- No hyperparameter tuning was performed
- Models were evaluated on a single train/test split, not cross-validated
- Dataset source and collection method are not fully documented

---

## Tech Stack

- Python (Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn)
- Jupyter Notebook

---

## Author

**Alif Fajrul Caesar Ifmaini**  
Information Systems Graduate — Tarumanagara University
