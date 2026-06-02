# Data Dictionary

This document describes the variables used in the German Credit Risk Modeling project.

The original German Credit dataset contains coded variable names and coded category values. To make the analysis and modeling workflow easier to interpret, the accompanying code table was parsed and the original codes were mapped to descriptive variable names and category labels.

The cleaned variable names and labels are used throughout the exploratory analysis, Weight of Evidence encoding and logistic regression modeling.

---

## Dataset Overview
Each row in the dataset represents one credit applicant or credit case.

The original data can be found here:
https://archive.ics.uci.edu/dataset/522/south+german+credit

The dataset consists of the following columns:

| Name                    | Description                                                              | Type        |
|-------------------------|--------------------------------------------------------------------------|-------------|
| status                  | Status of existing checking account in DM (Deutschen Mark)               | categorical |
| duration                | Duration in months for the loan/credit                                   | numerical   |
| credit_history          | Credit history of the applicant                                          | categorical |
| purpose                 | Purpose of the credit                                                    | categorical |
| amount                  | Credit amount of the loan                                                | numerical   |
| savings                 | Status of savings account in DM (Deutschen Mark)                         | categorical |
| employment_duration     | Present employment since                                                 | categorical |
| installment_rate        | Installment rate in percentage of disposable income                      | categorical |
| personal_status_sex     | Categories with personal status and sex                                  | categorical |
| other_debtors           | Other debtors / guarantors                                               | categorical |
| present_residence       | Present residence since                                                  | categorical |
| property                | Possible collateral for loan                                             | categorical |
| age                     | Age in years                                                             | numerical   |
| other_installment_plans | Other installment plans                                                  | categorical |
| housing                 | Indicator of the current housing (rent, own or for free)                 | categorical |
| number_credits          | Number of existing credits at this bank                                  | numerical   |
| job                     | Categories of job                                                        | categorical |
| people_liable           | Number of people being liable to provide maintenance for                 | categorical |
| telephone               | Flag indicating if the customer has a telephone registered in their name | categorical |
| foreign_worker          | Flag indicating foreign workers                                          | categorical |
| credit_risk             | Good = customer properly paid the loan, Bad otherwise                    | categorical |

**A Note on Sensitive Features**
The dataset contains two features that warrant special attention:
`personal_status_sex` and `foreign_worker`.
Both are excluded from the risk driver analysis. Under EU anti-discrimination
law and GDPR, the use of characteristics such as gender or nationality in
credit decisions is legally restricted and may expose institutions to
regulatory and reputational risk.


## Preprocessing Summary

The original dataset was transformed to improve readability and interpretability.

Main preprocessing steps:

- original coded variable names were replaced with descriptive names
- coded category values were mapped to readable labels
- numerical variables were converted to appropriate numeric types

These transformations do not add new information to the dataset. They only make the original coded values easier to understand and use in the analysis.

## Dataset Limitations

The German Credit dataset is useful for demonstrating a credit risk modeling workflow, but it has important limitations:

- it is small compared with real-world credit risk datasets
- it is historical and may not reflect current credit markets
- it contains simplified and coarse applicant information
- it does not include detailed income, affordability or macroeconomic information
- it does not provide real financial loss amounts
- some variables may be sensitive or problematic in a real-world decision system
- results are not suitable for production use

This project should therefore be understood as an educational portfolio project, not as a real credit approval model.
