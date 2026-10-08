# Student Performance Data Science Project

## Overview

This project analyses the **Student Performance** dataset (Portuguese secondary schools, Mathematics course; 395 students, 33 attributes). The goal is to understand which background and behavioural factors are associated with a student's final grade (`G3`, scale 0-20), to test a few concrete hypotheses, and to build models that predict or group students. The results can support early identification of students at risk of failing.

Throughout the project, preprocessing steps that learn from data (outlier capping, scaling) are fitted on the training split only, and hyper-parameters are tuned by cross-validation on the training set, so the test results are free of data leakage.

## Repository Structure

```
.
├── README.md
├── DATA SCIENCE PRESENTATION.pdf
├── data/
│   ├── student-mat.csv            # raw dataset (input)
│   ├── student_processed.csv      # created by notebook 01
│   └── student_clusters.csv       # created by notebook 05 (optional export)
└── notebooks/
    ├── 01_preprocessing_eda.ipynb
    ├── 02_hypothesis_testing.ipynb
    ├── 03_predictive_modelling.ipynb
    ├── 04_classification.ipynb
    └── 05_clustering.ipynb
```

## Tasks

1. **Preprocessing & EDA (`01`)** - data quality checks, range validation, outlier analysis, row-wise feature engineering, categorical encoding, visual exploration, and export of the processed dataset.
2. **Hypothesis testing (`02`)** - one-sample t-test (mean `G3` vs 10), Welch t-test (urban vs rural students) and chi-square test (higher-education aspiration vs romantic relationship), each with assumption checks, effect sizes and robustness checks.
3. **Predictive modelling (`03`)** - regression of `G3` (baseline, OLS, Ridge, Lasso, Random Forest) with and without earlier grades, model diagnostics, feature importance, and logistic regression for pass/fail.
4. **Classification (`04`)** - decision trees for pass/fail prediction, joint tuning of depth and leaf size, comparison with baselines, and extraction of IF-THEN rules for flagging at-risk students.
5. **Clustering (`05`)** - K-Means segmentation of students with elbow and silhouette analysis, stability checks, comparison with hierarchical clustering, and cluster profiling.

## How to Run

**Requirements:** Python 3.10+ and the packages below.

```bash
pip install pandas numpy scipy scikit-learn statsmodels matplotlib seaborn jupyter
```

**Steps:**

1. Place `student-mat.csv` in the `data/` folder.
2. Start Jupyter from the repository root:
   ```bash
   jupyter notebook
   ```
3. Run the notebooks from the `notebooks/` folder **in order**, from `01` to `05`. Notebook `01` creates `data/student_processed.csv`, which notebooks `02`-`05` read.

> Notebooks use relative paths (`../data/...`), so they must be run from inside the `notebooks/` folder.

## Dataset

https://archive.ics.uci.edu/dataset/320/student+performance

P. Cortez and A. Silva, *Using Data Mining to Predict Secondary School Student Performance*, 2008. Available from the UCI Machine Learning Repository.
