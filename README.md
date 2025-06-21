# Admission Chance Predictor

This project builds a predictive model to estimate the probability of admission to a university based on applicants' academic scores and research experience. It uses Linear Regression (or Logistic Regression) for prediction, with data preprocessing and evaluation steps included.

## Features

- Data cleaning and preprocessing
- Feature selection and engineering
- Model training and evaluation
- Real-time admission chance prediction based on user inputs

## Dataset

The dataset includes features such as GRE score, TOEFL score, University Rating, Statement of Purpose (SOP) rating, Letter of Recommendation (LOR) rating, CGPA, and Research experience.

## Usage

1. Clone the repository:

2. Install required packages:

3. Run the prediction script or Jupyter notebook to train the model and make predictions.

4. Input your scores and get the predicted admission chance.

## Example Prediction

```python
# Example input: GRE, TOEFL, University Rating, SOP, LOR, CGPA, Research
model.predict([[337, 118, 4, 4.5, 4.5, 9.65, 1]])
