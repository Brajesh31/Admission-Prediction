# 🎓 Admission Chance Predictor

<p align="center"><strong>A notebook-based machine learning project for exploring graduate admission chance estimates.</strong></p>
<p align="center"><a href="https://github.com/Brajesh31/Admission-Prediction">Repository</a> · <a href="https://github.com/Brajesh31/Admission-Prediction/issues">Issues</a> · <a href="docs/README.md">Documentation</a> · <a href="LICENSE">MIT License</a></p>

---

## 📚 Table of Contents
1. [Overview](#-project-overview)
2. [Goals and Scope](#-goals-and-scope)
3. [Features](#-features)
4. [Dataset](#-dataset)
5. [Machine Learning Workflow](#-machine-learning-workflow)
6. [Models Compared](#-models-compared)
7. [Evaluation and Results](#-evaluation-and-results)
8. [Repository Structure](#-repository-structure)
9. [Technology Stack](#-technology-stack)
10. [Requirements](#-requirements)
11. [Installation](#-installation)
12. [Running the Notebook](#-running-the-notebook)
13. [Making a Prediction](#-making-a-prediction)
14. [Understanding the Output](#-understanding-the-output)
15. [Reproducibility](#-reproducibility)
16. [Limitations and Responsible Use](#-limitations-and-responsible-use)
17. [Validation](#-validation)
18. [Troubleshooting](#-troubleshooting)
19. [Contributing](#-contributing)
20. [Security and Privacy](#-security-and-privacy)
21. [Roadmap](#-roadmap)
22. [Documentation Index](#-documentation-index)
23. [Citation](#-citation)
24. [License](#-license)

---

## 🎯 Project Overview

**Admission Chance Predictor** is an educational data-science project implemented as a Jupyter notebook. It explores how academic and application-related features in a tabular dataset relate to a numeric admission-chance target.

The notebook uses Python, pandas, NumPy, matplotlib, and scikit-learn. It performs exploratory data analysis, prepares input features, compares regression estimators, uses cross-validation and a train/test split, and demonstrates a sample prediction.

The project is notebook-centered. The repository does **not** currently provide a web application, HTTP API, database, hosted prediction service, user accounts, or automated admissions workflow.

> [!IMPORTANT]
> This is an educational regression experiment. Its output is not a university decision, a guarantee of admission, or a verified personal probability. Do not use it as the sole basis for admissions, scholarships, funding, or other high-impact decisions.

### Project snapshot

| Area | Current implementation |
|---|---|
| Project type | Data science / machine learning notebook |
| Main artifact | `Admission_Predict.ipynb` |
| Dataset | `admission_predict.csv` |
| Learning task | Supervised regression |
| Target | Numeric admission-chance field |
| Predictors | GRE, TOEFL, university rating, SOP, LOR, CGPA, research |
| Model comparison | Linear Regression, Lasso, SVR, Decision Tree, Random Forest, KNN |
| Search | scikit-learn `GridSearchCV` |
| Validation | Five-fold cross-validation and 80/20 holdout split |
| Execution | Local Jupyter Notebook / JupyterLab |
| License | MIT for project materials, subject to third-party terms |

## 🧭 Goals and Scope

This project helps learners understand a small supervised regression workflow: load a structured CSV, inspect distributions, prepare predictors, compare algorithms, evaluate with cross-validation and a holdout split, generate a sample prediction, and reason about model limitations.

It is a learning exercise, not a model of every university's actual admissions process. Real admissions decisions depend on institution-specific policies, applicant context, program capacity, and information not represented in this dataset.

## ✨ Features

### 📊 Exploratory Data Analysis
The notebook loads the CSV into pandas, inspects rows and columns, reviews data distributions, and generates visualizations such as histograms. These analyses describe the sample, they do not establish causation.

### 🧹 Data Preparation
The notebook creates a working copy, separates predictor columns from the target, and excludes the serial-number field from the final feature matrix. It also experiments with replacing zero values in selected rating and score fields with missing values. This assumption must be revisited before extending the model because zero may be meaningful in some datasets.

### 🤖 Regression Model Comparison
Multiple scikit-learn estimators are compared through parameter search. This provides an educational baseline for observing how algorithms behave on a common dataset.

### 🔍 Model Evaluation
Five-fold cross-validation is used during model comparison, followed by an 80/20 train/test example using a fixed random state. The notebook should be improved so final test data is not used during model selection.

### 🔮 Sample Prediction
A fitted estimator receives a seven-feature sample vector. This demonstrates inference mechanics, not the correctness of any real admissions decision.

## 🗃️ Dataset

The notebook reads `admission_predict.csv` from the repository root.

| Field | Meaning | Modeling role |
|---|---|---|
| `Serial No.` | Row identifier | Excluded from model features |
| `GRE Score` | GRE score | Predictor |
| `TOEFL Score` | TOEFL score | Predictor |
| `University Rating` | University rating | Predictor |
| `SOP` | Statement of purpose rating | Predictor |
| `LOR ` | Letter of recommendation rating | Predictor |
| `CGPA` | Grade-point average | Predictor |
| `Research` | Research experience indicator | Predictor |
| `Chance of Admit ` | Numeric target | Regression label |

The notebook cleans or renames some columns during preparation. Raw CSV headers contain whitespace inconsistencies. Inspect and normalize names before building additional code, and keep training and prediction feature order identical.

### Dataset handling rules
- Keep the CSV beside the notebook for its current relative-path load.
- Do not publish private applicant records.
- Do not assume the dataset represents every university, country, degree, discipline, or admissions cycle.
- Verify the original source, provenance, and redistribution rights before sharing the dataset elsewhere.
- Document filtering, missing-value handling, and all transformations.
- Do not assume the repository MIT license automatically covers the dataset.

See [docs/database.md](docs/database.md). Despite its historical filename, this document describes the CSV schema, not a SQL database.

## 🔬 Machine Learning Workflow

The committed notebook follows this broad sequence:

1. Import NumPy, pandas, matplotlib, and scikit-learn utilities.
2. Read `admission_predict.csv`.
3. Inspect columns, summary information, and visual distributions.
4. Create a working data copy.
5. Select GRE, TOEFL, university rating, SOP, LOR, CGPA, and research as predictors.
6. Use the admission-chance field as the regression target, represented as `Probability` after preparation.
7. Compare candidate regressors using GridSearchCV.
8. Use five-fold cross-validation.
9. Split the data into training and test partitions using an 80/20 split and `random_state=5`.
10. Fit Linear Regression and score it on the displayed holdout.
11. Pass an example feature row to `model.predict`.

### Recommended methodology improvements

The current notebook is a learning prototype, not a production evaluation pipeline. Before relying on model results:
- Split off final test data before selecting model parameters.
- Run GridSearchCV only within the training data.
- Put transformations and estimators in a scikit-learn Pipeline.
- Scale features for algorithms sensitive to feature magnitude.
- Fit preprocessing only on training folds.
- Report MAE, RMSE, and R², not only a single score.
- Inspect residuals and prediction ranges.
- Compare the estimator against a simple baseline.
- Record dataset version, package versions, and random seeds.

## 🧠 Models Compared

| Model | Estimator | Search parameters in the notebook |
|---|---|---|
| Linear Regression | `LinearRegression` | Default |
| Lasso | `Lasso` | `alpha`, `selection` |
| Support Vector Regression | `SVR` | `gamma` |
| Decision Tree | `DecisionTreeRegressor` | `criterion`, `splitter` |
| Random Forest | `RandomForestRegressor` | `n_estimators` |
| K-Nearest Neighbors | `KNeighborsRegressor` | `n_neighbors` |

The notebook uses five-fold GridSearchCV. For these regressors, the default scoring is R² unless explicitly changed. Different estimators make different assumptions about data. A comparison is useful only when preprocessing, data split, and evaluation protocol are consistent.

## 📈 Evaluation and Results

The committed notebook outputs show the following historical results:

| Evaluation item | Recorded notebook output |
|---|---:|
| Linear Regression mean five-fold CV score | Approximately 0.8108 R² |
| Random Forest mean five-fold CV score | Approximately 0.7783 R² |
| KNN mean five-fold CV score | Approximately 0.7230 R² |
| Linear Regression score on the 20% holdout | Approximately 0.8215 R² |
| Training rows in displayed split | 400 |
| Test rows in displayed split | 100 |

These are stored notebook outputs, not results independently re-run in every environment. Re-execution may produce different values due to dependency versions, data changes, or execution settings.

**Do not call an R² score “accuracy” for this regression task.** R² measures explained variance relative to a baseline. It is not a percentage chance of predicting admission correctly and does not prove probability calibration.

The notebook has a sample output labeled as a UCLA admission chance. That label is not supported by a verified UCLA admissions process in this repository. Treat it as a generic dataset-based demonstration, not an institution-specific estimate.

## 🗂️ Repository Structure

```text
Admission-Prediction/
├── .github/
│   ├── ISSUE_TEMPLATE/
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/
│       └── update-readme.yml
├── docs/
│   ├── README.md
│   ├── api.md
│   ├── architecture.md
│   ├── database.md
│   ├── deployment.md
│   ├── development.md
│   ├── faq.md
│   ├── installation.md
│   └── troubleshooting.md
├── .editorconfig
├── .env.example
├── .gitattributes
├── .gitignore
├── Admission_Predict.ipynb
├── admission_predict.csv
├── CHANGELOG.md
├── CITATION.cff
├── CODEOWNERS
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE
├── README.md
├── ROADMAP.md
├── SECURITY.md
└── SUPPORT.md
```

| Path | Responsibility |
|---|---|
| `Admission_Predict.ipynb` | Exploration, preparation, model search, evaluation, prediction |
| `admission_predict.csv` | Local tabular dataset |
| `.github/workflows/update-readme.yml` | README timestamp automation |
| `docs/` | Technical documentation |
| `CITATION.cff` | Citation metadata |
| `CONTRIBUTING.md` | Contribution standards |
| `SECURITY.md` | Security reporting and data safety |
| `LICENSE` | Project license |

No first-party Python package, database schema, HTTP service, or deployment target is currently included.

## 🧰 Technology Stack

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Jupyter Notebook | Interactive workflow |
| pandas | Data loading and tabular operations |
| NumPy | Numerical operations |
| matplotlib | Exploratory visualizations |
| scikit-learn | Regression, parameter search, data splitting, evaluation |
| CSV | Local dataset format |
| Git / GitHub | Version control |
| GitHub Actions | README timestamp workflow |

## 💻 Requirements

Recommended: Python 3.9 or newer, pip, Jupyter Notebook or JupyterLab, Git, and a modern operating system with a supported Python distribution.

The notebook metadata currently records Python 3.11.7. The repository does not include a fully pinned dependency lockfile, so results may vary across library versions.

```bash
python --version
python -m pip --version
git --version
```

## 🚀 Installation

### 1. Clone the repository

```bash
git clone https://github.com/Brajesh31/Admission-Prediction.git
cd Admission-Prediction
```

### 2. Create a virtual environment

**Windows PowerShell:**

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**macOS / Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
python -m pip install jupyter pandas numpy matplotlib scikit-learn
```

### 4. Verify imports

```bash
python -c "import numpy, pandas, matplotlib, sklearn; print('Environment ready')"
```

See [docs/installation.md](docs/installation.md) for detailed setup.

## ▶️ Running the Notebook

Start Jupyter from the repository root:

```bash
jupyter notebook Admission_Predict.ipynb
```

Or:

```bash
jupyter lab Admission_Predict.ipynb
```

Run cells from top to bottom using a clean kernel. The notebook reads the CSV using a relative path, so starting Jupyter from another working directory may cause a file-not-found error.

## 🔮 Making a Prediction

The notebook's feature order is:

| Order | Feature |
|---:|---|
| 1 | GRE |
| 2 | TOEFL |
| 3 | University Rating |
| 4 | SOP |
| 5 | LOR |
| 6 | CGPA |
| 7 | Research |

Example:

```python
sample = [[337, 118, 4, 4.5, 4.5, 9.65, 1]]
prediction = model.predict(sample)
print(prediction[0])
```

The estimator must already be fitted. A DataFrame with named columns avoids the feature-name warning stored in the current notebook output:

```python
import pandas as pd

columns = [
    "GRE", "TOEFL", "University Rating",
    "SOP", "LOR", "CGPA", "Research"
]
sample = pd.DataFrame(
    [[337, 118, 4, 4.5, 4.5, 9.65, 1]],
    columns=columns,
)
estimate = model.predict(sample)[0]
print(f"Regression estimate: {estimate:.4f}")
```

This is a code example, not a validated prediction for a named institution.

## 🧾 Understanding the Output

Keep these concepts separate:

- **Regression estimate:** numeric model output.
- **R²:** model fit relative to a baseline, not classification accuracy.
- **Calibration:** agreement between predicted probabilities and observed frequencies. The notebook does not establish calibration.
- **Admission decision:** made by an institution using its own policies and complete application review.

Regression can extrapolate outside the target range. Investigate unusual values rather than silently clipping them and presenting the result as a reliable probability.

## 🔁 Reproducibility

1. Use a fresh virtual environment.
2. Record Python and library versions.
3. Start Jupyter from the repository root.
4. Restart the kernel before a complete run.
5. Execute every cell in order.
6. Keep seeds fixed for comparable experiments.
7. Record dataset version and preprocessing.
8. Preserve evaluation settings and metrics.
9. Remove machine-specific paths and irrelevant outputs before committing.

The displayed split uses `random_state=5`. Exact reproduction across machines is not guaranteed because dependencies are not fully pinned.

## ⚠️ Limitations and Responsible Use

The dataset is a small structured sample. It cannot represent every admissions process, institution, program, applicant background, or application cycle.

Technical limitations requiring further review:
- Raw headers include whitespace inconsistencies.
- The notebook experiments with treating selected zeros as missing.
- The final holdout should be isolated from hyperparameter selection.
- Scaling and preprocessing should be included in a Pipeline.
- The sample prediction emits a feature-name warning when a list is used.
- The UCLA-specific print statement is not evidence of an institution-specific model.
- A regression value is not automatically a calibrated probability.

Do not automatically accept or reject applicants using this model. Do not use it as the sole basis for admissions, scholarships, or funding. Do not claim that a prediction is an official university probability. Do not assume the dataset represents all applicant groups or present statistical association as a causal explanation.

Any future high-impact use would require representative and lawfully obtained data, domain review, calibration and error analysis, subgroup evaluation, privacy controls, human oversight, and legal and ethical review.

## 🧪 Testing and Validation

The repository does not currently define a standalone automated test suite or Python package test command. Validation is performed by executing the notebook.

Import check:

```bash
python -c "import numpy, pandas, matplotlib, sklearn; print('Imports passed')"
```

Notebook checklist:
- [ ] Clean kernel runs all cells in sequence.
- [ ] CSV is loaded from the expected path.
- [ ] Expected columns and numeric types are present.
- [ ] Missing values are counted and handled deliberately.
- [ ] Serial identifier is excluded from features.
- [ ] Feature order matches the prediction input.
- [ ] Final test split is isolated before model tuning.
- [ ] Preprocessing occurs inside cross-validation folds.
- [ ] MAE, RMSE, and R² are reported.
- [ ] Predictions and their interpretation are reviewed.
- [ ] No private records or machine paths are committed.

## 🧯 Troubleshooting

| Problem | Likely cause | Action |
|---|---|---|
| `FileNotFoundError` | Jupyter launched outside repository root | Start Jupyter beside the CSV |
| `ModuleNotFoundError` | Missing package or inactive environment | Activate `.venv` and install dependencies |
| Different scores | Package versions, split, or preprocessing changed | Compare versions and settings |
| Feature-name warning | Model trained with named columns, prediction passed a list | Use a DataFrame with matching names |
| Unexpected prediction | Extrapolation or feature mismatch | Validate units, order, and assumptions |
| Cells fail inconsistently | Notebook cells executed out of order | Restart kernel and run all cells |
| Slow GridSearchCV | Many models and parameter combinations | Reduce search space for iteration only |

See [docs/troubleshooting.md](docs/troubleshooting.md).

## 🤝 Contributing

Contributions that improve reproducibility, correctness, evaluation quality, documentation, and responsible use are welcome.

1. Read [CONTRIBUTING.md](CONTRIBUTING.md).
2. Check existing issues.
3. Keep changes focused.
4. Preserve or version the feature contract.
5. Report the evaluation protocol for model changes.
6. Avoid data leakage.
7. Confirm dataset licensing before redistributing data.
8. Run the notebook from a clean kernel.
9. Update related documentation.

Do not include personal applicant data in public issues or pull requests.

## 🔐 Security and Privacy

The notebook currently requires no API credentials or deployment secrets. Never commit tokens, passwords, private applicant data, or personal datasets. Inspect notebook cells and outputs before executing notebooks from untrusted sources. Review dataset provenance and redistribution rights. Report vulnerabilities privately according to [SECURITY.md](SECURITY.md).

## 🗺️ Roadmap

- [ ] Add a pinned dependency file or reproducible environment specification.
- [ ] Add a data dictionary with provenance and license information.
- [ ] Normalize raw column names at load time.
- [ ] Add schema and missing-value validation.
- [ ] Separate final test data before hyperparameter search.
- [ ] Use pipelines for preprocessing and estimation.
- [ ] Report MAE and RMSE alongside R².
- [ ] Add residual and error analysis.
- [ ] Add subgroup evaluation where methodologically justified.
- [ ] Remove stale notebook warnings and machine-specific output.
- [ ] Add automated notebook execution checks.
- [ ] Package reusable preprocessing and inference logic.
- [ ] Add a model card before considering external use.

These are proposed improvements, not existing features.

## 📖 Documentation Index

| Document | Purpose |
|---|---|
| [Documentation home](docs/README.md) | Navigation and reading paths |
| [Architecture](docs/architecture.md) | Notebook components and data flow |
| [Prediction interface](docs/api.md) | Feature contract and notebook prediction |
| [Dataset schema](docs/database.md) | CSV fields and data handling |
| [Deployment](docs/deployment.md) | Local execution and future-service prerequisites |
| [Development](docs/development.md) | Notebook and model development |
| [FAQ](docs/faq.md) | Common questions |
| [Installation](docs/installation.md) | Environment setup |
| [Troubleshooting](docs/troubleshooting.md) | Common fixes |
| [Changelog](CHANGELOG.md) | Project changes |
| [Roadmap](ROADMAP.md) | Future improvements |
| [Contributing](CONTRIBUTING.md) | Contribution process |
| [Security](SECURITY.md) | Security and data-safety policy |
| [Code of Conduct](CODE_OF_CONDUCT.md) | Community standards |
| [Support](SUPPORT.md) | Help and issue reporting |
| [Citation](CITATION.cff) | Citation metadata |
| [License](LICENSE) | MIT License |

## 📚 Citation

Citation metadata is provided in [CITATION.cff](CITATION.cff). Cite the repository and specify the dataset and model version used in any research or derivative work.

## 📄 License

This repository includes the **MIT License**. See [LICENSE](LICENSE) for the complete terms.

Copyright (c) 2025 Brajesh Kumar.

The project license does not automatically change the license or terms that apply to the dataset or third-party materials. Verify those terms before redistribution.

---

<p align="center"><strong>Learn from data. Evaluate carefully. Use predictions responsibly.</strong></p>

Last updated: 2026-11-17 19:33 UTC
