# Roadmap

This roadmap describes possible improvements to the Admission Chance Predictor. Priorities may change as the dataset, notebook goals, and contributor feedback evolve.

## Near term

- Add a reproducible dependency lock or environment file.
- Replace machine-specific notebook paths and remove stale warning output.
- Add a clear data dictionary with units, ranges, missing-value rules, and provenance.
- Report multiple regression metrics, including MAE, RMSE, and R².
- Add notebook checks for expected columns and data types.

## Medium term

- Compare regularized regression and tree-based models with a consistent evaluation protocol.
- Add preprocessing pipelines that prevent leakage.
- Add residual analysis and subgroup error analysis.
- Calibrate or rename the output so its statistical interpretation is explicit.
- Add automated notebook execution in a non-YAML local validation script or documented command.

## Long term

- Package the predictor as a small, versioned Python module.
- Add a documented command-line or web interface.
- Version datasets and model artifacts with reproducible metadata.
- Publish model limitations, fairness considerations, and a model card before any real-world use.

## Non-goals

The project is not intended to make autonomous admissions decisions or replace institutional review. Any future interface must preserve that limitation.
