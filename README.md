# Practical Lab 2: Multivariate Linear Regression, Non-Parametric Models and Cross-Validation

## Project Overview

This project explores different machine learning approaches for predicting diabetes disease progression using the Scikit-learn Diabetes dataset.

The objective is to build, evaluate, and compare regression and classification models while investigating the impact of model complexity, feature selection, and generalization.

## Dataset

**Source:** Scikit-learn Diabetes Dataset (`load_diabetes`)

The dataset contains 442 patient observations, 10 input features, and a continuous target representing diabetes disease progression one year after baseline.

Exploratory Data Analysis includes descriptive statistics, histograms, scatter plots, correlation analysis, missing-value checks, and outlier detection.

## Methodology

The dataset is divided into three subsets:

| Dataset | Percentage | Samples |
|---|---:|---:|
| Training | 75% | 331 |
| Validation | 10% | 44 |
| Testing | 15% | 67 |

Regression models are evaluated using R², Mean Absolute Error (MAE), and Mean Absolute Percentage Error (MAPE).

For multivariate modeling, BMI, BP, S3, and S5 are selected using training-only correlation analysis.

## Models Implemented

| Model Family | Configurations |
|---|---|
| Univariate Polynomial Regression | Degrees 0–5 |
| Multivariate Polynomial Regression | Degrees 2 and 3 |
| Decision Tree Regression | Maximum depths 3 and 5 |
| kNN Regression | K = 5 and 10 |
| Logistic Regression | C = 0.1 and 10 |

Logistic Regression is treated as a classification problem by converting continuous progression scores into two categories using the training median threshold. Accuracy, precision, recall, F1-score, and confusion matrices are used for its evaluation.

## Key Results

### Best Univariate Regression Model

Polynomial Regression Degree 4 was selected using validation MAE.

| Test Metric | Result |
|---|---:|
| R² | 0.2401 |
| MAE | 52.3054 |
| MAPE | 43.30% |

### Best Multivariate Regression Model

Polynomial Regression Degree 2 achieved the lowest validation MAE among the regression models.

| Test Metric | Result |
|---|---:|
| R² | 0.5105 |
| MAE | 43.3109 |
| MAPE | 36.33% |

The multivariate model achieved better test performance than the BMI-only model.

### Logistic Regression

The selected Logistic Regression model (C = 0.1) achieved 74.63% test accuracy, 78.12% precision, 71.43% recall, and a 74.63% F1-score.

These results concern above-median versus at-or-below-median progression categories, not exact progression-score predictions.

### Cross-Validation

Five-fold cross-validation was performed on the training dataset for the selected multivariate polynomial model.

| Average Metric | Result |
|---|---:|
| R² | 0.4247 |
| MAE | 47.7628 |
| MAPE | 41.77% |

## Project Structure

```text
Diabetes_Progression_Prediction_Lab2/
├── Practical_Lab_2_Diabetes_Regression.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

The dataset is loaded directly from Scikit-learn, so no external dataset download is required.

## Running the Project

1. Clone or download this GitHub repository.
2. Open the project folder in VS Code.
3. Create a Python virtual environment using `python -m venv .venv`.
4. Activate the virtual environment.
5. Install dependencies using `python -m pip install -r requirements.txt`.
6. Open `Practical_Lab_2_Diabetes_Regression.ipynb`.
7. Select the virtual environment as the Jupyter kernel and run all cells.

## Limitations and Future Improvements

Although multivariate regression improved predictive performance, the models still make substantial errors for individual patients.

Potential improvements include evaluating additional features, regularization, more extensive cross-validation, and testing on independent datasets.

The feature-selection and model-development process should also be repeated in a fully independent experimental evaluation.

**Disclaimer:** This project is intended for educational purposes. The models have not been clinically validated and should not be used for medical screening or diagnosis.

## Conclusion

This lab demonstrates how different machine learning algorithms perform on the same dataset and how model complexity affects generalization.

The results highlight the value of combining multiple patient characteristics, evaluating predictions on unseen data, and considering both statistical performance and practical limitations.