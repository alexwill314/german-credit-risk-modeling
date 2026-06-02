# Data Dictionary

This document describes the variables used in the German Credit Risk Modeling project.

The original German Credit dataset contains coded variable names and coded category values. To make the analysis and modeling workflow easier to interpret, the accompanying code table was parsed and the original codes were mapped to descriptive variable names and category labels.

The cleaned variable names and labels are used throughout the exploratory analysis, Weight of Evidence encoding and logistic regression modeling.

---

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

## Target Variable

The target variable is `credit_risk`.

It represents the observed credit risk classification in the dataset.

| Value | Meaning |
|---|---|
| `good` | Applicant was classified as lower credit risk |
| `bad` | Applicant was classified as higher credit risk |

---

## Variable Details

### `checking_account_status`

Status of the applicant's existing checking account.

This variable can be interpreted as a rough indicator of short-term liquidity or account relationship.

Typical categories include:

- no checking account
- checking account balance below zero
- low checking account balance
- higher checking account balance

---

### `duration_months`

Duration of the credit in months.

This is a numerical loan contract variable. Longer durations may be associated with different risk patterns than shorter durations.

---

### `credit_history`

Applicant's previous credit history.

This variable summarizes past credit behavior, such as whether previous credits were paid back duly or whether there were critical credit events.

---

### `purpose`

Purpose of the requested credit.

Examples may include:

- car
- furniture or equipment
- radio or television
- education
- business
- repairs
- other purposes

The exact category labels depend on the parsed code table.

---

### `credit_amount`

Requested credit amount.

This is a numerical loan contract variable and represents the size of the credit.

---

### `savings_account`

Status of savings account or bonds.

This variable can be interpreted as a rough proxy for available financial reserves.

Typical categories include different savings balance ranges and cases where no savings account is available or known.

---

### `employment_duration`

Duration of current employment.

This variable is categorical or ordinal and represents employment stability.

Typical categories include:

- unemployed
- employed for less than one year
- employed for one to four years
- employed for four to seven years
- employed for more than seven years

---

### `installment_rate`

Installment rate as a percentage of disposable income.

This variable represents the repayment burden relative to income. In the original dataset, it is usually given as an ordinal numerical value.

---

### `personal_status_sex`

Combined personal status and sex variable.

This variable contains information about marital or personal status and sex. It is part of the original dataset structure and should be interpreted carefully, especially because it combines multiple concepts into one categorical feature.

---

### `other_debtors`

Information about other debtors or guarantors involved in the credit.

Typical categories include:

- none
- co-applicant
- guarantor

---

### `residence_duration`

Duration of residence at the current address.

This variable is usually represented as an ordinal value and can be interpreted as a rough stability indicator.

---

### `property`

Property or asset category of the applicant.

Typical categories include different types of property or cases where no property is available. This variable can act as a rough proxy for financial security.

---

### `age`

Age of the applicant in years.

This is a numerical applicant characteristic.

---

### `other_installment_plans`

Other existing installment plans.

Typical categories include:

- bank
- stores
- none

This variable indicates whether the applicant has other ongoing installment obligations.

---

### `housing`

Housing situation of the applicant.

Typical categories include:

- rent
- own
- free

---

### `existing_credits`

Number of existing credits at the bank.

This variable indicates how many credits the applicant already has with the institution.

---

### `job`

Applicant's job category.

The original dataset groups applicants into broad occupational categories. These categories are coarse and should not be interpreted as detailed employment information.

---

### `liable_people`

Number of people the applicant is liable to provide maintenance for.

This variable can be interpreted as a rough indicator of financial responsibility or household burden.

---

### `telephone`

Telephone availability.

This variable indicates whether a telephone is registered or available according to the dataset.

---

### `foreign_worker`

Foreign worker indicator.

This variable is part of the original dataset. It should be interpreted carefully, since it reflects the historical structure of the dataset and may not be appropriate for real-world model deployment without legal, ethical and fairness review.

---

