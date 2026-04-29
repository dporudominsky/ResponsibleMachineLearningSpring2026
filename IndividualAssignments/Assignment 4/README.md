[README.md](https://github.com/user-attachments/files/27219503/README.md)
# Individual Homework 4 — From Accuracy to Accountability: Stress Testing a Predictive Model

## Overview
This repository contains the fourth individual assignment for DNSC 6330 Responsible Machine Learning. The notebook extends the earlier COMPAS workflow and reframes it as a reliability audit based on the Lecture 04 requirements.

Instead of reporting only a single model score, the analysis evaluates how stable and trustworthy the predictive pipeline is under distribution shift, train-test generalization, attribute swaps, feature perturbations, and subgroup slicing.

## Grading Alignment
The notebook is organized to match the Lecture 04 grading guidance for the individual coding homework:

- **Correctness of implementation**: all five required technical sections are implemented directly in Python
- **Code clarity and reproducibility**: the notebook is standalone, uses a local copy of the COMPAS CSV, and runs from top to bottom
- **Interpretation quality**: each section includes short written interpretations rather than only raw metrics
- **Evidence of audit-level reasoning**: the notebook ends with a governance-oriented memo that explains what the results mean, what they miss, and what actions they justify

## Assignment Scope
The notebook covers the five coding tasks from Lecture 04:

1. **Distribution drift**
   - PSI and KS tests for numeric features
   - MMD in the encoded feature space
   - train-versus-test score distribution comparisons
2. **Generalization**
   - train and test AUC
   - train and test accuracy
   - train and test log loss
   - overfitting diagnosis through performance gaps
3. **Spurious-correlation probe**
   - counterfactual-style swaps on selected protected attributes
   - change in predicted probabilities under those swaps
4. **Robustness**
   - `priors_count` stress testing
   - ICE curves
   - sensitivity summaries and threshold-flip analysis
5. **Slice-based evaluation**
   - performance comparison by race, sex, and age category

The notebook ends with an audit-style memo that interprets the results and explains what actions they justify.

## Files
- `Individual_Assigment_04_David_Porudominsky_Rotstain.ipynb` — complete Assignment 4 notebook
- `compas-scores-two-years.csv` — COMPAS dataset used by the notebook
- `DNSC_6330_Lecture-04.pdf` — lecture reference used for the assignment
- `README.md` — project documentation

## Methods And Models
The notebook keeps the same general COMPAS preprocessing workflow used in the earlier assignments so that the audit remains comparable to the prior work.

The main models are:

- **Logistic Regression** as an interpretable baseline
- **Gradient-Boosted Tree** as the primary black-box model under audit

## Python Libraries Used
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scipy`
- `scikit-learn`
- `IPython.display`

## How To Run
1. Open the notebook in Jupyter Notebook, JupyterLab, VS Code, or Google Colab.
2. Keep `compas-scores-two-years.csv` in the same folder as the notebook.
3. Run the notebook from top to bottom in order.

The notebook first tries to load the local CSV file. If the file is missing, it falls back to the public ProPublica source URL.

## Reproducibility Notes
- The notebook is self-contained and does not depend on the earlier assignment notebooks.
- It preserves the earlier modeling structure so the Assignment 4 results can be interpreted as an audit of the same general pipeline rather than a new modeling exercise.
- Because the analysis uses a single train-test split, the reported drift, robustness, and slice findings should be treated as audit signals rather than final causal conclusions.

## Author
**David Porudominsky Rotstain**
