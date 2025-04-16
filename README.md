# 📧 Email Marketing Campaign Optimization - Quantaucs.ai Assignment

This project is part of a machine learning internship focused on analyzing and optimizing an email marketing campaign using predictive modeling techniques.

---

## 🧠 Objective

The goal of this case study is to:
- Evaluate the performance of an email campaign.
- Build a machine learning model to **optimize email delivery** to maximize user **click-through rate (CTR)**.
- Uncover patterns across user segments that influence email interaction (open/click behavior).

---

## 📂 Dataset Description

The data is composed of three tables merged into a single dataset for analysis and modeling:

### 1. `email_table.csv`
Contains metadata about emails sent:
- `email_id`: Unique ID for each email
- `email_text`: Type of email content - `short_email` or `long_email`
- `email_version`: `personalized` or `generic`
- `hour`: Time when the email was sent
- `weekday`: Day of the week when the email was sent
- `user_country`: Country of the user
- `user_past_purchases`: Number of past purchases by the user

### 2. `email_opened_table.csv`
Contains IDs of emails that were opened.

### 3. `link_clicked_table.csv`
Contains IDs of emails whose embedded link was clicked.

---

## 📊 Key Metrics

- **Open Rate** = (Number of emails opened / Total emails sent)
- **Click-Through Rate (CTR)** = (Number of emails clicked / Total emails sent)
- **Click-to-Open Rate (CTOR)** = (Number of emails clicked / Number of emails opened)

---

## 🧪 Exploratory Data Analysis (EDA)

- Analyzed click and open rates by:
  - User past purchase history
  - Email content (`short` vs `long`)
  - Personalization
  - Hour and weekday
  - Country

### 📈 Insightful Findings:
- Users with higher past purchases tend to click more.
- Personalized emails had a slightly better CTR.
- Certain hours (like midday) and weekdays (e.g., Tuesday, Wednesday) showed better user interaction.

---

## 🔍 Feature Engineering

- One-hot encoding for categorical features: `email_text`, `email_version`, `weekday`, `user_country`
- Bucketed user purchase history into categorical bins (`purchase_bucket`)
- Created `opened`, `clicked` as target labels for respective models

---

## 🧠 Modeling

Three classification models were trained and evaluated:
1. **Logistic Regression**
2. **Random Forest**
3. **XGBoost**

The primary objective was to **predict whether an email would be clicked**.

### 🎯 Evaluation Metric:
- **ROC-AUC Score**
- **F1-Score**
- **Confusion Matrix**

### 📊 Model Performance Summary

| Model              | ROC-AUC (CV) | Final ROC-AUC | Recall (Class 1) |
|--------------------|--------------|----------------|------------------|
| Logistic Regression | 0.956        | 0.957          | 0.02 → improved to 0.05 after tuning |
| Random Forest       | 0.954        | 0.955          | 0.01             |
| XGBoost             | **0.957**    | **0.958**      | **0.05**         |

> XGBoost performed the best post-tuning, but Logistic Regression also performed strongly and is more interpretable.

---

## 🛠️ Hyperparameter Tuning

Performed GridSearchCV for all three models using `StratifiedKFold` with ROC-AUC as the scoring metric.

---

## 📌 Strategy & Recommendations

- **Target users with higher past purchases** using personalized emails.
- **Send during optimal time windows**, especially weekdays like Tuesday and hours like 12PM–3PM.
- Consider A/B testing future campaigns to validate model suggestions.
- Deploy the logistic regression model for simplicity and interpretability in production, unless you need higher performance (then go with XGBoost).

---

## 📦 Artifacts

- `logistic_model_ctr.pkl`
- `rf_model_ctr.pkl`
- `xgb_model_ctr.pkl`
- Feature importance plots and model comparison visualizations included in the repo.

---

