# 🏦 Bank Telemarketing Campaign Effectiveness Analyzer

> **IBM Internship Capstone Project — AI & Data Science**
>
> **Author: Jasveer Singh**

[![Python](https://img.shields.io/badge/Python-3.10+-blue)](https://python.org)
[![Scikit-learn](https://img.shields.io/badge/scikit--learn-1.4+-orange)](https://scikit-learn.org)
[![Dataset](https://img.shields.io/badge/Dataset-UCI_Bank_Marketing-green)](https://archive.ics.uci.edu/ml/datasets/Bank+Marketing)

---

## 📌 Project Overview

This project analyses the **direct marketing campaigns** of a Portuguese banking institution conducted via telephone calls. The goal is to determine which clients are likely to subscribe to a **bank term deposit**, helping analyse campaign effectiveness, customer response patterns and predictive factors.

The project follows a **4-Tier Analytics Pipeline**:

**Descriptive → Diagnostic → Predictive → Prescriptive**

The submitted implementation is provided as a Jupyter Notebook and is designed for reproducible data analysis and machine learning.

> **Source attribution:** This repository is an adapted and independently structured implementation based on the public project **Bank Telemarketing Campaign Effectiveness Analyzer** by Sanket Kale. The source project is acknowledged to distinguish the original public work from this submission by Jasveer Singh.

---

## 🎯 Problem Statement

A Portuguese bank runs telephone marketing campaigns to sell term-deposit products. Each campaign involves multiple calls per client, which can create significant marketing cost.

The analysis addresses three main questions:

1. Which client profiles and campaign conditions are associated with subscriptions?
2. Can subscription probability be predicted before a new call?
3. How can campaign analysis support more efficient targeting and contact strategies?

---

## 🧭 Objectives

1. **Descriptive Analytics** — Summarise historical campaign outcomes.
2. **Diagnostic Analytics** — Identify important factors associated with subscription behaviour.
3. **Predictive Analytics** — Train a machine-learning model to estimate subscription probability.
4. **Prescriptive Analytics** — Translate analytical patterns into data-driven campaign recommendations.

---

## 📊 Dataset Description

| Attribute | Value |
|---|---|
| Source | UCI Machine Learning Repository |
| Citation | Moro et al. (2014), *A Data-Driven Approach to Predict the Success of Bank Telemarketing* |
| File Used | `bank-additional-full.csv` |
| Raw Records | 41,188 |
| Clean Records | 41,176 |
| Duplicate Rows Removed | 12 |
| Features | 21 (20 input + 1 target) |
| Target Variable | `y` — term-deposit subscription (yes/no) |
| Subscription Rate | 11.27% (4,639 subscriptions) |
| Time Period | May 2008 – November 2010 |
| Missing Values | No explicit missing values; unknown categories are represented as `unknown` |

### Feature Groups

**Client Data**

`age`, `job`, `marital`, `education`, `default`, `housing`, `loan`

**Campaign Contact**

`contact`, `month`, `day_of_week`, `duration`, `campaign`, `pdays`, `previous`, `poutcome`

**Social / Economic Context**

`emp.var.rate`, `cons.price.idx`, `cons.conf.idx`, `euribor3m`, `nr.employed`

---

## 🛠️ Technologies Used

| Library / Technology | Purpose |
|---|---|
| Python 3.10+ | Primary programming language |
| Pandas | Data loading, cleaning, manipulation and aggregation |
| NumPy | Numerical computation |
| Scikit-learn | Random Forest machine learning and evaluation |
| Plotly | Interactive visualisations |
| Jupyter Notebook | Reproducible project workflow |

---

## 📁 Project Structure

```
Bank-Telemarketing-Campaign-Effectiveness-Analyzer/
├── Jasveer Singh_Bank Telemarketing Campaign Effectiveness Analyzer.ipynb
├── Jasveer Singh_ProjectReport.docx
├── README.md
└── requirements.txt
```

The notebook contains the analysis, preprocessing, visualisation and machine-learning workflow. The UCI dataset can be downloaded automatically when the notebook is executed, so a large CSV file does not need to be committed to GitHub.

---

## 🔄 Data Preprocessing

| Step | Action |
|---|---|
| Duplicate removal | 12 exact duplicate rows removed (41,188 → 41,176) |
| Column renaming | Selected dotted column names converted to Python-friendly names |
| Target encoding | `y` → `y_binary` (1 = subscribed, 0 = not subscribed) |
| Unknown handling | Unknown categorical values handled and imputed using the column mode |
| `pdays = 999` | Treated as no previous contact |
| Feature flag | `was_contacted_before` created from previous-contact information |
| Education ordinal | Education mapped to an ordinal scale |
| Feature engineering | `call_duration_min` created for diagnostic analysis |
| Ordered categoricals | `month` and `day_of_week` kept in logical order |

---

## 📈 Analytics Methodology

### 📋 Tier 1: Descriptive Analytics

The project examines:

- Subscription outcome distribution
- Monthly contact volume and subscription rate
- Subscription rate by job
- Subscription patterns by customer characteristics
- Contact-method distribution
- Day-of-week and campaign patterns

### 🔬 Tier 2: Diagnostic Analytics

The project examines:

- Call duration and subscription relationship
- Previous campaign outcome
- Economic indicators such as Euribor and employment variation
- Loan and credit-default information
- Campaign contact frequency
- Historical patterns associated with subscription behaviour

### 🤖 Tier 3: Predictive Analytics

**Algorithm:** Random Forest Classifier

- `n_estimators = 200`
- `max_depth = 12`
- `class_weight = "balanced"`
- Train/test split: 80% / 20%
- Stratified split
- Random state: 42
- Call `duration` excluded from the pre-call model to reduce target leakage
- Categorical variables are one-hot encoded

The notebook calculates:

- Accuracy
- F1 Score
- ROC-AUC
- Average Precision
- Classification report
- Confusion matrix
- ROC curve
- Feature importance

### 💡 Tier 4: Prescriptive Analytics

The analytical findings can support:

- Customer segment analysis
- Campaign timing analysis
- Contact-frequency strategy
- Economic-condition monitoring
- Targeting and prioritisation recommendations

---

## 📊 Model Results

The source project reported the following results for its Random Forest implementation:

| Metric | Reported Value |
|---|---:|
| ROC-AUC | 0.8131 |
| F1 Score | 0.4979 |
| Average Precision | 0.4875 |
| Accuracy | 85.38% |

**Important:** these are the reported results of the acknowledged source implementation. The Jasveer Singh notebook recalculates its own metrics when executed against the dataset rather than hard-coding these values.

---

## 🔑 Key Findings

The source analysis reported the following historical patterns:

1. **11.27%** of contacted clients subscribed (4,639 / 41,176 clean records).
2. **Call duration** was reported as the strongest predictor in the source analysis; subscribers averaged about 9.22 minutes versus 3.68 minutes for non-subscribers.
3. Clients with a previous successful campaign outcome had a reported conversion rate of **65.11%**, compared with **8.83%** for never-contacted clients.
4. Cellular contact had a reported subscription rate of **14.74%**, compared with **5.23%** for telephone contact.
5. The source analysis reported higher subscription rates for students (**31.43%**) and retirees (**25.26%**) among job segments.
6. The source analysis reported a **24.46%** subscription rate when Euribor was ≤ 2%, compared with **4.84%** when Euribor was > 4%.
7. The source analysis reported diminishing response after repeated contacts, with the rate decreasing from **13.04%** at one contact to **7.5%** at five contacts.
8. March was reported as having the highest monthly subscription rate at **50.55%**.

These are historical dataset observations, not guarantees of future campaign performance.

---

## ✅ Business Recommendations

Based on the historical analysis:

1. Prioritise clients with prior successful campaign history.
2. Compare contact channels using historical response rates.
3. Monitor repeated-contact frequency for diminishing returns.
4. Consider economic conditions when interpreting campaign results.
5. Examine high-response months while validating results on current data.
6. Consider tailored messaging for customer segments with higher historical response.
7. Use predictive scoring as decision support rather than as an automatic decision-maker.

---

## 📥 Dataset

The application analysis uses the **UCI Bank Marketing `bank-additional-full.csv`** dataset (Moro et al., 2014).

The notebook can download the official UCI archive automatically:

`https://archive.ics.uci.edu/static/public/222/bank+marketing.zip`

The archive contains the required `bank-additional-full.csv` file.

No large dataset file is required to be committed to this GitHub repository.

---

## 🚀 Installation & Setup

### Prerequisites

- Python 3.10 or higher
- pip
- Jupyter Notebook / JupyterLab

### 1. Clone the Repository

```bash
git clone https://github.com/rathore28jasveer-wq/Bank-Telemarketing-Campaign-Effectiveness-Analyzer.git
cd Bank-Telemarketing-Campaign-Effectiveness-Analyzer
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Open the Notebook

```bash
jupyter notebook
```

Then open:

```
Jasveer Singh_Bank Telemarketing Campaign Effectiveness Analyzer.ipynb
```

### 4. Run the Notebook

Run the cells from top to bottom. The notebook loads the UCI dataset, performs preprocessing, generates visualisations and trains the Random Forest model.

---

## 💻 Notebook Workflow

1. **Project Overview** — Project scope and attribution
2. **Imports and Configuration** — Python libraries and random-state configuration
3. **Dataset Loading** — UCI Bank Marketing data
4. **Data Cleaning and Preprocessing** — Duplicate removal, encoding and feature engineering
5. **Descriptive Analytics** — Outcome and segment analysis
6. **Diagnostic Analytics** — Campaign and historical relationship analysis
7. **Predictive Analytics** — Random Forest model
8. **Model Evaluation** — Classification metrics, ROC curve and confusion matrix
9. **Feature Importance** — Important predictive variables
10. **Business Insights** — Interpretation and limitations
11. **References and Attribution** — Dataset and source-project references

---

## 🔮 Future Improvements

1. Integrate a real-time client database for live scoring.
2. Add SHAP explainability for individual predictions.
3. Explore XGBoost or LightGBM for model comparison.
4. Add A/B testing analysis for campaign variants.
5. Add time-series analysis of subscription trends.
6. Add geographic segmentation if regional data becomes available.
7. Deploy the analytical workflow as an interactive Streamlit application.

---

## 📚 Citation

> S. Moro, P. Cortez and P. Rita.  
> *A Data-Driven Approach to Predict the Success of Bank Telemarketing.*  
> Decision Support Systems, 2014.  
> http://dx.doi.org/10.1016/j.dss.2014.03.001

---

## 👤 Author

**Jasveer Singh**

**IBM Internship Project**  
AI and Data Science / Data Analytics

---

*This repository is intended as an academic/internship project. Analysis should be validated on appropriate current data before operational use.*
