# project-24

# Auto Insurance Claims Analytics and Predictive Modeling

## 1. Project Overview

This project analyzes auto insurance claims data to investigate claim severity, reporting delays, payment incidence, payment amounts, and policyholder risk profiles.

Five related datasets are integrated into a unified claim-level dataset. Exploratory Data Analysis (EDA), supervised machine learning, feature importance analysis, and unsupervised clustering are applied to answer five research questions.

The project focuses on comparing statistical baselines with more sophisticated machine learning models, evaluating predictive performance using appropriate metrics, and identifying the limitations of the available data.

**Project Objectives:**

- Integrate multiple relational datasets into a single analytical dataset.
- Examine numerical and categorical variables while preserving meaningful information.
- Investigate five research questions from different analytical perspectives.
- Compare multiple machine learning models using cross-validation.
- Identify the most influential predictive features.
- Segment claims into interpretable groups using K-Means clustering.
- Evaluate model limitations and practical implications.

---

## 2. Dataset Description

The project uses five CSV datasets:

| Dataset | Records | Description |
|---|---:|---|
| `claim_payments.csv` | 38,843 | Recorded insurance claim payments |
| `claims.csv` | 50,000 | Claim information, amounts, dates, and incident characteristics |
| `policies.csv` | 37,000 | Insurance policy characteristics |
| `policyholders.csv` | 30,000 | Policyholder demographic information |
| `vehicles.csv` | 37,000 | Vehicle characteristics |

### Data Integration

The five datasets are merged into a claim-level analytical dataset.

Payment records are aggregated before merging to prevent duplication caused by multiple payments associated with a single claim.

The resulting dataset contains approximately 50,000 claim records and 40 variables.

**Merged dataset:** `auto_insurance_claims_merged.csv`

### Data Preprocessing

The preprocessing workflow includes:

- Checking missing values and duplicate records.
- Validating relational keys and merge relationships.
- Converting date variables into datetime format.
- Engineering temporal features, including reporting delay, loss year, and loss month.
- Preserving categorical information through appropriate encoding.
- Examining text variables for potentially multiple values within individual cells.
- Applying numerical scaling and categorical encoding within machine learning pipelines.
- Separating training and testing data to evaluate model generalization.

Special attention is given to avoiding data leakage and preventing information from the test set from influencing model training.

---

## 3. Research Questions

The project investigates five research questions.

| Research Question | Analytical Task | Primary Evaluation |
|---|---|---|
| RQ1: Can claim amounts be predicted using policyholder, vehicle, and incident characteristics? | Regression | MAE |
| RQ2: Can insurance claim reporting delays be predicted? | Regression | MAE |
| RQ3: Can we predict whether a claim has a recorded payment? | Binary Classification | PR-AUC |
| RQ4: Can recorded payment amounts be estimated accurately? | Regression | MAE |
| RQ5: Can claims be segmented into meaningful profiles? | Clustering | Elbow and Silhouette |

The research questions address different stages and aspects of the insurance claim process.

---

## 4. Exploratory Data Analysis

EDA was conducted to examine distributions, relationships, and potential data quality concerns.


---

## 5. Machine Learning Methodology

### Regression Models

For RQ1, RQ2, and RQ4, the following models were compared:

- Dummy Median
- Ridge Regression
- Random Forest Regressor
- Extra Trees Regressor

**Primary metric:** Mean Absolute Error (MAE)

**Secondary metrics:** Root Mean Squared Error (RMSE) and R²

MAE was selected as the primary evaluation metric because it measures prediction errors in the original units and is less sensitive to extreme observations than squared-error metrics.

### Classification Models

For RQ3, the following models were compared:

- Dummy Prior
- Logistic Regression
- Random Forest Classifier
- Extra Trees Classifier

**Primary metric:** PR-AUC

**Secondary metrics:** ROC-AUC, Precision, Recall, F1-score, and Accuracy

PR-AUC was selected because the target variable has an imbalanced class distribution and the analysis focuses on identifying claims with recorded payments.

### Model Selection

Models were compared using cross-validation on the training data.

The model achieving the best mean cross-validation score according to the predefined primary metric was selected.

Final performance was evaluated using a separate holdout test set.

Permutation importance was used to investigate feature contributions. When a baseline model was selected, feature importance from an alternative fitted model could be examined as a supplementary exploratory analysis.



---

## 6. Tools and Technologies

**Programming Language:** Python

**Data Processing:**
- Pandas
- NumPy

**Visualization:**
- Matplotlib
- Seaborn

**Machine Learning:**
- Scikit-learn

**Development Environment:**
- Visual Studio Code
- Jupyter Notebook
- Quarto
- GitHub Codespaces

---
