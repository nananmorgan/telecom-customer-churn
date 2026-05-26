# Telecom Customer Churn: Segmentation and Prediction

## Overview
Customer churn is a persistent challenge in subscription-based industries. Acquiring a new customer can cost 5 to 25 times more than retaining an existing one, making early identification of at-risk customers a high-value business problem. This project takes a two-stage approach: first segmenting customers into behavioral archetypes using K-Means clustering, then training a Logistic Regression classifier to predict churn. The combined approach allows for both prediction and targeted, segment-specific retention strategies.

## Key Results
- Logistic Regression achieved **80% accuracy** and an **AUC-ROC of 0.84**
- Precision (churn class): 0.64 | Recall: 0.53 | F1: 0.58
- K-Means clustering (k=3) identified three distinct customer segments with meaningfully different churn rates

## Customer Segments
| Cluster | Profile | Churn Rate |
|---------|---------|------------|
| Cluster 0 | Loyal Super Users: high tenure, high charges, full service usage | ~15% |
| Cluster 1 | Low-Value Loyal Users: minimal service usage, low charges | ~7% |
| Cluster 2 | High-Risk New Users: low tenure, full service usage | ~43% |

Cluster 2 represents the highest-priority target for retention interventions, particularly through improved onboarding and early customer support.

## Key EDA Findings
- Month-to-month contract customers churned far more often than those on one or two year contracts
- Customers with high monthly charges and low tenure were at the highest risk of churn
- Fiber optic customers churned at a higher rate than DSL customers or those with no internet service
- Customers who churned had significantly lower total charges, suggesting they left early in the customer lifecycle

## Methods
- **Exploratory Data Analysis**: Churn by contract type, monthly charges vs. tenure, churn by internet service type, total charges distributions
- **Data Preparation**: Removed non-predictive columns, binary-encoded yes/no and gender fields, one-hot encoded multi-category variables (Contract, InternetService, PaymentMethod), standardized numeric features for clustering, engineered a TotalServicesUsed feature to capture engagement
- **Clustering**: K-Means with k=3, selected using the elbow method and silhouette analysis
- **Classification**: Logistic Regression with StandardScaler, evaluated on accuracy, AUC-ROC, precision, recall, F1, and confusion matrix
- Data snooping was avoided by ensuring transformations did not leak information from the target variable

## Dataset
IBM Telco Customer Churn dataset, sourced from [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn). Contains customer-level data including demographic details, account information, and service usage for 7,043 customers.

## Tools
Python, scikit-learn (KMeans, LogisticRegression, StandardScaler), pandas, numpy, matplotlib, seaborn

## Repository Contents
```
telecom-customer-churn/
├── customer_churn.ipynb             # Full analysis: EDA, clustering, and classification
├── project_writeup.docx             # Project write-up and findings
├── telecom_customer_churn_data.csv  # Source dataset
└── README.md
```

## How to Run
1. Install dependencies: `pip install pandas numpy matplotlib seaborn scikit-learn`
2. Open `telecom_churn_analysis.ipynb` in Jupyter or VS Code and run all cells

  
---
  
*Part of my [Data Science Portfolio](https://github.com/nananmorgan/data-science-portfolio)*
  
---
