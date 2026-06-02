---
layout: default
---

# German Credit Risk Modeling

This project develops an interpretable credit risk classification workflow using the German Credit dataset. It combines exploratory data analysis, Weight of Evidence (WoE) encoding, logistic regression and cost-sensitive decisioning.

## Project Overview

This portfolio project demonstrates an end-to-end data science workflow for credit risk classification. It focuses on building a transparent, regulatory-friendly model using techniques commonly applied in real-world banking environments.

## Business Problem

In retail lending, predicting credit risk determines whether to approve or reject loan applications. However, misclassification errors have asymmetric costs:

- **False Positive**: Rejecting a creditworthy applicant — the bank loses potential revenue and may damage customer relationships.
- **False Negative**: Approving a high-risk applicant — the bank faces potential default losses, which can be substantially higher.

Using accuracy alone to evaluate or tune a credit model can lead to suboptimal business decisions when these costs are not considered.

## Dataset

The project uses the corrected South German Credit dataset (available from UCI ML Repository). This dataset addresses known inconsistencies in the original German Credit dataset.

**Key feature groups:**
- Loan characteristics: amount, duration, purpose
- Financial status: savings, checking account
- Personal attributes: age, employment, housing
- Credit history information

The dataset contains 1,000 records with 20 features describing loan applicants and their repayment behavior (good/bad credit risk).

## Methodology

1. Exploratory data analysis to understand feature distributions and risk patterns
2. Weight of Evidence (WoE) encoding for categorical variables
3. Logistic regression modeling with interpretability focus
4. Cost-sensitive threshold optimization for business alignment

## Exploratory Data Analysis

The analysis examines univariate and bivariate relationships between features and credit risk outcome. Key insights identify which customer attributes are most predictive of default behavior.

<!-- Future plots can be added here:
![Feature Overview](assets/feature_overview.png)
-->

## WoE Encoding and Logistic Regression

Weight of Evidence (WoE) encoding transforms categorical variables into a numeric format suitable for logistic regression while preserving interpretability. This approach is commonly used in scorecard development because:

- Each category receives a meaningful numeric score
- The resulting model resembles traditional credit scorecards
- Feature contributions to risk are transparent and explainable

Logistic regression was chosen as the modeling approach because it is:

- Widely used and accepted in regulated banking environments
- Interpretable — each feature’s impact on risk can be quantified
- Compatible with WoE encoding for scorecard-style implementations

## Model Evaluation

Performance is evaluated using ROC-AUC and accuracy on a hold-out test set. The model achieves reasonable discriminative power while maintaining interpretability.

<!-- Future plots can be added here:
![ROC Curve](assets/roc_curve.png)
-->

## Cost-sensitive Threshold Selection

Instead of using the default 0.5 classification threshold, the model is tuned to minimize total portfolio cost under asymmetric misclassification costs (false negatives weighted higher than false positives). This approach:

- Compares decision thresholds under different cost scenarios
- Selects the threshold that minimizes business risk cost
- Demonstrates that threshold optimization can yield significant savings relative to naive accuracy-based decisions

<!-- Future plots can be added here:
![Cost Curve](assets/cost_curve.png)
![Confusion Matrix](assets/confusion_matrix.png)
-->

## Key Findings

- WoE-encoded logistic regression provides a transparent modeling approach suitable for regulated environments
- Threshold optimization under asymmetric costs significantly reduces total portfolio risk
- Key risk drivers include checking account status, credit history, and savings status (identified via Information Value)

## Limitations

This is an educational portfolio project, not a production credit approval system:

- The German Credit dataset is small (1,000 records) and historical
- Features are simplified representations of real-world borrower characteristics
- No external validation or stress testing has been performed
- Regulatory compliance, fairness, and monitoring would be required for production use

## Tech Stack

- Python, Pandas, NumPy
- scikit-learn (Logistic Regression, metrics)
- Matplotlib, Seaborn
- Jupyter Notebook

## Repository Structure

```
.
├── README.md           # Technical documentation
├── docs/               # GitHub Pages site
│   └── index.md
├── notebooks/          # Main analysis notebook
├── src/                # Python modules for data processing
└── data/               # Raw dataset and code tables
```

## How to Run

Clone the repository and install dependencies:

```bash
pip install -r requirements.txt
```

Run the analysis notebook:

```bash
jupyter notebook notebooks/German_Credit_Data_Analysis.ipynb
```

