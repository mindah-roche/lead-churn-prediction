# Churn Prediction Project Report

## Project Overview
This project aims to predict lead conversion (churn) in a marketing dataset using machine learning models. The workflow covers data import, cleaning, feature engineering, exploratory data analysis (EDA), model building, evaluation, and interpretation of results.

## 1. Data Import and Initial Exploration
- Data was imported from the HuggingFace Datasets library.
- The dataset contains information about marketing leads, including lead status, stage, source, and behavioral metrics (calls, connects, etc.).
- Initial checks included inspecting data shape, missing values, and unique values in key columns.

## 2. Data Cleaning and Preprocessing
- **Lead Disposition and Lead Stage**: Text values were consolidated into standardized categories using custom functions, reducing noise and improving consistency.
- **Conversion Data**: The target variable was binarized (1 for 'YES', 0 otherwise).
- **Date Features**: The 'Created On' column was converted to datetime, and new features (month, day, weekday) were extracted.
- **Missing Values**: Numerical columns were filled with the median; categorical columns were filled with 'Unknown'.
- **Irrelevant Columns**: High-null or irrelevant columns were dropped to streamline the dataset.

## 3. Exploratory Data Analysis (EDA)
- **Class Balance**: The target variable ('Converted') was moderately imbalanced.
- **Univariate Analysis**: Distributions of key categorical and numerical features were visualized.
- **Bivariate Analysis**: Conversion rates were analyzed by lead disposition, stage, state, and time features.
- **Behavioral Metrics**: Relationships between total calls/connects and conversion were explored.

## 4. Feature Engineering
- **Categorical Encoding**: One-hot encoding was applied to categorical variables (Lead Disposition, Lead Source, Lead Stage, State, Student Grade).
- **Numerical Transformation**: Skewed features (Total Calls, Total Connects) were log-transformed.
- **Temporal Features**: Month and weekday were encoded as categorical dummies.
- **Interaction Terms**: Created for potential nonlinear relationships.

## 5. Model Building
- **Train-Test Split**: Data was split into training and test sets (80/20 split, stratified by target).
- **Models Used**:
  - Logistic Regression (baseline, interpretable)
  - Random Forest Classifier (robust, non-linear)
- **Scaling**: Features were standardized before modeling.

## 6. Model Evaluation
- **Metrics**: Accuracy, Precision, Recall, F1-Score, ROC-AUC, and Confusion Matrix were used.
- **Results**:
  - Logistic Regression: Test Accuracy ~78%, AUC = 0.92
  - Random Forest: Test Accuracy ~84%, AUC = 0.81
- **Interpretation**:
  - Random Forest outperformed Logistic Regression in accuracy, precision, recall, and F1-score for both classes.
  - Logistic Regression had a higher AUC, indicating better probability ranking and class separation.
  - Confusion matrices showed Random Forest made fewer false positives and negatives, especially for churners.

## 7. Insights and Recommendations
- **Random Forest** is recommended for deployment due to its superior predictive performance, especially in identifying churners (critical for business action).
- **Logistic Regression** remains valuable for interpretability and understanding feature importance.
- **Business Impact**: Higher recall for churners means fewer missed at-risk leads; higher precision means more efficient targeting.

## 8. Next Steps
- Further hyperparameter tuning and model comparison (e.g., XGBoost, ensemble methods).
- Feature selection and importance analysis for actionable business insights.
- Deployment of the best model as a scoring service or dashboard.

---

This report summarizes the end-to-end process for churn prediction, from raw data to actionable model evaluation and business recommendations.
