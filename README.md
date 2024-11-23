# Datathon Challenge - Automated Property Valuation Model

## Overview
This project was developed during a 24-hour datathon organized by **UPC**, where our team of four students tackled the challenge of creating an **Automated Valuation Model (AVM)** for real estate in Illinois. We aimed to predict property sale prices using a dataset provided by **Restb.ai**.

The complete project was coded collaboratively on **Google Colab**, while this repository on **GitHub** presents the final code. Since the dataset is private, only the methodology and code are shared. However, the approaches can be applied to other datasets with similar characteristics.

---

## Dataset Summary
- **Source**: Real estate transactions in Illinois (Sept 2023 – Sept 2024)
- **Dimensions**:
  - **Training Set**: 107,437 rows
  - **Test Set**: 22,039 rows
  - **Features**: 
    - **54 original variables** expanded into **631 features** after preprocessing
    - Target variable: Property sale price
    - **24% missing values** across all data
- **Key Challenges**:
  - High dimensionality and missing values
  - Outliers (e.g., properties with extreme prices, unusual features)

---

## Methodology

### 1. **Data Preprocessing**
- **Missing Values**:
  - Location-based: Estimated using mean latitude/longitude per city
  - Features like living area: Derived from related metrics (e.g., rooms)
  - General: Imputed using median or dropped if excessive missingness
- **Feature Expansion**:
  - Categorical variables: One-hot encoding
  - List variables: Expanded into binary columns for each unique list value
- **Formatting**:
  - Dates: Converted to days since the earliest transaction
  - Grouping categorical variables: Based on cumulative frequency for more robust encoding
- **Outlier Handling**:
  - Flagged extreme anomalies, such a $35M two-bedroom apartment or a property with 75 bathrooms
- **Dimensionality Reduction**:
  - Features with dominance (>80% binary value skew) removed
  - Correlated features (correlation > 0.8) dropped
  - Final selection: 24 key features (e.g., living area, kitchen quality, interiors)

---

### 2. **Model Development**
- **Approach**:
  - Explored various algorithms: 
    - Linear Regression, Decision Trees, Random Forest, Extra Trees, XGBoost
  - Hyperparameter tuning via grid search
- **Best Model**:
  - **Random Forest**:
    - Parameters: `max_depth=30`, `n_estimators=200`
    - **Performance**:
      - Validation MAE: $58,000
      - Test MAE: $80,000
- **Evaluation**:
  - Used MSE and MAE as primary metrics
  - Focused on model interpretability and robustness over metric optimization

---

## Results and Reflections
Our AVM achieved competitive accuracy while maintaining interpretability. The methodology emphasized data cleaning, feature engineering, and justification of all preprocessing steps. Although the dataset is not public, the workflow can inspire similar projects in real estate or other domains.

---

## Team
- **Andreja Andrejic**
- **Simone Paloschi**
- **Jinheng Lin**
- **Alexandros Tremopoulos** 

We hope this repository provides valuable insights and sparks inspiration for your projects!