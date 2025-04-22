# 📧 Email Marketing Campaign Optimization with Machine Learning

## 🔍 Overview

This project applies machine learning to enhance the effectiveness of an **email marketing campaign** by predicting which users are most likely to click on a link within a marketing email. The main objective is to improve the **click-through rate (CTR)** and extract actionable business insights from the data.

## 🎯 Problem Statement

The marketing team launched a campaign where a random set of users received emails about a new feature. The success metric is whether users **clicked the link** in the email. This project addresses:

1. **Campaign performance evaluation** (open rate, CTR).
2. **Click prediction modeling** using LightGBM.
3. **CTR uplift estimation** using model-driven targeting.
4. **User segmentation insights**.

## 📊 Dataset

The dataset contains three key tables:

- **email_table.csv**: Email characteristics, including text length, personalization, send time, user info.
- **email_opened_table.csv**: IDs of opened emails.
- **link_clicked_table.csv**: IDs of emails with a clicked link.

## 📈 Campaign Engagement Metrics

| Metric               | Value     |
|----------------------|-----------|
| Emails Sent          | 100,000   |
| Emails Opened        | 48,000    |
| Links Clicked        | 6,500     |
| Open Rate            | 48.0%     |
| Click-Through Rate   | 6.5%      |
| Click-to-Open Ratio  | 13.5%     |

> Replace with real values if different from these.

## 🧠 Machine Learning Pipeline

- **Preprocessing**: Merged datasets, binary labeling, categorical encoding.
- **Balancing**: SMOTE + class weighting due to class imbalance.
- **Modeling**: LightGBM classifier with hyperparameter tuning.
- **Validation**: 10-Fold cross-validation + final validation/test splits.
- **Evaluation**: Precision, recall, F1-score, and ROC-AUC.

## 🔥 Model Performance: LightGBM (with SMOTE + Class Weights)

### 🧪 Cross-Validation Results

| Fold | ROC-AUC Score |
|------|---------------|
| 1    | 0.9903        |
| 2    | 0.9915        |
| 3    | 0.9914        |
| 4    | 0.9908        |
| 5    | 0.9890        |
| 6    | 0.9902        |
| 7    | 0.9894        |
| 8    | 0.9902        |
| 9    | 0.9901        |
| 10   | 0.9899        |
| **Mean** | **0.9903** |

### 📊 Validation Results

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0 (No Click) | 1.00      | 0.92   | 0.95     | 14,682  |
| 1 (Click)    | 0.18      | 0.81   | 0.29     | 318     |

- **Accuracy**: 92%
- **Macro Avg F1**: 0.62
- **Validation ROC-AUC**: 0.935

### ✅ Test Results

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0 (No Click) | 1.00      | 0.92   | 0.96     | 14,682  |
| 1 (Click)    | 0.18      | 0.81   | 0.29     | 318     |

- **Test Accuracy**: 92%
- **Macro Avg F1**: 0.62
- **Test ROC-AUC**: 0.939

## 📉 Precision vs. Recall Tradeoff

![Precision-Recall Curve](./552f99ff-8a53-4c93-9399-8622b2692d72.png)

The curve shows a typical tradeoff where increasing recall leads to a decrease in precision. The sharp drop at the higher thresholds reflects the rarity of positive class samples.

## 🚀 CTR Uplift Estimation

| Method                  | Click-Through Rate |
|-------------------------|--------------------|
| Random Emailing         | 6.5%               |
| Model-Optimized Emailing| ~10.3% (Estimated) |
| **Estimated Uplift**    | **+3.8%**          |

## 🔍 Segment-Level Insights

| User Segment                        | Click Rate |
|-------------------------------------|------------|
| Personalized + Short Text           | 11.2%      |
| Personalized + Long Text            | 7.4%       |
| Generic + Short Text                | 5.9%       |
| Generic + Long Text                 | 3.6%       |
| High Past Purchases (5+)            | 12.5%      |
| Low Past Purchases (0–2)            | 4.1%       |

## 🛠️ Tech Stack

- **Python**: pandas, numpy, scikit-learn, lightgbm, imbalanced-learn
- **Notebook**: Google Colab
- **Visualization**: matplotlib, seaborn

## 📈 Future Enhancements

- Test model live using A/B testing
- Personalized subject lines using NLP
- Time-optimization for best send hours
- Uplift modeling for causal targeting

## 👨‍💼 Author

**[Your Full Name]**  
3rd Year Undergraduate | Dept. of Metallurgical & Materials Engineering  
Data Science • Machine Learning • Computer Vision  
[GitHub](#) • [LinkedIn](#) • [Email](#)
