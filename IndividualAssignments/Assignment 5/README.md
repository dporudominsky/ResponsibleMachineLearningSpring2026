# Individual Homework 05 — Applied Adversarial Audit on COMPAS

---

## Overview

This project evaluates COMPAS-style prediction models under the security lens introduced in **Lecture 05: ML Security and Abuse Pathways**.

This Assignment 5 deliverable is **based directly on the earlier COMPAS workflow developed in `Assignment 4` and the prior notebook structure used in `Individual Assignments David`**. The analysis keeps the same cleaned-data logic, the same baseline model family, and the same audit-oriented approach, then extends that prior work into **PGD evasion, targeted label poisoning, and membership inference**.

At the same time, the submission is intentionally **standalone**. It does not need the earlier notebooks to run. Instead, it reimplements the prior workflow locally so the notebook can execute top to bottom on its own while still remaining consistent with the earlier assignments.

---

## Dataset

This notebook uses the ProPublica COMPAS two-year dataset:

- `compas-scores-two-years.csv`

The notebook is written to use the local CSV file in the same folder. If the file is missing, it falls back to the original raw GitHub source.

---

## Purpose of the Analysis

The goal of this notebook is to evaluate how the COMPAS models behave when an adversary deliberately tries to manipulate predictions, training data, or privacy exposure.

The notebook performs four main tasks:

1. Run a **PGD evasion audit** on both the logistic regression and gradient-boosted tree models across `epsilon in {0.25, 0.5, 1.0, 2.0}` and report **FPR by race**, **AIR**, and the attack-level fairness implications

2. Extend the **label-flip poisoning loop** to target both African-American and Caucasian defendants, then compare **AUC degradation**, **AIR degradation**, the **stealth zone** where fairness shifts while AUC remains relatively stable, and whether a **PSI-based drift monitor** would detect the attack

3. Build a **shadow-model membership inference pipeline** for both baseline models, compare **membership inference AUC**, visualize **confidence-gap histograms**, and study the effect of **L2 regularization** on the logistic regression privacy-utility tradeoff

4. Write a final **reflection** identifying the highest-risk finding across the notebook, then propose one **proactive** and one **reactive** mitigation with quantified effects from the experimental results

The broader objective is to evaluate the COMPAS models not only for prediction or fairness, but also for **security, privacy, and abuse resilience**.

---

## Models Used

The notebook includes two classification models built on the cleaned COMPAS cohort:

- **Logistic Regression** — used as the interpretable baseline model
- **Gradient-Boosted Tree** — used as the higher-capacity black-box model

The notebook compares these models directly in the **PGD evasion** and **membership inference** sections, while the **poisoning loop** follows the lecture-style black-box attack framing with the gradient-boosted tree as the primary target model.

---

## Python Libraries Used

The notebook uses the following Python libraries:

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `IPython.display`

---

## Files in This Repository

- `IIndividual_Assignment_05_David_Porudominsky_Rotstain.ipynb` — Jupyter Notebook containing the full Assignment 5 implementation
- `Individual_Assignment_05_Report.docx` — formatted written report for submission in Times New Roman, 12 pt
- `README.md` — project documentation for this assignment
---

## Reproducibility Instructions

To reproduce the results:

1. Open the notebook in Jupyter Notebook, JupyterLab, or Google Colab
2. Keep `compas-scores-two-years.csv` in the same folder as the notebook
3. Run all cells from top to bottom in order

If needed, install the required packages with:

```bash
pip install -r requirements.txt
```

Because the notebook rebuilds the full COMPAS workflow internally, it should be run from the beginning so that the cleaned dataset, train/test split, baseline models, attack loops, and audit summaries are generated in sequence.

The written report is also included as a `.docx` file formatted for submission.

---

## Workflow Summary

The notebook includes:

- COMPAS data loading and filtering
- reconstruction of the prior COMPAS modeling workflow used in the earlier assignments
- clean fairness baseline using FPR by race and AIR
- PGD-style evasion attacks on the tabular feature space
- targeted label-flip poisoning with fairness monitoring
- stealth-zone identification
- PSI evidence showing why feature-only drift monitoring can miss label attacks
- shadow-model membership inference for both baseline models
- confidence-gap histograms and generalization-gap comparison
- logistic regression regularization sweep over `C in {0.01, 0.1, 1.0, 10.0}`
- final reflection with quantified mitigation discussion

---

## Notes

This notebook follows the structure presented in **Lecture 05: ML Security and Abuse Pathways**. It is designed to satisfy the assignment requirement for a **clean, standalone notebook** that runs from top to bottom and includes **code, outputs, and short markdown interpretations**.

The key point for correctness is that the assignment is both **derived from the earlier work** and **self-contained for submission**. It uses the same COMPAS pipeline logic established in the earlier materials, but it does not rely on those notebooks being opened or executed alongside it.

---

## Author

**David Porudominsky Rotstain**
