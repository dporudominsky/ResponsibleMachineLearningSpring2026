# Individual Homework 3 — Disparate Impact, Intersectional Fairness, and Error-Rate Auditing in COMPAS

---

## Overview

This project extends the COMPAS analysis developed in the earlier homework assignments. The previous sections of the notebook establish the workflow for loading, cleaning, and preparing the COMPAS dataset, fitting predictive models, and examining explanation methods in Python.

This notebook continues that work by focusing on **disparate-impact measurement, subgroup fairness auditing, intersectional analysis, and governance-oriented reporting**.

The Assignment 3 section follows the structure of **Lecture 03: Algorithmic Bias Measurement** and applies those ideas directly to the COMPAS models built earlier in the notebook.

---

## Dataset

This analysis uses the ProPublica COMPAS dataset:

- `compas-scores-two-years.csv`

The notebook relies on the cleaned COMPAS cohort created in the earlier sections and uses that processed data as the basis for the Assignment 3 fairness audit.

---

## Purpose of the Analysis

This notebook moves beyond model prediction and explanation to evaluate whether the fitted models produce outcomes that raise **group-level fairness and disparate-impact concerns**.

The notebook performs five main tasks:

1. Compute **AIR (Adverse Impact Ratio)**, **ME (Marginal Effect)**, and **SMD (Standardized Mean Difference)** for race and sex using the Solas-AI disparity workflow

2. Build an **intersectional analysis** for race × sex and identify the subgroup with the lowest AIR relative to the Caucasian male reference group

3. Compute **false positive rate (FPR)** and **false negative rate (FNR)** disparities by race and test those differences with a **two-proportion z-test**

4. Produce a **publication-style figure** showing FPR and FNR by race with the Caucasian group used as the visual reference baseline

5. Write a **regulator-facing compliance memo** summarizing the main findings, limitations, and recommended monitoring steps

The broader goal is to evaluate the COMPAS models not only in terms of predictive behavior, but also in terms of **group fairness, legal exposure, and auditability**.

---

## Models Used

The notebook includes two models trained on the cleaned COMPAS data:

- **Logistic Regression** — used as an interpretable baseline
- **Gradient-Boosted Tree** — used as the main black-box model for the fairness audit

The Assignment 3 discussion emphasizes the **gradient-boosted tree** while also checking whether the logistic regression shows the same overall disparity pattern.

---

## Python Libraries Used

The notebook uses the following Python libraries:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `statsmodels`
- `scikit-learn`
- `shap`
- `lime`
- `dice-ml`
- `solas-ai`

---

## Files in This Repository

- `Individual_Assigment_03_David_Porudominsky_Rotstain.ipynb` — Jupyter Notebook containing the full Assignment 3 implementation
- `DNSC_6330_Lecture-03.pdf` — Lecture 3 slides used as the methodological reference
- `README.md` — Project documentation

---

## Reproducibility Instructions

To reproduce the results:

1. Open the notebook in Jupyter Notebook, JupyterLab, or Google Colab
2. Run all cells from top to bottom in order
3. Allow the package-installation cells to finish before moving on

If needed, install the required packages used in the notebook:

- `shap`
- `lime`
- `dice-ml`
- `solas-ai`

Because the Assignment 3 section depends on preprocessing, feature engineering, and model objects created earlier in the notebook, it should be run in full from the beginning so that all required variables and models are created in sequence.

If the notebook is run in Google Colab, internet access is required because the COMPAS dataset is read from GitHub.

---

## Workflow Summary

The notebook includes:

- loading and cleaning the COMPAS dataset
- preparing model features and train/test splits
- fitting logistic regression and gradient-boosted tree classifiers
- model explanation work from the earlier sections of the notebook
- Solas-AI disparity analysis for race and sex
- manual verification of AIR values using direct selection-rate calculations
- intersectional subgroup analysis for race × sex
- FPR and FNR disparity testing by race using two-proportion z-tests
- a publication-style fairness visualization
- a compliance memo based on the audit results

---

## Notes

This notebook combines the COMPAS workflow, explainability analysis, and fairness audit in one file. The Assignment 3 section specifically emphasizes **bias measurement, disparate-impact testing, and subgroup evaluation**.

The fairness results should be interpreted with care because some demographic subgroups are very small, and the reported metrics are based on a single train-test split. For that reason, the notebook treats the Assignment 3 analysis as an audit-style diagnostic rather than a final causal claim.

The compliance memo at the end of the notebook is written in the style of a short report to a regulator or auditor reviewing the fairness implications of the model outputs.

---

## Author

**David Porudominsky Rotstain**
