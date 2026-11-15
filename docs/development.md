# 🧑‍💻 Development Guide

## 1. Environment
Use a dedicated Python virtual environment. Follow [installation.md](installation.md).

```bash
python -m pip install jupyter pandas numpy matplotlib scikit-learn
```

## 2. Contributor workflow
1. Pull the latest default branch.
2. Create an isolated working branch.
3. Review the notebook and dataset schema.
4. Make a focused change.
5. Restart the kernel.
6. Run all cells from top to bottom.
7. Inspect metrics, warnings, and notebook outputs.
8. Remove machine-specific paths and private data.
9. Update documentation.
10. Submit a focused pull request.

## 3. Notebook standards
Keep explanations near relevant cells. Use meaningful variables. Avoid hidden dependencies on cell execution order. Restart and run all cells before publishing. Keep outputs manageable and remove local paths or sensitive records. Preserve or explicitly version the seven-feature order.

## 4. Modeling standards
- Split final test data before selecting model parameters.
- Run GridSearchCV only within training data.
- Put transformations and estimators in a scikit-learn Pipeline.
- Scale features for algorithms sensitive to feature magnitude.
- Set random seeds for stochastic estimators and split operations.
- Report MAE, RMSE, and R².
- Compare against a baseline.
- Inspect residuals and prediction ranges.
- Do not interpret feature associations as causal effects.
- Do not call R² "accuracy" for a regression task.

## 5. Reproducibility record

| Item | Information to record |
|---|---|
| Python | Runtime version |
| Libraries | pandas, NumPy, matplotlib, scikit-learn versions |
| Dataset | Source, version, checksum, date |
| Preparation | Renaming, filtering, missing-value logic |
| Split | Strategy and random seed |
| Model | Estimator and parameters |
| Evaluation | CV scheme and held-out metrics |

## 6. Validation

```bash
python -c "import numpy, pandas, matplotlib, sklearn; print('Imports passed')"
```

Then restart the kernel and run the entire notebook. No standalone test suite or CI notebook-execution job is currently configured.

## 7. Review checklist
- [ ] Feature names and order remain consistent.
- [ ] No target leakage is introduced.
- [ ] Test data is not used for tuning.
- [ ] Preprocessing is fitted only within appropriate folds.
- [ ] Metrics and parameters are recorded.
- [ ] Data provenance and license are understood.
- [ ] No private records or secrets are committed.
- [ ] Documentation reflects actual behavior.
