🛡️ FraudShield: Banking Fraud Detection System
📌 Project Overview

Fraud detection is a critical challenge in the banking and financial sector. This project builds a machine learning model to identify fraudulent transactions based on customer behavior, transaction patterns, and risk indicators.

The goal is to minimize financial losses by accurately detecting fraud while reducing false negatives (missed fraud cases).

🎯 Problem Statement

The objective is to develop a classification model that can distinguish between:

Fraudulent transactions (1)

Normal transactions (0)

The model should prioritize detecting fraud cases effectively, as missing fraud (false negatives) is more costly than false alarms.

📂 Dataset

File: FraudShield_Banking_Data.csv

Type: Structured tabular dataset

Contains:

Transaction details

Customer behavior

Risk indicators

Target variable: Fraud_Label

⚙️ Tech Stack

Python

Libraries:

pandas, numpy → data manipulation

matplotlib, seaborn → visualization

missingno → missing data analysis

scikit-learn → ML models & preprocessing

imbalanced-learn → SMOTE

xgboost → advanced boosting model

pickle → model saving

🔍 Project Workflow
1. Data Loading & Cleaning

Removed irrelevant identifier columns:

Transaction_ID, Customer_ID, Merchant_ID, Device_ID, IP_Address

Handled missing values in target variable

Converted target:

Fraud → 1

Normal → 0

2. Exploratory Data Analysis (EDA)

Checked dataset structure and missing values

Visualized:

Numerical features → Boxplots

Categorical features → Countplots

Observation:

Dataset appears synthetic or pre-cleaned (no strong outliers)

3. Feature Engineering

Created meaningful features to improve model performance:

Time-based Features

Transaction Hour

Transaction Day

Transaction Month

Night Transaction (binary)

Behavioral Features

Transaction Deviation

Transaction Velocity

Transaction Balance Ratio

Distance Risk

Fraud History

Transformations

Log Transaction Amount

Amount-to-Balance Ratio

Transactions per Hour

High-Risk Combination (Night + Distance)

4. Data Preprocessing
Imputation

Numerical → Median

Categorical → Most frequent

Encoding

OneHotEncoding for categorical variables

Scaling

StandardScaler applied to normalize features

5. Handling Class Imbalance

Visualized imbalance between fraud and normal cases

Applied SMOTE (Synthetic Minority Oversampling Technique) to balance classes

🤖 Models Used

The following models were trained and evaluated:

Random Forest

Logistic Regression

AdaBoost

XGBoost

📊 Model Evaluation
Metrics Used:

F2 Score (focus on recall → catching fraud)

Classification Report

ROC-AUC Curve

Confusion Matrix

Why F2 Score?

F2 emphasizes recall more than precision, which is critical in fraud detection:

Missing fraud is worse than flagging a normal transaction.

🏆 Best Model: XGBoost

Although not always the highest AUC, XGBoost was selected because:

Handles missing values well

Strong regularization (reduces overfitting)

High performance in real-world applications

Reliable for production systems

⚡ Hyperparameter Tuning

Used GridSearchCV to optimize:

n_estimators

max_depth

learning_rate

subsample

Final model selected using ROC-AUC score.

📈 Final Evaluation

Generated:

Classification report

ROC-AUC score

Confusion matrix

The model achieves strong performance in identifying fraud cases while maintaining balanced predictions.

💾 Model Saving

The trained model is saved using pickle:

with open('fraud_model.pkl', 'wb') as f:
    pickle.dump(best_model, f)
