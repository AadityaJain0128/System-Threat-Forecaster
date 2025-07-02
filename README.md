
# Malware Prediction Based on System Configuration

## Overview

This project is based on a Kaggle competition where the goal is to **predict the probability of a Windows machine being infected by malware**, using system telemetry data. The dataset contains anonymized system configuration properties and corresponding malware infection labels.

---

## Problem Statement

Given various **system attributes**—like software versions, hardware specs, protection states, and system settings—the task is to build a machine learning model that can accurately **classify whether a machine is likely to be infected by malware**.

---

## Approach

- **EDA (Exploratory Data Analysis):**  
  Explored distributions, missing values, and correlation between features and target.

- **Preprocessing:**  
  - Missing value imputation using `SimpleImputer`  
  - Version number cleaning (e.g., "1.2.3.4" → 1234)  
  - Encoding:
    - `OneHotEncoder` for nominal categorical features
    - `OrdinalEncoder` for ordinal features  
  - Scaling using `StandardScaler`

- **Feature Selection & Engineering:**  
  - Removed highly unique or low-variance columns  
  - Used `RFE` and `SelectKBest` for dimensionality reduction  
  - Created numeric representations for version-based columns

- **Modeling:**  
  Trained and evaluated multiple models including:
  - `SGDClassifier` (Logistic Regression with `log_loss`)
  - `RandomForestClassifier`
  - `XGBoostClassifier` with hyperparameter tuning

- **Evaluation Metrics:**  
  - Accuracy
  - Log loss
  - Confusion matrix and classification report

---

## Dataset

- Source: [Kaggle Malware Prediction Dataset](https://www.kaggle.com/competitions/System-Threat-Forecaster)
- Rows: 99,835
- Features: 76 system telemetry fields (OS version, antivirus settings, etc.)
- Target: `0` (not infected) / `1` (infected)

---

## Technologies Used

- Python, NumPy, Pandas
- Scikit-learn
- Seaborn, Matplotlib
- lightgbm
- XGBoost

---

## Key Learnings

- Handling high-dimensional, balanced, and noisy telemetry data
- Selecting encoding strategies based on feature type
- Dimensionality reduction to prevent overfitting
- Model selection and evaluation in a real-world malware detection context
