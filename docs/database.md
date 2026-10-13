# Data storage and schema

The project does not use a database. Its source data is the local CSV file `admission_predict.csv`, loaded directly by the notebook.

## Logical schema

The dataset represents one applicant per row. The primary feature fields are:

- GRE score
- TOEFL score
- university rating
- statement-of-purpose rating
- letter-of-recommendation rating
- CGPA
- research experience

The target is the admission chance value used for regression.

## Data handling

Keep the CSV beside the notebook, preserve its header names, and verify row counts and data types after changes. Do not add private applicant information or commit derived data without confirming redistribution rights.

## Future storage

If the project grows beyond notebook experimentation, use a versioned data contract and store dataset metadata separately from model artifacts. Record the source, collection date, license, preprocessing version, and a checksum for each training dataset.
