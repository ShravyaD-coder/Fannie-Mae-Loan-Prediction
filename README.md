# Fannie Mae Loan Performance Prediction

## Overview
The project focuses on building predictive models using Fannie Mae mortgage loan data to:
- Predict the **number of months payments (NMONTHS)** are made on each mortgage.
- Predict the likelihood of **foreclosure (FORECLOSURE)** for each mortgage.

Understanding these predictions is critical for stakeholders such as Fannie Mae and investors in mortgage-backed securities (MBS), who rely on forecasts of cash flows and risk.

---

## Project Goals
- **Regression task:** Predict `NMONTHS`, the number of monthly mortgage payments expected before payments cease.
- **Classification task:** Predict `FORECLOSURE` (1 if foreclosed, 0 otherwise) and identify the **1,000 loans most likely to foreclose**.

---

## Data Description
The project uses two datasets:

- **Training dataset**:  
  - 250,000 mortgage loans  
  - 27 predictor variables + `LOAN ID` + two response variables (`NMONTHS`, `FORECLOSURE`)

- **Test dataset**:  
  - 100,000 mortgage loans  
  - Same 27 predictor variables + `LOAN ID`  
  - Ground truth held separately for performance evaluation.

### Key Variables
- **Predictors:** Loan terms, interest rates, LTV ratios, borrower credit scores, property info, etc.  
- **Response variables:**  
  - `NMONTHS`: Number of months payments were made.
  - `FORECLOSURE`: 1 if foreclosed, 0 otherwise.

---

## Data Processing & Feature Engineering
- **Dropped columns** with too many null values to maintain model integrity
- **Converted integer fields** (initially stored as strings) to proper numeric types
- **Parsed dates** to extract `month` and `year` components for temporal analysis
- **One-hot encoded categorical variables** such as loan purpose, occupancy status, property type, and more
- **Imputed missing values** with suitable strategies to minimize data loss
- **Applied PCA** for dimensionality reduction, improving computational efficiency and focusing on principal components

---

## Approach & Methods
- Used provided Jupyter notebook to parse fixed-width CSV files into dataframes
- **Regression:**  
  - Gamma regression model to predict `NMONTHS`.  
  - Estimated mean absolute error via internal train/test splits

- **Classification:**  
  - Logistic regression to predict `FORECLOSURE`.
  - Selected top 1,000 loans by predicted foreclosure probability
---

## Libraries Used

This project was implemented in Python using the following key libraries and tools:

- `pandas` — for data manipulation and analysis
- `numpy` — for numerical operations
- `requests` — to handle any data retrieval from remote sources
- `import_ipynb` — to import functions from other notebooks (e.g. `FunctionToReadData.ipynb`)
- `matplotlib` & `seaborn` — for data visualization (box plots, distributions, correlation heatmaps)
- `scikit-learn (sklearn)`:
  - `train_test_split` for splitting data
  - `StandardScaler` for feature scaling
  - `PCA` for dimensionality reduction
  - `GammaRegressor` for modeling `NMONTHS`
  - `LogisticRegression` for modeling `FORECLOSURE`
  - `mean_squared_error`, `mean_absolute_error`, `r2_score` for evaluation metrics

---

## Note
- This project is my submission for the final assignment of the course **553.688 Computing for Applied Mathematics (Fall 2024)** (Instructor Prof. Dan Naiman) at Johns Hopkins University
- This entire processing and modeling pipeline is **tailored specifically to the dataset provided to me for the final assessment**
- Running this code on a different dataset (or even on another student’s data from the same course) will likely result in errors, due to differences in data distributions, unique preprocessing needs, and file specifications
- The actual training and test datasets used in this project are **not included in this repository**, as they were provided exclusively for coursework and cannot be shared


