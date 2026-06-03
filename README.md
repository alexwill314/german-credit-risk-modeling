# South German Credit Data – EDA & Regression Model

This repository contains a data science portfolio project on credit risk classification using the German Credit dataset.

The project started with exploratory data analysis and was extended into an interpretable modeling workflow using Weight of Evidence encoding, logistic regression and cost-sensitive threshold selection.

[Project website](https://alexwill314.github.io/german-credit-risk-modeling/)

---

## Project Summary

The goal of this project is to build and evaluate an interpretable credit risk classification model.

In addition to standard model evaluation, the project considers asymmetric misclassification costs, since approving a risky applicant and rejecting a reliable applicant do not have the same business impact.

The project includes:

- data loading and preprocessing
- parsing and mapping of coded categorical variables
- exploratory data analysis
- Weight of Evidence encoding
- logistic regression modeling
- model evaluation
- cost-sensitive threshold analysis

## Repository Structure

```text
├── data/                 # Raw and/or processed data files
├── notebooks/            # Exploratory analysis and modeling notebooks
├── src/                  # Reusable Python functions
├── docs/                 # GitHub Pages project website
│   ├── index.md
│   ├── data_dictionary.md
│   └── assets/
├── requirements.txt      # Python dependencies
└── README.md
```

---

## Dataset
The analysis uses the corrected South German Credit dataset to avoid known 
inconsistencies in the original UCI German Credit dataset.
A custom parser is used to transform the original codebook into a structured mapping table. 
This enables reproducible renaming and categorical decoding of the dataset.

A detailed overview of the variables is available in the [data dictionary](docs/data_dictionary.md).

---

## Methodology

The analysis follows these main steps:

1. Load and clean the original dataset
2. Parse the code table and convert coded variables into readable labels
3. Explore default rates across applicant and loan characteristics
4. Transform categorical variables using Weight of Evidence encoding
5. Train an interpretable logistic regression model
6. Evaluate model performance using classification metrics and visual diagnostics
7. Compare classification thresholds under asymmetric misclassification costs

---

## Tools

- Python  
- Pandas / NumPy
- Matplotlib / Seaborn  
- scipy  
- scikit-learn (Logistic Regression, metrics)  
- Jupyter Notebook  

---

## Note

This project is part of a portfolio to demonstrate structured data analysis skills in a credit risk context. 
It combines EDA with a transparent predictive model suitable for regulatory banking environments, focusing on interpretability and business-relevant insights rather than purely predictive modeling.
The German Credit dataset is small, historical and simplified. The results should not be interpreted as a production-ready credit approval system or as a real-world banking model.