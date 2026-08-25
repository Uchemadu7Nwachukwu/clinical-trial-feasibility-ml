# Clinical Trial Feasibility & Site Selection

> **Machine learning for clinical trial enrollment forecasting and site prioritisation.**

## 📌 Overview

Clinical trial feasibility involves identifying sites that are likely to recruit participants efficiently and meet enrollment targets.

This project explores how **machine learning regression models** can be applied to predict **site-level enrollment time** using clinical trial feasibility variables available before study initiation.

The workflow covers:

**Data → Exploration → Feature Analysis → Regression → Model Comparison → Site Ranking**

> **Dataset note:** The dataset used in this project was loaded from a prepared CSV file. It is intended for demonstration and portfolio purposes and should not be interpreted as real-world clinical evidence.

---

## 🎯 Objective

The primary objective is to predict:

> **How many days will a clinical trial site require to complete enrollment?**

The prediction can then be used to rank sites according to their expected enrollment performance.

### Potential applications

- Clinical trial feasibility
- Site selection
- Enrollment forecasting
- Site prioritisation
- Study planning

---

## 📊 Dataset

The dataset contains information for **100 clinical trial sites**.

### Features

| Feature | Description |
|---|---|
| `site_id` | Unique identifier for each clinical trial site |
| `site_experience` | Previous clinical trial experience |
| `patient_pool` | Estimated available patient population |
| `startup_speed` | Estimated site start-up time in days |
| `enrollment_days` | Actual enrollment duration — target variable |

The dataset is stored in:

```text
data/clinical_trial_sites.csv
🤖 Machine Learning

This project is formulated as a supervised regression problem because the target variable is numerical.

Four regression approaches were evaluated:

1. Linear Regression

A simple baseline model used to establish a reference level of performance.

2. Random Forest

An ensemble of decision trees capable of modelling non-linear relationships.

3. Gradient Boosting

An ensemble method that sequentially builds trees to reduce prediction error.

4. XGBoost

A gradient-boosting implementation designed for efficient and high-performance predictive modelling.

📈 Model Performance

The models were evaluated using Mean Absolute Error (MAE).

Lower MAE indicates better predictive performance.

Model                  MAE
──────────────────────────────
Linear Regression       94 days
Random Forest           34 days
Gradient Boosting       23 days ⭐
XGBoost                 27 days
Best-performing model

Gradient Boosting achieved the lowest MAE of 23 days on the current test set.

This means that, on the current test data, its predictions differed from the observed enrollment duration by approximately 23 days on average.

Because the dataset is limited in size and intended for demonstration, further validation would be required before drawing conclusions about real-world performance.

🔎 Feature Importance

Feature importance was examined using the tree-based models.

The results showed that:

Patient Pool       ████████████████████████████████████████
Startup Speed      █
Site Experience    █

Patient pool was the dominant predictive feature in the current dataset.

This should be interpreted as a model-specific predictive relationship, not as evidence of causality.

🏥 Site Prioritisation

After selecting the best-performing model, enrollment time can be predicted for all available sites.

Sites are then ranked by predicted enrollment duration.

                 Clinical Trial Sites
                         │
                         ▼
                 Predict Enrollment
                         │
                         ▼
                Rank by Predicted Days
                         │
                         ▼
                 Prioritise Sites
Example
Lower predicted enrollment days
              ↓
      Higher site priority

This provides a simple framework for translating a regression model into a potential site-selection decision-support tool.

🔬 Analytical Workflow
┌──────────────────────┐
│      Load Data       │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│   Explore & Prepare  │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│  Train Regression    │
│       Models         │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Compare Performance  │
│        (MAE)         │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Feature Importance   │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│ Predict Site-Level   │
│  Enrollment Duration │
└──────────┬───────────┘
           ↓
┌──────────────────────┐
│    Rank Sites        │
└──────────────────────┘
🛠️ Technologies

Programming & Analysis

Python
Pandas
NumPy

Machine Learning

Scikit-learn
XGBoost

Visualisation

Matplotlib

Development

Jupyter Notebook
VS Code
Git
GitHub
📁 Project Structure
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
├── .gitignore
├── README.md
└── requirements.txt
🚀 Getting Started
Clone the repository
git clone https://github.com/Uchemadu7Nwachukwu/clinical-trial-feasibility-ml.git
Navigate to the project
cd clinical-trial-feasibility-ml
Create a virtual environment
python -m venv .venv
Activate the environment — Windows
.\.venv\Scripts\Activate.ps1
Install dependencies
pip install -r requirements.txt
Run the analysis

Open:

notebooks/01_site_selection.ipynb

and execute the notebook cells sequentially.

📌 Key Findings
The problem can be approached as a regression task.
Four regression models were compared.
Gradient Boosting produced the lowest MAE on the current test set.
Patient pool was the most influential feature in the tree-based models.
Model predictions can be used to create a ranked list of potential trial sites.
🔭 Future Development

Potential extensions include:

Cross-validation
Hyperparameter optimisation
SHAP model explainability
Actual vs. predicted analysis
Prediction intervals and uncertainty estimation
Additional site and study-level variables
Classification of sites into feasibility categories
Time-to-enrollment forecasting
Validation using appropriately sourced real-world data
⚠️ Limitations

The current dataset is limited to a small number of variables and sites. Model performance may change substantially with larger, more representative datasets.

Predictions should therefore not be used for actual clinical trial site selection without appropriate validation, domain review, governance, and real-world data.

👤 Project

Clinical Trial Feasibility & Site Selection — Machine Learning

Built as a demonstration of applying predictive modelling to clinical trial feasibility and operational decision-making.


Then save it and run:

```powershell
git add README.md
git commit -m "Improve project documentation"
git push
