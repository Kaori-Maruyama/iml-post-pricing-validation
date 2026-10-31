# iml-post-pricing-validation

## Overview

This repository provides the Python code and simulated datasets accompanying the following research.

**Interpretable Machine Learning as an Exploratory Data Analysis Tool: An Application to Post-Pricing Validation of Japanese Private Health Insurance Products**

*Maruyama et al. (2026)*

(See the Reference section for the full citation.)

This study demonstrates how Interpretable Machine Learning (IML) can be used as an Exploratory Data Analysis (EDA) tool to complement traditional Actual-to-Expected (A/E) analysis in post-pricing validation of private health insurance products.

The analysis focuses on the lump-sum hospitalization rider and uses simulated insurance data designed to reflect the structure of actual insurance operational data while preserving confidentiality.

Two analytical cases are presented, using datasets with different levels of granularity.

## Repository Structure

```text
.
├── Case1/
│   ├── Case1.ipynb
│   └── inforce_policies_aggregated_0.5.0.zip
│
├── Case2/
│   ├── Case2.ipynb
│   └── inforce_policies_aggregated_0.5.0.zip
│
└── reference/
    └── generate_simulated_data.ipynb

```

## Analytical Cases

### Case 1: Global Analysis Using Aggregated Data

**Dataset:** Dataset A (Aggregated data)

**Objective:**

To obtain a global understanding of the features influencing the predicted A/E ratio and the interaction effects among those features.

Dataset A consists of aggregated data extracted from an A/E analysis database. The analysis examines all available features rather than limiting the investigation to features selected based on prior actuarial experience or hypotheses.

**IML Methods:**

- **Permutation Feature Importance (PFI):** Identifies and ranks features according to their importance in the fitted model.
- **SHAP Summary Plot:** Visualizes the magnitude, distribution, and direction of feature contributions across the dataset.
- **Partial Dependence Plot (PDP):** Examines the relationship between individual features and the predicted A/E ratio.
- **Two-way PDP:** Visualizes how the relationship between two features jointly affects the predicted A/E ratio.
- **Friedman's H-statistic:** Quantifies the strength of pairwise interaction effects between features.

Together, these methods provide complementary insights into feature importance, feature effects, and interactions in the fitted model.

### Case 2: Policy-Level Analysis Using SHAP

**Dataset:** Dataset B (Policy-level data)

**Objective:**

To understand the factors associated with policies exhibiting high predicted A/E ratios and to examine the contributions of individual features to the predicted A/E ratio for each policy.

Dataset B contains policy-level data, including more detailed policy and product attributes than Dataset A, such as the sums assured of other riders and the presence of optional riders.

**IML Method:**

- **SHAP Waterfall Plot:** Visualizes how individual features contribute to the predicted A/E ratio for each policy, showing how the prediction moves from the baseline value to the final predicted value.

By examining policies with different levels of predicted A/E ratios, analysts can identify the characteristics contributing to higher predicted A/E ratios and guide further actuarial investigations.

## Prediction Model

LightGBM is used to predict the A/E ratio.

The model is trained using expected-amount-weighted squared-error loss (WLS) and Poisson deviance loss. The WLS model is used as the primary model for the IML analyses.

## How to Run

### Case 1

1. Extract `inforce_policies_aggregated_0.5.0.zip` to obtain the CSV file.
2. Place `Case1.ipynb` and the extracted CSV file in the same folder.
3. Open `Case1.ipynb` using Jupyter Notebook or JupyterLab.
4. Run the notebook cells sequentially.

### Case 2

1. Extract `inforce_policies_aggregated_0.5.0.zip` to obtain the CSV file.
2. Place `Case2.ipynb` and the extracted CSV file in the same folder.
3. Open `Case2.ipynb` using Jupyter Notebook or JupyterLab.
4. Run the notebook cells sequentially.

### Generating Simulated Data

The `reference/generate_simulated_data.ipynb` notebook provides the code used to generate the simulated datasets.

It is included to illustrate the data generation process and the construction of the simulated insurance data used in this study.

## Data and Confidentiality

All datasets provided in this repository are simulated data.

They are designed to reflect the structure of insurance operational data, including data fields and aggregation frameworks, while preserving confidentiality.

The simulated data do not reproduce the actual portfolio characteristics or interaction effects of any particular insurance company. Therefore, the numerical results should not be interpreted as representing actual insurance claim experience.

## Reference

Maruyama, K., Kozuma, R., Asashiba, R., Murakami, K., Asai, M., & Iwasawa, H. (2026).

*Interpretable Machine Learning as an Exploratory Data Analysis Tool: An Application to Post-Pricing Validation of Japanese Private Health Insurance Products.*

33rd International Congress of Actuaries (ICA2026).

## Disclaimer

The code is provided for research and educational purposes. It illustrates how IML can be applied as an exploratory data analysis tool in actuarial practice and is not necessarily intended as a production-ready implementation.
