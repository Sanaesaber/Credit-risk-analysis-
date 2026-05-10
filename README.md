**README :**
```markdown
# 💳 Credit Risk & Loan Default Analysis

> End-to-end credit scoring system using XGBoost, SHAP explainability, and Power BI — replacing manual credit review with Basel III-compliant predictions.



![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)




![XGBoost](https://img.shields.io/badge/XGBoost-ML-orange)




![SQL](https://img.shields.io/badge/SQL-Exploration-336791?logo=postgresql)




![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)




![SHAP](https://img.shields.io/badge/SHAP-Explainability-green)



---

## 📊 Project Results

| Metric | Result |
|---|---|
| Loan Applications Analyzed | 32,581 |
| Default Rate | 22.1% |
| Model Accuracy | 93.8% |
| Recall (Defaulters) | 87.3% |
| F1-Score | 88.5% |
| ROC-AUC | **0.971** |

---

## 🧩 Business Context

A commercial bank needed to replace its manual credit review process with a data-driven system to assess borrower default risk. Traditional scoring relied on limited variables and failed to capture full borrower complexity. The institution required a system that accurately predicts defaults, explains decisions to loan officers, and complies with **Basel III** regulatory requirements.

---

## 🔬 Methodology

### 1. SQL-Based Exploration
Default rates analyzed by loan grade, interest rate tier, and borrower income level.

### 2. Preprocessing
| Step | Detail |
|---|---|
| Missing — interest rate | Grade-grouped median imputation (9.6% missing) |
| Missing — employment length | Overall median imputation (2.7% missing) |
| Outliers — annual income | Winsorization |
| Loan grade | Ordinal encoding A=1 through G=7 |

### 3. Feature Engineering
- **Debt-to-income ratio** — engineered to capture overall leverage
- **Loan purpose** — one-hot encoded to capture borrower intent risk

### 4. Class Imbalance — SMOTE
Applied on training set only (77.9 / 22.1 split) — test set kept clean.

### 5. Model Comparison
| Model | Accuracy | Recall | F1-Score | ROC-AUC |
|---|---|---|---|---|
| Logistic Regression | 84.2% | 64.8% | 67.9% | 0.892 |
| Random Forest | 91.4% | 79.1% | 82.5% | 0.954 |
| **XGBoost (Final)** | **93.8%** | **87.3%** | **88.5%** | **0.971** |

Tuned with GridSearchCV — 5-fold cross-validation optimizing for ROC-AUC.

### 6. SHAP Feature Importance
| Feature | Business Meaning |
|---|---|
| Loan Grade | Strongest single predictor of default |
| Interest Rate | High rate signals embedded risk |
| Loan-to-Income Ratio | Debt burden vs income |
| Prior Default on File | 2.3× higher re-default risk |
| Annual Income | Higher income = significantly lower default |
| Debt-to-Income Ratio | Engineered leverage indicator |

### 7. Power BI Dashboard
Three-page report: portfolio KPIs, segment analysis by grade and loan intent, individual borrower risk scoring.

---

## 💼 Business Impact

- **Grade G loans default at 14× the rate of Grade A** — loan grade must anchor any scoring model
- Model identifies **87 out of every 100 actual defaulters** before disbursement
- On a **$50M portfolio** → projected savings of **$2.1–2.8M annually**
- Strategic recommendations:
  - Restrict Grade F and G loans
  - Flag loan-to-income ratios above 40%
  - Enhanced due diligence on venture loans (31.6% default rate)

---

## 🗂️ Project Structure

credit-risk-analysis/
├── data/
│   └── loan_data.csv
├── sql/
│   └── credit_exploration.sql
├── notebooks/
│   ├── 01_EDA_and_SQL_Profiling.ipynb
│   ├── 02_Preprocessing_and_Feature_Engineering.ipynb
│   ├── 03_Modeling_and_Evaluation.ipynb
│   └── 04_SHAP_and_Business_Insights.ipynb
├── dashboard/
│   └── credit_risk_dashboard.pbix
├── requirements.txt
└── README.md


---

## 🛠️ Tech Stack

| Tool | Usage |
|---|---|
| Python | Core language |
| SQL | Default rate profiling and exploration |
| XGBoost | Final classification model |
| Scikit-learn | Pipeline, GridSearchCV, SMOTE |
| SHAP | Explainability and feature ranking |
| Power BI | Credit risk monitoring dashboard |
| Pandas / NumPy | Data manipulation |
| Matplotlib / Seaborn | Visualization |

---

## 🚀 Getting Started

```bash
git clone https://github.com/SanaeSaber/credit-risk-analysis.git
cd credit-risk-analysis
pip install -r requirements.txt
jupyter notebook

👤 Author
Sanae Saber — Data Analyst & Machine Learning Engineer
📧 sanaesaber03@gmail.com | 🔗 github.com/SanaeSaber
