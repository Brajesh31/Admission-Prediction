# 🤝 Contributing to Admission Chance Predictor

Thank you for considering a contribution. The most valuable improvements make the notebook more reproducible, the evaluation more statistically sound, the documentation more accurate, and the project safer to interpret.

## 📚 Before you start

1. Read the [README](README.md) and documentation in [docs/](docs/README.md).
2. Check open issues and pull requests for existing work.
3. Understand the notebook's current feature order and target.
4. Verify the dataset's provenance and license before changing or redistributing it.
5. Never commit private applicant records, credentials, personal information, or machine-specific paths.

## 🛠️ Development setup

```bash
python -m venv .venv
```

Activate the environment, then install:

```bash
python -m pip install --upgrade pip
python -m pip install jupyter pandas numpy matplotlib scikit-learn
```

Start the notebook from the repository root:

```bash
jupyter notebook Admission_Predict.ipynb
```

## 📓 Notebook contribution standards

- Keep explanatory Markdown beside the code it explains.
- Use meaningful variable names and avoid hidden cell-order dependencies.
- Restart the kernel and run all cells before submitting.
- Keep outputs concise and remove irrelevant execution artifacts.
- Avoid committing local absolute paths or sensitive data.
- Preserve the documented predictor order or explicitly version the feature contract.
- Add a data dictionary when introducing or renaming fields.

## 🧠 Machine-learning standards

- Split off final test data before model selection.
- Perform hyperparameter tuning only inside training data.
- Use scikit-learn Pipelines for preprocessing and estimators.
- Fit transformations within training folds to prevent leakage.
- Apply scaling when the selected estimator requires it.
- Set and document random seeds where relevant.
- Report MAE, RMSE, and R² where appropriate.
- Compare against a baseline and inspect residuals.
- Do not call R² "accuracy" for regression.
- Do not describe an uncalibrated regression value as a verified admission probability.
- Do not claim causal conclusions from feature correlations.

## 🔎 Pull request checklist

A focused pull request should include:
- [ ] A clear summary and motivation.
- [ ] The affected files or notebook sections.
- [ ] A clean notebook run or an explanation of what could not be run.
- [ ] Metrics and evaluation protocol for model changes.
- [ ] Dataset source and license details if data changes.
- [ ] Updated documentation and changelog where needed.
- [ ] No secrets, private data, or unrelated notebook output.
- [ ] A review of the resulting diff.

## 🐛 Reporting a problem

Open an issue with a descriptive title, expected behavior, actual behavior, reproduction steps, Python version, and relevant package versions. Remove private applicant records and personal data from screenshots or logs.

## 💬 Conduct

All participants must follow the [Code of Conduct](CODE_OF_CONDUCT.md). Security issues should be reported privately using [SECURITY.md](SECURITY.md).

## ✅ Review approach

Contributions are reviewed for correctness, clarity, reproducibility, data handling, and alignment with the project's educational purpose. A submission is not guaranteed to be merged; reviewers may request changes or additional evidence.
