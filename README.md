# Project-Deliverable-3-Classification-Clustering-and-Pattern-Mining (MSCS-634-B01)

## Project Overview
This deliverable focuses on advanced data mining techniques—classification, clustering, and association rule mining—applied to a healthcare dataset. The goal is to develop predictive and descriptive models that can help in estimating test results, uncovering hidden patient clusters, and mining medical treatment patterns.

## Tasks Completed

### 1. Classification Models
Two classification models were developed to predict patient test results:

- Decision Tree Classifier
- Naïve Bayes Classifier

Additionally, hyperparameter tuning using GridSearchCV was performed on the Decision Tree model.

### 2. Classification Evaluation
Evaluation metrics used:
- Confusion Matrix
- Accuracy and F1-Score
- Classification Report
- ROC Curve (conditionally generated for binary classification)

Results Summary:

| Model               | Accuracy | F1 Score |
|--------------------|----------|----------|
| Decision Tree       | 33.1%    | 0.32     |
| Naive Bayes         | 33.4%    | 0.33     |
| Tuned Decision Tree | 33.5%    | 0.29     |

All models performed similarly, with low performance due to likely class imbalance and complexity/noise in categorical data.

### 3. Clustering Model
A KMeans clustering model was used with 3 clusters based on numerical features: `age` and `billing_amount`.

Dimensionality was reduced using PCA and visualized in 2D.

Clusters revealed segments with differing age-billing patterns, possibly representing patient types (e.g., young/low-cost vs. elderly/high-cost).

### 4. Association Rule Mining
Association rules were mined using the Apriori algorithm on frequent combinations of `medical_condition` and `medication`.

Sample Discovered Rules:

| Medical Condition => Medication | Support | Confidence | Lift |
|---------------------------------|---------|------------|------|
| Arthritis => Aspirin            | 3.4%    | 20.5%      | 1.03 |
| Obesity => Penicillin           | 3.4%    | 20.4%      | 1.03 |
| Cancer => Lipitor               | 3.5%    | 20.8%      | 1.04 |

These rules confirm known clinical pairings and can inform default medication suggestions or anomaly detection if deviations are found.


## Key Insights
- Classification of test results remains challenging; model accuracy is near random guess levels (33%)
- Clustering based on age and billing segments patients into interpretable groups
- Association rule mining yields medically meaningful relationships between diagnoses and medications

## Challenges and Solutions

| Challenge                                            | Solution                                                         |
|------------------------------------------------------|------------------------------------------------------------------|
| Sparse one-hot encoding incompatible with GaussianNB | Used `sparse_output=False` in `OneHotEncoder`                    |
| No association rules found initially                 | Lowered `min_support` and `lift` thresholds to capture patterns  |
| Poor classification performance                      | Tuned Decision Tree; considered further feature engineering      |

