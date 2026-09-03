# Predicting Student Dropout and Academic Success

> Machine learning project to classify student academic outcomes into
> Dropout, Enrolled, and Graduate categories.

## Project Overview

This project analyzes student demographic, socioeconomic, and academic
performance data to predict three academic outcomes:

- Dropout
- Enrolled
- Graduate

The goal is to compare several classification algorithms and identify the
model with the best performance for an imbalanced multiclass classification task.

## Dataset

- **Source:** UCI Machine Learning Repository
- **Dataset:** Predict Students' Dropout and Academic Success
- **Instances:** 4,424 students
- **Features:** 36 input features
- **Target classes:** Dropout, Enrolled, Graduate
- **Data type:** Tabular data
- **License:** CC BY 4.0

Dataset link:
https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success

> Note: The dataset contains demographic, socioeconomic, enrollment, and
> first- and second-semester academic information. Therefore, this model is
> intended for prediction after academic-performance data becomes available,
> not purely at the admission stage.


## Methodology

### Data Preparation

- Loaded the dataset using `pandas`.
- Standardized inconsistent column names.
- Converted numeric columns into appropriate numeric data types.
- Checked missing values and duplicate records.
- No missing values and no duplicate rows were found.

### Target Encoding

| Class | Encoded Value |
|---|---:|
| Dropout | 0 |
| Enrolled | 1 |
| Graduate | 2 |

### Train-Test Split

The dataset was split using stratified sampling:

- Training set: 3,539 records (80%)
- Test set: 885 records (20%)

### Feature Selection

Feature selection was performed only on the training data using:

1. Mutual Information
2. Random Forest Feature Importance

The final feature set was selected from the intersection of the top-ranked
features from both methods, resulting in 11 selected features.

### Class Imbalance Handling

The target classes were imbalanced. SMOTE was applied only to the training data
to balance the class distribution, while the test set remained untouched.

### Models Evaluated

- Decision Tree
- Logistic Regression
- Random Forest
- Support Vector Machine (SVM)

Hyperparameter tuning was performed using `GridSearchCV` with
`StratifiedKFold` cross-validation and macro F1-score as the optimization metric.

## Model Performance

| Model | Accuracy | Precision (Macro) | Recall (Macro) | F1-score (Macro) |
|---|---:|---:|---:|---:|
| Random Forest | **0.7424** | **0.7020** | **0.7009** | **0.6963** |
| SVM | 0.7107 | 0.6942 | 0.6948 | 0.6780 |
| Logistic Regression | 0.7051 | 0.6797 | 0.6825 | 0.6685 |
| Decision Tree | 0.6712 | 0.6315 | 0.6397 | 0.6298 |

**Best model:** Random Forest, based on the highest macro F1-score of 0.6963.


## Limitations

- The dataset represents students from a specific higher-education context, so
  results may not generalize directly to other institutions or countries.
- Some academic-performance features are only available after the first or
  second semester, limiting use for admission-time prediction.
- The Enrolled class has lower predictive performance than the other classes.
- Future work could evaluate additional models and use an imbalanced-learn
  pipeline so SMOTE is applied separately inside each cross-validation fold.



## Team Contribution

| No | Name | Student ID | Task Allocation |
| :---: | :--- | :---: | :--- |
| **1.** | **Hilmi Muhammad Bintang** | 164241004 | <ul><li>Suggested research topics and recommended suitable models for analysis.</li><li>Searched for relevant datasets and outlined the rationale for dataset selection.</li><li>Developed and written code for preprocessing, EDA, data visualization, encoding, and model evaluation.</li><li>Drafted Chapter II (Literature Review) and Chapter IV (EDA section) of the report.</li><li>Prepared presentation slides for Literature Review, Conclusion, and Suggestions.</li></ul> |
| **2.** | **Shahnaz Fatharani Azima** | 164241024 | <ul><li>Built and trained *Support Vector Machine* & *Decision Tree* models.</li><li>Drafted report and presentation slides for Chapter II (Literature Review).</li><li>Drafted report and presentation slides for Chapter IV (Results and Discussion) for *Support Vector Machine* & *Decision Tree* models.</li></ul> |
| <mark>**3.**</mark> | <mark>**Dame Gabriela Silitonga**</mark> | <mark>**164241042**</mark> | <ul><li><mark>Built and trained <b>Logistic Regression</b> & <b>Random Forest</b> models.</mark></li><li><mark>Drafted report and presentation slides for Chapter III (Research Methodology).</mark></li><li><mark>Drafted report and presentation slides for Chapter IV (Results and Discussion) for <b>Logistic Regression</b> & <b>Random Forest</b> models.</mark></li></ul> |
| **4.** | **Ismanisa Ridhan Mutiarso** | 164241043 | <ul><li>Developed code for model evaluation, conducted performance comparison across classification algorithms using Macro F1-score, and generated confusion matrix visualizations for each model.</li><li>Drafted Chapter I (Introduction), including background, problem statement, research objectives, benefits, and scope.</li><li>Drafted Chapter V (Conclusion and Suggestions) based on analysis and evaluation results.</li><li>Edited and formatted the report to ensure consistency in writing, layout, and compliance with guidelines.</li><li>Prepared presentation slides for Introduction and classification method comparisons.</li></ul> |
| **5.** | **Muhammad Iqbal Aulia Fatah** | 164241052 | <ul><li>Developed code for preprocessing, EDA, and feature selection.</li><li>Designed the project flowchart visualization.</li><li>Drafted Chapter III (Research Methodology) for preprocessing section.</li><li>Drafted Chapter IV (Results and Discussion) for EDA and feature selection sections.</li><li>Prepared presentation slides for EDA and feature selection results.</li></ul> |
