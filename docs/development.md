# Development

## Workflow

1. Create or activate the project virtual environment.
2. Make a focused change to the notebook or documentation.
3. Run the notebook from a clean kernel.
4. Check expected columns, feature order, and model metrics.
5. Review outputs for private data and machine-specific paths.
6. Update documentation and submit a focused pull request.

## Notebook standards

Keep markdown explanations near the cells they describe. Use fixed random seeds when comparing models, record evaluation settings, and avoid fitting preprocessing steps on the full dataset before the test split.

## Reproducibility

Run from the repository root with the CSV in its expected location. Capture the Python version and dependency versions when results are important. Do not commit virtual environments, notebook checkpoints, or generated caches.

## Change review

Use `git diff --check` before committing. For model changes, report the baseline and new metrics rather than relying on a visual impression. Explain changes to data cleaning and feature engineering because they can affect results more than the estimator itself.
