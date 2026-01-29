# Predictive Maintenance of Oil & Gas Pipelines Using Machine Learning

## Project Overview
This project implements a machine learning–based predictive maintenance system to assess the condition of oil and gas pipelines using inspection data. The objective is to classify pipeline conditions into Normal, Moderate, and Critical categories in order to support risk-based maintenance decision-making and improve pipeline integrity management.

---

## Business Problem
Oil and gas pipelines are critical assets that degrade over time due to corrosion, operational stress, and material fatigue. Traditional maintenance strategies are often schedule-based or reactive, which can result in unnecessary inspections, late detection of high-risk pipelines, and increased operational and safety risks. This project addresses the problem by using historical inspection data and machine learning to prioritize maintenance actions based on actual pipeline condition.

---

## Dataset Description
The dataset consists of 1,000 inspection records with 11 features. After data cleaning and domain validation, 881 records were retained for modeling.

Feature categories include:
- Physical properties: pipe size, thickness, thickness loss  
- Operational conditions: maximum pressure, temperature  
- Degradation indicators: corrosion impact, material loss percentage  
- Asset attributes: material type, pipe grade  
- Temporal factor: time in service (years)

The target variable is Condition, representing pipeline health status (Normal, Moderate, Critical).

---

## Data Cleaning and Domain Validation
The dataset was validated using engineering-based domain rules to ensure physical consistency:
- Pipe thickness must be positive  
- Thickness loss must be non-negative  
- Thickness loss cannot exceed original thickness  
- Time in service must be non-negative  

Outliers were intentionally retained when they were physically valid, as extreme values often represent high-risk pipeline conditions that are critical for predictive maintenance.

---

## Exploratory Data Analysis
Exploratory data analysis focused on business-relevant insights. The analysis showed that thickness loss clearly differentiates pipeline conditions, with critical pipelines exhibiting significantly higher degradation. Initial pipe thickness acts as a mitigating factor, while material type and grade influence condition distribution but are not sole determinants. Most operational features show weak individual correlations, reinforcing the need for a multivariate, non-linear modeling approach.

---

## Feature Engineering and Preprocessing
Key preprocessing steps include:
- Creation of a Thickness Loss Ratio feature to represent relative degradation  
- Encoding of categorical features such as material and pipe grade  
- Train-test split for fair model evaluation  
- Feature scaling applied to numerical variables to ensure stable training and prevent data leakage  

---

## Modeling Approach
Two models were implemented and compared:
- Logistic Regression as a baseline model  
- Random Forest as the primary model to capture non-linear relationships and feature interactions  

Random Forest was selected as the final model due to its superior performance, particularly in identifying critical pipeline conditions.

---

## Model Evaluation
Model performance was evaluated using confusion matrices, classification reports, and macro F1-score to treat all condition classes equally. The Random Forest model consistently outperformed the baseline and demonstrated strong capability in detecting high-risk pipelines.

---

## Hyperparameter Tuning
Model performance was further improved using RandomizedSearchCV to optimize parameters such as the number of trees, maximum depth, and minimum samples per split and leaf. This tuning process enhanced generalization while avoiding overfitting.

---

## Model Interpretability
Feature importance analysis revealed that thickness loss is the most influential feature, followed by material loss percentage and thickness loss ratio. Operational and material features provide supporting signals. The model’s decision logic aligns well with pipeline engineering principles, increasing trust and interpretability.

---

## Inference and Prediction Pipeline
An end-to-end inference pipeline was developed to preprocess new inspection data consistently, apply scaling and encoding, and generate condition predictions along with class probabilities. This enables seamless integration into dashboards or decision-support systems.

---

## Business Impact and Recommendations
The solution enables risk-based maintenance prioritization, early identification of critical pipelines, optimized inspection planning, and reduced operational and safety risks. Pipelines with high degradation indicators can be flagged proactively, allowing maintenance teams to allocate resources more effectively.

---

## Conclusion
This project demonstrates how machine learning can be applied to pipeline integrity management to transition from reactive maintenance to a predictive, data-driven strategy. By combining domain knowledge, exploratory analysis, and interpretable modeling, the solution delivers both technical robustness and practical business value.
