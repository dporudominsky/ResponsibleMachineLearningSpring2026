# Individual Homework 2 — Model Explainability, Counterfactuals, and Governance in COMPAS

---

## Overview

This project extends the COMPAS analysis developed in **Individual Homework 1**. Assignment 1 served as the base workflow for loading, cleaning, and preparing the COMPAS dataset, as well as reproducing the initial predictive and fairness-oriented analysis in Python.

This notebook builds on that foundation by focusing on **model explainability, local interpretation, counterfactual recourse, and governance-oriented evaluation**.

For background on the original data preparation and baseline analytical workflow, please refer to **Individual Homework 1**.

---

## Dataset

This analysis uses the same ProPublica COMPAS dataset used in Assignment 1:

- `compas-scores-two-years.csv`

The notebook continues from the cleaned COMPAS cohort created in the earlier assignment and uses that processed data as the basis for the explainability analysis.

---

## Purpose of the Analysis

This notebook moves beyond model fitting and evaluates how a predictive model behaves for specific individuals and groups.

The notebook performs four main tasks:

1. Compute **SHAP values** for the gradient-boosted tree model and produce:
   - a global beeswarm summary plot
   - waterfall plots for the highest-risk and lowest-risk defendants in each racial group

2. Run **LIME** on the same four individuals and compare the local feature attributions from LIME and SHAP

3. Generate **counterfactual explanations using DiCE** and identify the feature changes needed to flip predictions, while checking whether any counterfactuals require changes to immutable features such as race or sex

4. Write a **governance memo** summarizing what the explanation methods reveal about model behavior, what their limitations are, and what additional monitoring should be recommended

The broader goal is to evaluate a black-box classification model not only in terms of predictive performance, but also in terms of **interpretability, recourse, and governance**.

---

## Models Used

The notebook includes two models built on the cleaned COMPAS data:

- **Logistic Regression** — used as an interpretable baseline
- **Gradient-Boosted Tree** — used as the main black-box model for explanation analysis

The explainability and counterfactual tasks are centered primarily on the **gradient-boosted tree model**.

---

## Python Libraries Used

The notebook uses the following Python libraries:

- `pandas`
- `numpy`
- `matplotlib`
- `scikit-learn`
- `lime`
- `shap`
- `dice-ml`

---

## Files in This Repository

- `Individual_Assingment_02_David_Porudominsky_Rotstain.ipynb` — Jupyter Notebook containing the full Assignment 2 implementation
- `README.md` — Project documentation

---

## Reproducibility Instructions

To reproduce the results:

1. Clone this repository
2. Open the notebook in Jupyter Notebook, JupyterLab, or Google Colab
3. Run all cells from top to bottom in order

If needed, install the required packages used in the notebook:

- `lime`
- `shap`
- `dice-ml`

Because this notebook builds on the cleaned data and workflow from Assignment 1, it should be run in full from the beginning so that all preprocessing, feature engineering, model fitting, and explanation objects are created in sequence.

---

## Workflow Summary

The notebook includes:

- continuation of the COMPAS workflow from Assignment 1
- feature preparation, including conversion of jail-date fields into numeric form
- train/test split on the cleaned dataset
- construction of preprocessing pipelines for numeric and categorical variables
- fitting of logistic regression and gradient-boosted tree classifiers
- group-level performance comparison by race
- SHAP global and local explanation analysis
- LIME local explanation analysis for selected individuals
- DiCE counterfactual generation for selected individuals
- a governance memo discussing findings, limitations, and recommendations

---

## Notes

This notebook is intended to extend the analytical foundation established in **Individual Homework 1**. Assignment 1 covers the original data preparation, exploratory analysis, logistic modeling, and fairness metrics. Assignment 2 builds on that work by focusing on **explainability, recourse, and governance**.

As with many explainability methods, local explanations may vary across techniques, especially for lower-importance features. For that reason, the notebook emphasizes agreement on major drivers while also discussing the limitations of explanation tools and the caution required when interpreting counterfactual recommendations.

---

## Author

**David Porudominsky Rotstain**
