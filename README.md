# Clinical Trial Feasibility ML

## Overview

This project demonstrates how machine learning can be used to support **clinical trial feasibility and site selection**.

The objective is to predict the number of days required for a clinical trial site to enroll patients based on information available before the trial begins.

The project uses a synthetic dataset representing clinical trial sites and compares several regression models to identify the best-performing approach.

> **Note:** The dataset is synthetic and is intended for demonstration and educational purposes only. It does not represent real clinical trial data.

---

## Business Problem

Clinical trial teams need to identify sites that are likely to recruit patients efficiently.

A predictive model can help answer:

> **Which clinical trial sites are likely to achieve enrollment targets faster?**

This can support activities such as:

- Clinical trial feasibility
- Site selection
- Enrollment forecasting
- Site prioritisation
- Study planning

---

## Dataset

The dataset contains 100 synthetic clinical trial sites.

### Features

| Feature | Description |
|---|---|
| `site_id` | Unique identifier for each site |
| `site_experience` | Number of previous clinical trials |
| `patient_pool` | Estimated available patient population |
| `startup_speed` | Estimated number of days required for site start-up |
| `enrollment_days` | Number of days required for enrollment — target variable |

The dataset was generated using Python and saved as:

```text
data/clinical_trial_sites.csv
Machine Learning Approach

This is a supervised regression problem because the target variable, enrollment_days, is numerical.

The following models were evaluated:

Linear Regression
Random Forest Regressor
Gradient Boosting Regressor
XGBoost Regressor
Evaluation Metric

The primary evaluation metric is Mean Absolute Error (MAE).

MAE represents the average difference between predicted and actual enrollment time in days.

Lower MAE indicates better predictive performance.

Model Results

Results from the current test set:

Linear Regression    → MAE: 94 days
Random Forest        → MAE: 34 days
Gradient Boosting    → MAE: 23 days
XGBoost              → MAE: 27 days

Gradient Boosting produced the lowest MAE on the current test set.

Because the dataset is small and synthetic, these results should not be interpreted as evidence of real-world clinical trial performance.

Feature Importance

Feature importance was examined using the tree-based models.

The models consistently identified patient pool as the strongest predictor in this synthetic dataset.

This result is expected to some extent because the synthetic data-generation process assigns a strong relationship between patient pool and enrollment time.

Feature importance indicates predictive contribution to the model; it should not be interpreted as causal evidence.

Site Selection

The trained model can be used to estimate enrollment time for all available sites.

Sites can then be ranked according to predicted enrollment time:

Lower predicted enrollment days
                ↓
        Higher priority

Example workflow:

Site Data
    ↓
Data Preparation
    ↓
Train Regression Models
    ↓
Evaluate Models
    ↓
Select Best-Performing Model
    ↓
Predict Enrollment Days
    ↓
Rank Clinical Trial Sites
Project Structure
clinical-trial-feasibility-ml/
│
├── data/
│   └── clinical_trial_sites.csv
│
├── notebooks/
│   ├── 01_site_selection.ipynb
│   ├── analysis.ipynb
│   └── ml2i.png
│
├── src/
│   └── model.py
│
├── README.md
├── requirements.txt
└── .gitignore
Technologies
Python
Pandas
NumPy
Scikit-learn
XGBoost
Matplotlib
Jupyter Notebook
Git / GitHub
Installation

Clone the repository:

git clone https://github.com/Uchemadu7Nwachukwu/clinical-trial-feasibility-ml.git

Navigate to the project:

cd clinical-trial-feasibility-ml

Create a virtual environment:

python -m venv .venv

Activate it on Windows:

.\.venv\Scripts\Activate.ps1

Install the required packages:

pip install -r requirements.txt
Running the Project

Open the project in VS Code and launch:

notebooks/01_site_selection.ipynb

Run the notebook cells sequentially to:

Load the dataset
Explore the data
Train regression models
Compare model performance
Analyse feature importance
Predict enrollment time
Rank clinical trial sites
Future Improvements

Potential improvements include:

Cross-validation for more reliable model evaluation
Hyperparameter tuning
SHAP-based model explainability
Actual vs predicted visualisations
Classification of sites into high/low feasibility
Enrollment forecasting over time
Additional clinical trial feasibility variables
Real-world clinical trial operational data, where appropriately sourced and permitted
Key Takeaway

This project demonstrates a complete machine learning workflow for a clinical trial feasibility use case:

Data → Exploration → Modelling → Evaluation → Explainability → Site Prioritisation

The main objective is to demonstrate how predictive modelling can support data-driven decision-making in clinical trial planning.


Then save the file.

### Push the README to GitHub

In your VS Code terminal:

```powershell
git add README.md
git commit -m "Add project documentation"
git push
