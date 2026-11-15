# 🚀 Deployment and Execution

## Current deployment status
This repository is currently a local Jupyter notebook project. It does not contain a production API, web frontend, inference server, database, Docker configuration, or cloud deployment workflow. The supported execution mode is local notebook execution.

## Local run
From the repository root:

```bash
python -m venv .venv
```

Activate the environment, install dependencies, and start Jupyter:

```bash
python -m pip install --upgrade pip
python -m pip install jupyter pandas numpy matplotlib scikit-learn
jupyter notebook Admission_Predict.ipynb
```

The notebook expects `admission_predict.csv` at the relative path it reads.

## Before building a hosted service
1. Verify dataset provenance and redistribution terms.
2. Extract reusable preprocessing and prediction logic into tested Python modules.
3. Create an explicit and validated feature schema.
4. Build a pipeline that prevents preprocessing leakage.
5. Evaluate against an untouched test set.
6. Report MAE, RMSE, R², uncertainty, and appropriate subgroup analysis.
7. Document model version and training-data provenance.
8. Add privacy, security, access, and abuse controls.
9. Establish monitoring and rollback procedures.
10. Obtain domain and legal review before any high-impact use.

A future UI or API must explain that outputs are experimental estimates and must not automate admission decisions.
