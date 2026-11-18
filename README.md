# Customer Churn Prediction Using Machine Learning

A university group project that explores how supervised machine-learning models can identify customers who may leave a service provider. The project includes data preparation, model training and evaluation, prediction utilities, and an interactive Streamlit dashboard.

**Project type:** University group project  
**My role:** Shared contribution to Python data preparation and model implementation (with AI-tool assistance), Streamlit dashboard development, technical report, presentation, and team coordination. Work was completed collaboratively; this repository is not a claim of sole authorship.

## Overview

The workflow uses a Telco customer churn sample dataset to predict the `Churn` target (`No` = Stay, `Yes` = Leave). The included CSV has the customer identifier column removed.

The codebase includes:
- Data loading, validation, cleaning, and preprocessing
- Logistic Regression and Random Forest model training
- Model comparison and selection using F1-score
- Saved model artifacts and metadata
- Command-line prediction utility
- Streamlit dashboard for interactive predictions

## Recorded model evaluation

The project's saved evaluation metadata records the following results. These are the results stored with the supplied trained artifacts; they have not been independently rerun as part of preparing this GitHub copy.

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 73.81% | 50.43% | 78.34% | 61.36% | 84.15% |
| Random Forest | 76.01% | 53.61% | 71.39% | 61.24% | 83.51% |

The metadata identifies Logistic Regression as the selected model based on F1-score. Random Forest has the higher recorded accuracy.

## Repository structure

```text
customer-churn-prediction/
├── app/                  # Streamlit application
├── data/                 # Dataset used by the project
├── models/               # Saved model, preprocessing artifacts, and metadata
├── src/                  # Preprocessing, training, and prediction modules
├── utils/                # Configuration and logging helpers
├── requirements.txt
└── README.md
```

## Setup

Use a Python environment compatible with the package versions in `requirements.txt`. From this repository's root directory:

```bash
python -m venv .venv
```

Activate the environment, then install dependencies:

**Windows (PowerShell):**
```powershell
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

**macOS / Linux:**
```bash
source .venv/bin/activate
pip install -r requirements.txt
```

## Run the dashboard

```bash
streamlit run app/app.py
```

## Retrain the models

```bash
python src/train.py
```

Optional target-column override:

```bash
python src/train.py --target-column Churn
```

Training writes updated model artifacts and evaluation metadata into `models/`.

## Command-line prediction

```bash
echo "{\"tenure\":12,\"MonthlyCharges\":78.5,\"TotalCharges\":\"942.0\",\"Contract\":\"Month-to-month\"}" | python src/predict.py
```

## Technologies

Python, Pandas, NumPy, Scikit-learn, Streamlit, Matplotlib, Seaborn, and Joblib.

## Notes

- This was developed as a collaborative university project. Team members shared implementation, documentation, presentation, and coordination responsibilities.
- AI tools were used as development assistance; they do not replace the team's responsibility for understanding, reviewing, and validating the code.
- The dataset is a sample customer-churn dataset. The `customerID` identifier column has been removed from this public copy because it is not used as a model feature.
- The included `.pkl` files are serialized Python objects. Only load them from this project repository or another trusted source.
