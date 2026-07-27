# lab_2-23MID0381-predictive-analysis

# Breast Mass Malignancy Classification using Decision Trees

![Python](https://img.shields.io/badge/Python-3.12.13-blue.svg)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.6.1-orange.svg)
![pandas](https://img.shields.io/badge/pandas-2.2.2-green.svg)
![Status](https://img.shields.io/badge/Status-Completed-success.svg)

> **Advanced Predictive Analytics (Lab 02)**
> An end-to-end, reproducible, and leakage-safe machine learning workflow for predicting breast mass malignancy using interpretable tree-based classifiers and ensemble methods.

---

## Table of Contents

1. [Overview](#overview)
2. [Datasets](#datasets)
3. [Project Workflow](#project-workflow)
4. [Models Evaluated](#models-evaluated)
5. [Key Results](#key-results)
6. [Repository Structure](#repository-structure)
7. [How to Run](#how-to-run)
8. [Outputs Generated](#outputs-generated)
9. [Reproducibility](#reproducibility)
10. [License](#license)

---

## Overview

This repository contains the implementation, exploratory data analysis (EDA), and technical clinical prediction report for classifying breast masses as **benign** or **malignant**. The project follows a strict predictive analytics workflow, progressing from an unconstrained Decision Tree to a cost-complexity pruned model and finally to a Random Forest ensemble.

Special emphasis is placed on:

- Clinical interpretability
- Prevention of data leakage
- Cost-complexity pruning
- Threshold optimization prioritizing sensitivity
- Responsible Medical AI practices
- Model reproducibility

---

## Datasets

To satisfy multi-dataset diagnostic and robustness requirements, two medical datasets were utilized.

### Breast Cancer Wisconsin Diagnostic Dataset (Primary)

- **Samples:** 569
- **Features:** 30 continuous numerical predictors extracted from digitized fine-needle aspirate (FNA) images
- **Target:** Binary class label
  - 0 = Benign
  - 1 = Malignant

### UCI Heart Disease Dataset (Secondary / Extended Study)

- **Samples:** 303
- **Features:** 13 mixed numerical and categorical variables
- **Target:**
  - 0 = No Heart Disease
  - 1 = Heart Disease Present

The secondary dataset was used to validate the workflow on heterogeneous medical data containing missing values and mixed feature types.

---

## Project Workflow

The project follows an industry-standard predictive analytics pipeline.

1. Fixed random seed (`RANDOM_STATE = 42`) for reproducibility.
2. Performed an 80/20 stratified train-test split before any analysis.
3. Conducted EDA only on the training partition to eliminate data leakage.
4. Built preprocessing pipelines for numerical and categorical variables.
5. Performed Cost-Complexity Pruning using cross-validation.
6. Compared multiple Decision Tree configurations.
7. Trained a Random Forest ensemble for comparison.
8. Optimized decision thresholds to maximize clinical sensitivity.
9. Compared Gini Importance with Permutation Importance.
10. Generated interpretable decision paths and evaluated robustness across multiple random seeds.

---

## Models Evaluated

The following machine learning models were implemented and evaluated using **5-Fold Stratified Cross Validation**.

- Dummy Classifier (Baseline)
- Unconstrained Decision Tree (CART)
- Cost-Complexity Pruned Decision Tree
- Random Forest Classifier

---

## Key Results

The **Pruned Decision Tree** achieved the best balance between predictive performance and interpretability, whereas the **Random Forest** achieved the highest overall predictive accuracy.

### Final Test Performance

| Metric | Pruned CART | Random Forest | Description |
| :--- | :---: | :---: | :--- |
| Sensitivity (Recall) | **95.24%** | **97.62%** | Correct detection of malignant tumors |
| Specificity | **94.44%** | **97.22%** | Correct identification of benign masses |
| ROC-AUC | **0.968** | **0.991** | Overall discrimination ability |
| F1 Score | **0.930** | **0.965** | Balance between Precision and Recall |

### Major Findings

- The unconstrained Decision Tree overfitted the training data (depth = 7 with 16 leaf nodes).
- Cost-Complexity Pruning reduced the model to a compact 3-level tree while improving generalization.
- Threshold optimization significantly reduced False Negatives, an important objective in clinical diagnosis.
- Random Forest achieved the highest predictive performance but sacrificed interpretability.
- Permutation Importance revealed bias in Gini-based feature importance caused by correlated predictors.

---

## Repository Structure

```text
lab_2-23MID0381-predictive-analysis/
│
├── lab_02_23MID0381_Predictive_Analysis.ipynb
├── lab02_decision_tree_artifact.joblib
├── lab02_test_metrics.csv
├── RegistrationNumber_Lab02_ModelCard.md
└── README.md
```

### Repository Contents

| File | Description |
| :--- | :--- |
| `lab_02_23MID0381_Predictive_Analysis.ipynb` | Complete predictive analytics workflow |
| `lab02_decision_tree_artifact.joblib` | Serialized trained model |
| `lab02_test_metrics.csv` | Final test evaluation metrics |
| `RegistrationNumber_Lab02_ModelCard.md` | Responsible AI model documentation |
| `README.md` | Project documentation |

---

# How to Run

## Prerequisites

The project was developed and tested using the following software versions.

| Software | Version |
| :--- | :---: |
| Python | 3.10+ |
| pandas | 2.2.2 |
| scikit-learn | 1.6.1 |
| NumPy | Latest |
| joblib | 1.4.2 |

Install the required packages:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn joblib jupyter
```

---

## Running the Notebook

### Clone the repository

```bash
git clone <repository-url>
```

### Move into the project directory

```bash
cd lab_2-23MID0381-predictive-analysis
```

### Launch Jupyter Notebook

```bash
jupyter notebook
```

### Open the notebook

```
lab_02_23MID0381_Predictive_Analysis.ipynb
```

Run all notebook cells from top to bottom (**Kernel → Restart & Run All**) to reproduce the complete workflow, including data preprocessing, model training, evaluation, visualization, pruning, and model export.

---

## Outputs Generated

Executing the notebook generates the following files.

| Output File | Description |
| :--- | :--- |
| `lab02_decision_tree_artifact.joblib` | Serialized trained Decision Tree model |
| `lab02_test_metrics.csv` | Final evaluation metrics on the test set |
| `RegistrationNumber_Lab02_ModelCard.md` | Responsible AI model card summarizing intended use, performance, limitations, and ethical considerations |

---

## Reproducibility

This project is fully reproducible because it:

- Uses a fixed random seed (`RANDOM_STATE = 42`)
- Performs train-test splitting before model selection
- Prevents target leakage during preprocessing
- Uses Stratified 5-Fold Cross Validation
- Applies Cost-Complexity Pruning
- Stores trained model artifacts
- Exports evaluation metrics
- Documents the workflow using a model card

---

## License

This repository was developed as part of the **Advanced Predictive Analytics Laboratory (Lab 02)** coursework.

It is intended solely for **educational and research purposes**.
