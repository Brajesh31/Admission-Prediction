# Deployment

This repository is currently designed for local notebook execution and does not contain a production service or deployment configuration.

## Recommended path for future deployment

Before exposing predictions through an API or user interface:

1. Verify the dataset license and provenance.
2. Move preprocessing and model inference into tested Python modules.
3. Version the trained model with its feature schema and training data reference.
4. Add input validation, rate limiting, logging, and privacy controls.
5. Document model limitations and prohibit autonomous admissions decisions.
6. Evaluate accuracy, calibration, and subgroup performance on a held-out dataset.

## Reproducible local run

The supported execution path is:

```powershell
.\.venv\Scripts\Activate.ps1
jupyter notebook Admission_Predict.ipynb
```

Run from the repository root so the relative CSV path remains valid. No cloud credentials, deployment secrets, or hosted service are required by the current notebook.
