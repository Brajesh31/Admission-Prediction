# Admission Chance Predictor

This project explores whether a graduate-school applicant's profile can be used to estimate an admission probability. The work is implemented as a Jupyter notebook using the public `admission_predict.csv` dataset and scikit-learn regression models.

## What is included

- `Admission_Predict.ipynb` - exploratory analysis, preprocessing, model comparison, validation, and example predictions.
- `admission_predict.csv` - the tabular dataset used by the notebook.

The notebook uses GRE score, TOEFL score, university rating, statement-of-purpose rating, letter-of-recommendation rating, CGPA, and research experience as input features. The target is the admission chance recorded in the dataset.

## Models and workflow

The notebook:

1. Loads the CSV with pandas.
2. Inspects and prepares the tabular data.
3. Separates applicant features from the admission-chance target.
4. Compares regression approaches, including linear regression and random-forest regression.
5. Uses cross-validation and a reproducible 80/20 train/test split.
6. Fits a final `LinearRegression` model and demonstrates a prediction for a sample applicant.

The prediction is an educational estimate, not an admissions decision or a guarantee of acceptance.

## Requirements

- Python 3.9 or newer
- Jupyter Notebook or JupyterLab
- pandas
- NumPy
- matplotlib
- scikit-learn

Install the dependencies in a virtual environment:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install jupyter pandas numpy matplotlib scikit-learn
```

If PowerShell execution policies prevent activation, run the notebook with the environment's interpreter directly or activate it from a terminal with the appropriate local policy.

## Run the notebook

From the repository root:

```powershell
.\.venv\Scripts\Activate.ps1
jupyter notebook Admission_Predict.ipynb
```

Keep `admission_predict.csv` beside the notebook because the notebook reads it using a relative path:

```python
pd.read_csv("admission_predict.csv")
```

Run the cells from top to bottom. Re-running the notebook from a clean kernel makes the exploratory results and model evaluation reproducible.

## Example input

The notebook demonstrates a feature vector in this order:

```python
[GRE, TOEFL, UniversityRating, SOP, LOR, CGPA, Research]
```

For example:

```python
model.predict([[337, 118, 4, 4.5, 4.5, 9.65, 1]])
```

Use the same feature order and units as the training data. Do not treat predictions as calibrated probabilities unless the model and evaluation process have been explicitly calibrated for that purpose.

## Data and responsible use

The dataset contains applicant-related academic information. Use it only for learning and experimentation, avoid publishing individual records, and do not use this notebook as the sole basis for real admissions, funding, or other high-impact decisions. Review data licensing and provenance before redistributing the CSV.

## Development notes

- Keep notebook outputs manageable and remove machine-specific paths before committing.
- Record changes to preprocessing, features, and model selection in the notebook markdown.
- Compare metrics on a held-out test set and use cross-validation when changing the model.
- Avoid data leakage by fitting transformations only on training data.

## License

This repository does not currently declare a software license. Confirm the license and redistribution terms for the dataset and add an appropriate license file before publishing derived data or model artifacts.

Last updated: 2026-10-20 01:31 UTC
