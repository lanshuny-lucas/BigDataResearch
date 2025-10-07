# Credit Risk Management using Machine Learning

## 📌 Project Overview
This project focuses on **credit risk prediction** by identifying customers likely to default on their credit card payments. With the increasing competition among issuers and rising default risks, the goal is to build predictive models that help banks minimize credit losses while maintaining growth.

The dataset contains demographic, behavioral, and financial variables such as **credit limit, repayment history, billing statements, and payment amounts**, enabling robust modeling of borrower risk profiles.

---

## 🗂 Dataset
- **Source**: Provided coursework dataset (`group_3_modified.csv`)
- **Size**: 30,000 credit card clients
- **Key Variables**:
  - **Demographics**: Age, Gender, Education, Marriage
  - **Credit Information**: Credit limit, repayment history (PAY_1–PAY_6)
  - **Financial Records**: Bill amounts (BILL_AMT1–BILL_AMT6), Payment amounts (PAY_AMT1–PAY_AMT6)
- **Target**: Default payment (binary: 1 = default, 0 = non-default)

---

## 🔎 Data Exploration
- Average client age: ~35 years  
- Average credit limit: 167,130 (heavily right-skewed)  
- Repayment history mostly shows timely payments (majority values = 0)  
- All financial variables are **right-skewed**  
- No missing values, making dataset reliable for modeling  

---

## ⚙️ Methodology

### 1. **Data Preprocessing**
- Removed outliers (invalid education/marriage values)
- Applied **Isolation Forest** for advanced anomaly detection
- Standardized variables for fair comparison

### 2. **Models Implemented**
- **Logistic Regression**
  - Stepwise selection, multicollinearity check
  - Regularized with **LASSO (L1 penalty)**
- **Random Forest**
  - Created new engineered features:
    - Credit Utilization (Bill/Credit Limit)
    - Payout Ratio Type
    - Bill & Payment Volatility
  - Tuned hyperparameters (100 trees, max depth=10, min samples/leaf=10)
- **Naïve Bayes**
  - Created new features: Default Count, Activity Frequency, Credit Balance Type
  - Applied PCA for dimensionality reduction (increased accuracy but raised false positives, so excluded)

---

## 📊 Model Evaluation

| Model              | AUC   | F1    | False Positive Rate |
|--------------------|-------|-------|---------------------|
| Logistic Regression | ~0.78 | High  | <50% (poor specificity) |
| Random Forest       | 0.785 | 0.80  | <50% (poor specificity) |
| Naïve Bayes         | 0.754 | 0.78  | **59% (better balance)** |

- **Random Forest** had the best AUC/F1 but suffered from higher false positives.
- **Naïve Bayes** achieved the most balanced performance and was selected as the **final model**.

---

## ✅ Conclusion & Recommendations
- **Winning Model**: **Naïve Bayes** (best trade-off between sensitivity and specificity)
- **Business Value**: Helps banks avoid granting credit to high-risk customers while maintaining stable growth.
- **Limitations**: Dataset lacked income, loan history, and longer time span. Future work should integrate richer financial attributes for stronger predictive power.

---

## 🛠 Tech Stack
- **Languages**: Python (Pandas, NumPy, Scikit-learn)
- **Techniques**: Outlier detection, Feature engineering, Logistic Regression, Random Forest, Naïve Bayes, PCA
- **Tools**: Jupyter Notebook, Orange3 (for workflow automation), Excel

---

## 📂 Repository Structure
```
├── data/
│   └── group_3_modified.csv      # Dataset
├── report/
│   └── IDS Coursework_group3.pdf # Full project report
├── notebooks/
│   └── model_building.ipynb      # Code for preprocessing & modeling
└── README.md
```

---

✨ *This project demonstrates applied data science for financial risk management, with a focus on feature engineering, model selection, and practical business implications.*  
