# Contributing

Thank you for helping improve the Admission Chance Predictor. Contributions should keep the notebook reproducible, explain model changes clearly, and respect the privacy and licensing terms of the dataset.

## Before you start

1. Read the [README](README.md) and inspect the notebook workflow.
2. Check open issues before starting substantial work.
3. Do not commit secrets, private applicant data, generated credentials, or machine-specific paths.
4. Confirm that dataset changes are legally redistributable.

## Development setup

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install jupyter pandas numpy matplotlib scikit-learn
```

Open `Admission_Predict.ipynb` and run it from a clean kernel after changing code or data preparation.

## Notebook and model standards

- Preserve the documented feature order and target definition.
- Use deterministic random seeds when comparing models.
- Separate training and test data before fitting model-specific transformations.
- Report the evaluation metric, split strategy, and relevant model parameters.
- Explain changes to preprocessing, feature selection, and model choice in notebook markdown.
- Do not describe a regression output as a calibrated probability without calibration evidence.
- Keep outputs concise and remove local filesystem paths before committing.

## Pull requests

Use a focused branch and a descriptive commit message. A pull request should include:

- a summary of the change;
- the motivation and expected effect;
- validation performed, including notebook cells or commands run;
- dataset provenance or license information when data changes;
- screenshots or exported charts when visualization behavior changes.

Reviewers may request a clean notebook run, updated documentation, or additional evaluation before merging.

## Reporting problems

Use the repository issue tracker for reproducible bugs, documentation corrections, and improvement proposals. Do not include personal applicant records or confidential information in an issue.
