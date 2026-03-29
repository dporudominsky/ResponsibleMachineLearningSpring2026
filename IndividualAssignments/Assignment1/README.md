# Individual Homework 1 — Translating an R Machine Learning Workflow into Python

## Overview
This project reproduces the COMPAS analysis workflow from DNSC 6330 Lecture 01 in Python. The original lecture workflow was written in R and included exploratory data analysis, preprocessing, logistic regression modeling, and fairness-oriented diagnostic evaluation.

The purpose of this notebook is to translate each substantive step of the R workflow into an equivalent Python implementation while preserving the same analytical logic and interpretation.

## Dataset
The analysis uses the ProPublica COMPAS dataset:

- `compas-scores-two-years.csv`

In the notebook, the dataset is loaded directly from the raw GitHub URL to make the workflow fully reproducible.

## Purpose of the Analysis
The notebook performs four main tasks:

1. Load and clean the COMPAS dataset
2. Reproduce the exploratory data analysis from the R workflow
3. Fit a logistic regression model
4. Evaluate model behavior using confusion matrices, group-level metrics, and disparity measures such as false positive rate (FPR) and false negative rate (FNR)

The broader goal is to reproduce the lecture’s statistical and fairness-oriented workflow in Python.

## Python Libraries Used
The notebook uses the following Python libraries:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `statsmodels`
- `IPython.display`

## Files in This Repository
- `Individual_Asingment_01_David_Porudominsky_Rotstain.ipynb` — Jupyter Notebook containing the full Python implementation
- `README.md` — project documentation

## Reproducibility Instructions
To reproduce the results:

1. Clone this repository
2. Open the notebook in Jupyter Notebook, JupyterLab, or Google Colab
3. Run all cells from top to bottom in order
4. The notebook will automatically load the dataset from the raw GitHub source

## Workflow Summary
The notebook includes:

- Data loading from the raw COMPAS CSV
- Data cleaning and filtering
- Variable transformation and factor construction
- Descriptive summaries and visualizations
- Logistic regression estimation
- Predicted probabilities and binary classification
- Overall confusion matrix metrics
- Group-specific fairness diagnostics by race
- Disparity calculations relative to the Caucasian reference group

## Notes
This notebook is intended to conceptually reproduce the original R workflow from class. Minor numerical differences may appear relative to R because Python and R handle categorical variables, defaults, and output formatting somewhat differently, but the analytical interpretation remains the same.

## Author
David Porudominsky Rotstain
