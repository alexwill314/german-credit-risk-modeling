# German Credit Data – EDA & Regression Model

[Project website](https://alexwill314.github.io/german-credit-risk-modeling/)

## Overview

This project explores the **German Credit Dataset** using exploratory data analysis (EDA) to understand 
patterns in borrower characteristics and their relationship to credit risk.
Using the insights gained from the EDA, we construct a logistic regression model which uses Weight of Evidence (WoE)
Encoding for credit default classification. The model is tuned using an asymmetric cost method.
The analysis is framed in a banking context and focuses on interpretability and business relevance.

## Objective

- Explore structure and quality of credit data  
- Identify differences between good and bad credit risk profiles  
- Analyze relationships between customer features and credit outcomes  
- Derive simple, interpretable insights relevant to credit risk analysis 

## Dataset
The analysis uses the corrected South German Credit dataset to avoid known 
inconsistencies in the original UCI German Credit dataset.
A custom parser is used to transform the original codebook into a structured mapping table. 
This enables reproducible renaming and categorical decoding of the dataset.

Key feature groups include:
- Loan characteristics (amount, duration, purpose)  
- Financial status (savings, checking account status)  
- Personal attributes (age, employment, housing)  
- Credit history information


## Methodology

The analysis is structured into:

- Data overview (structure, types, missing values)  
- Univariate feature analysis
- Bivariate analysis vs. credit risk  
- Segment-based risk insights  
- Logistic Regression modeling with WoE encoding and asymmetric cost optimization

## Logistic Regression Model

After the exploratory analysis, a logistic regression model is trained to predict credit risk using **Weight of Evidence (WoE)** encoding for categorical features. This approach provides both predictive performance and full regulatory transparency — every prediction can be traced back to the underlying feature categories.

**Key modeling decisions:**
- The features used in modeling are the key drivers identified in EDA
- Features are encoded using WoE transformation before modeling
- All coefficients are negative, consistent with the WoE encoding direction

**Baseline model performance (default 0.5 threshold):**

| Metric       | Value  |
|--------------|--------|
| ROC-AUC      | 0.7292 |
| Gini         | 0.4583 |
| Accuracy     | 74%    |

**Feature importance (by Information Value):**

| Feature        | Coefficient (Beta) | IV       |
|----------------|-------------------|----------|
| status         | -0.8003           | 0.7190   |
| credit_history | -0.7808           | 0.3390   |
| savings        | -0.7856           | 0.2391   |
| duration_bin   | -0.5638           | 0.1839   |
| amount_bin     | -0.7038           | 0.1478   |
| property       | -0.7263           | 0.1267   |
| age_bin        | -0.6672           | 0.0988   |

### Business Value: Asymmetric Cost Optimization

In retail lending, false negatives (approving a bad borrower) are far more costly than false positives (rejecting a good borrower). Using an asymmetric cost matrix (FN cost = 5, FP cost = 1), the model's decision threshold is optimized to minimize total portfolio risk cost rather than raw accuracy.

**Results:**

| Strategy                    | Total Cost | Savings vs. Approve All |
|-----------------------------|------------|-------------------------|
| Approve All                 | 300        | —                       |
| Reject All                  | 140        | 53.34%                  |
| Default Threshold (0.50)    | 199        | 33.67%                  |
| **Optimized Threshold (0.11)** | **117**  | **61.00%**              |

The optimal threshold of **0.11** cuts risk costs by **41.21%** compared to the standard 0.50 threshold, demonstrating that aligning the decision boundary with business economics yields significantly higher value than technical model tuning alone.

## Tools

- Python  
- Pandas / numpy  
- Matplotlib / Seaborn  
- scipy  
- scikit-learn (Logistic Regression, metrics)  
- Jupyter Notebook  

## Note

This project is part of a portfolio to demonstrate structured data analysis skills in a credit risk context. It combines EDA with a transparent predictive model suitable for regulatory banking environments, focusing on interpretability and business-relevant insights rather than purely predictive modeling.