# smart-grid-overload-classification
Smart-grid overload classification using machine learning and multi-source electrical, renewable, and environmental data.
# Machine Learning-Based Classification of Overload Conditions in Smart Grids

This repository contains the dataset and supporting information associated with the study:

**"Machine Learning-Based Classification of Overload Conditions in Smart Grids Using Multi-Source Electrical and Environmental Features"**

## Overview

This study develops a machine-learning framework for classifying smart-grid operating conditions into **Normal** and **Overload** states using multi-source electrical, renewable-generation, environmental, and operational features.

The study uses a publicly available smart-grid dataset obtained from Kaggle. The downloaded data were subsequently prepared and processed for the present analysis.

## Dataset Source

The original dataset was obtained from the following publicly available Kaggle source:

**Smart Grid Real-Time Load Monitoring Dataset**  
https://www.kaggle.com/datasets/ziya07/smart-grid-real-time-load-monitoring-dataset

The authors did not collect physical measurements directly. The present study is based on the publicly available secondary dataset obtained from the above source.

## Dataset Description

The dataset used in this study contains **50,000 time-ordered observations** recorded at **15-minute intervals**.

The dataset includes electrical, renewable-generation, environmental, and operational variables, including:

- Voltage (V)
- Current (A)
- Power Consumption (kW)
- Reactive Power (kVAR)
- Power Factor
- Solar Power (kW)
- Wind Power (kW)
- Grid Supply (kW)
- Predicted Load (kW)
- Voltage Fluctuation (%)
- Temperature (°C)
- Humidity (%)
- Electricity Price (USD/kWh)
- Transformer Fault
- Overload Condition

### Target Variable

**Overload Condition**

- `0` = Normal operating condition
- `1` = Overload operating condition

The existing overload labels provided in the dataset were used for the binary classification task.

## Data Processing

For the present study, the downloaded dataset was subsequently processed for machine-learning analysis. The workflow included:

1. Data preparation and preprocessing
2. Feature preparation
3. Physics-informed feature engineering
4. Chronological train-validation-test splitting
5. Feature scaling using training data
6. Class-imbalance handling
7. Machine-learning model development
8. Temporal cross-validation and hyperparameter optimization
9. Independent test evaluation
10. SHAP-based model interpretation

## Machine-Learning Models

Six supervised classification algorithms were evaluated:

- Logistic Regression
- Support Vector Machine (SVM)
- Random Forest
- XGBoost
- LightGBM
- CatBoost

XGBoost was selected as the final model following comparative evaluation and temporal hyperparameter optimization.

## Evaluation Metrics

Model performance was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- PR-AUC
- Matthews Correlation Coefficient (MCC)
- Cohen's Kappa

Because overload events represent the minority class, particular emphasis was placed on **Recall, F1-score, PR-AUC, and MCC**.

## Final Model Performance

On the independent test dataset, the optimized XGBoost model achieved:

| Metric | Performance |
|---|---:|
| Accuracy | 95.63% |
| Precision | 78.96% |
| Recall | 93.71% |
| F1-score | 85.70% |
| ROC-AUC | 99.12% |
| PR-AUC | 95.10% |
| MCC | 83.57% |
| Cohen's Kappa | 83.14% |

The final test confusion matrix identified **983 of 1,049 overload events**, with **66 false negatives** and **262 false positives**.

## Explainable AI

SHAP (SHapley Additive exPlanations) was used to interpret the final XGBoost model.

The most influential variables included:

1. Grid Supply
2. Solar Power
3. Predicted Load
4. Power Consumption
5. Electricity Price
6. Current

The analysis also examined important feature interactions, particularly between:

- Solar Power and Predicted Load
- Grid Supply and Solar Power
- Grid Supply and Predicted Load

## Repository Contents

The repository may contain the following files:

```text
smart-grid-overload-classification/
│
├── data/
│   └── smart_grid_raw_data_50000.csv
│
├── README.md
└── LICENSE
