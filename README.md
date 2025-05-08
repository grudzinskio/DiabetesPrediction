# Diabetes Prediction Using Random Forest

This project investigates whether clinical variables can be used to predict diabetes in patients, using machine learning techniques and statistical hypothesis testing.

## Team Members
- Oliver Grudzinski  
- Pranaav Paladugu  
- Alec Weinbender  

---

## Dataset Overview

- **Source:** [Pima Indians Diabetes Database](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database)  
- **Population:** Female patients aged 21+ of Pima Indian heritage  
- **Features:**  
  - `Pregnancies`  
  - `Glucose`  
  - `BloodPressure`  
  - `SkinThickness`  
  - `Insulin`  
  - `BMI`  
  - `DiabetesPedigreeFunction`  
  - `Age`  
- **Target Variable:**  
  - `Outcome`: 1 = Diabetes, 0 = No Diabetes  

---

## Hypothesis Testing

We performed Kruskal-Wallis tests (non-parametric) with Bonferroni correction to determine variable significance.

### Significant Variables:
- `Glucose`  
- `Age`  
- `Pregnancies`  

### Not Significant:
- `BMI`  
- `Insulin`  
- `SkinThickness`  
- `BloodPressure`  
- `DiabetesPedigreeFunction`  

---

## Data Preprocessing

- Replaced zeros in `Glucose`, `BloodPressure`, `SkinThickness`, `Insulin`, and `BMI` with the column mean  
- Verified there were no null values  
- Retained all eight features for baseline modeling  

---

## Machine Learning Models

We used a Random Forest Classifier, optimizing `max_leaf_nodes` and `n_estimators` through validation accuracy.

### Model Parameters:
- `max_leaf_nodes = 25`  
- `n_estimators = 25`  

### Model Results:

| Model              | Accuracy | F1 Score | Precision | Recall |
|-------------------|----------|----------|-----------|--------|
| Baseline           | 77.06%   | 0.6241   | 0.7333    | 0.5432 |
| Significant Only   | 71.86%   | 0.5578   | 0.6212    | 0.5062 |
| Greedy Feature Add | 77.49%   | 0.6533   | 0.7101    | 0.6049 |

---

## Greedy Feature Selection

Features added based on incremental accuracy improvement:

1. `Glucose`  
2. `BMI`  
3. `Age`  
4. `DiabetesPedigreeFunction`  
5. `Pregnancies`  

---

## Feature Importance (Baseline Model)

1. `Glucose`  
2. `BMI`  
3. `Age`  
4. `DiabetesPedigreeFunction`  
5. `Insulin`  

---

## Conclusion

- Glucose, Age, and Pregnancies are statistically significant predictors of diabetes.
- A greedy feature selection strategy yielded the best F1 score and precision.
- This project demonstrates that with minimal clinical inputs, diabetes diagnosis can be reasonably predicted using machine learning models.

---

## Future Work

- Compare with logistic regression or neural networks  
- Expand dataset to include more diverse populations  
- Use SHAP values for explainability