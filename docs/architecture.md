# 🏗️ Architecture

## Overview
Admission-Prediction is a notebook-centered machine-learning project. The primary executable artifact is `Admission_Predict.ipynb`; its local data source is `admission_predict.csv`.

There is no web server, HTTP API, database, frontend application, scheduled model-training worker, or deployed runtime in the current repository.

## Component flow

```text
admission_predict.csv
        |
        v
pandas DataFrame
        |
        v
Exploratory analysis and preparation
        |
        v
Feature matrix (X) + target (y)
        |
        v
scikit-learn model comparison
  |-- Linear Regression
  |-- Lasso
  |-- SVR
  |-- Decision Tree
  |-- Random Forest
  `-- KNN
        |
        v
Cross-validation and holdout evaluation
        |
        v
Fitted estimator and sample prediction
```

## Main artifacts

| Artifact | Responsibility |
|---|---|
| `Admission_Predict.ipynb` | Data loading, exploration, preparation, model search, evaluation, and sample inference |
| `admission_predict.csv` | Tabular training and evaluation data |
| `README.md` | User-facing project guide |
| `docs/` | Technical documentation |
| `.github/workflows/update-readme.yml` | README timestamp automation |

## Data flow

1. The notebook loads the CSV through a relative path.
2. pandas creates a working DataFrame.
3. The notebook explores distributions and columns.
4. A working copy is used for preparation experiments.
5. The serial identifier is excluded from the final feature matrix.
6. Seven applicant-related fields are used as predictors.
7. The admission-chance field is used as the regression target.
8. Candidate regressors are evaluated with cross-validation.
9. Linear Regression is trained and evaluated on a displayed 80/20 split.
10. A sample feature vector is passed to the fitted model.

## Feature contract

The demonstrated prediction order is GRE, TOEFL, University Rating, SOP, LOR, CGPA, and Research. The order and units must match training. Future reusable inference code should define this contract once, validate it, and prefer named columns.

## Architectural limitations

- Data loading and modeling logic are coupled inside a notebook.
- Dependency versions are not fully pinned.
- There is no independent automated test suite for model behavior.
- Final test data should be isolated from hyperparameter selection.
- Preprocessing should be placed inside an sklearn Pipeline to prevent leakage.
- No model artifact serialization or model registry is configured.

## Recommended evolution

Move data validation, preprocessing, training, evaluation, and inference into tested Python modules if the project grows. Keep the notebook as an explanatory entry point. Record dataset checksum, feature schema, estimator configuration, library versions, and evaluation metrics for each model version.
