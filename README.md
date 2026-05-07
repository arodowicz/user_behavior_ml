# user_behavior_ml

This repository contains a single notebook for predicting whether a user is on the Ultra plan based on user behavior data.

## Files

- `user_behavior.ipynb` — Loads the dataset, prepares training and testing splits, evaluates baseline and candidate models, and selects the final classifier.

## Dataset

- `users_behavior.csv` is loaded from `/datasets/users_behavior.csv`.
- The target column is `is_ultra`.
- All other columns are used as features.

## Workflow

1. Load the dataset and inspect its structure.
2. Split the data into training, validation, and test sets in a 60/20/20 ratio.
3. Train and evaluate three classifiers:
   - `DecisionTreeClassifier` to tune maximum depth.
   - `RandomForestClassifier` to tune number of estimators and tree depth.
   - `LogisticRegression` as a linear baseline.
4. Compare validation accuracy and choose the best performer.
5. Train the final model on the training set and evaluate on the test set.
6. Compare the final model accuracy to the baseline majority-class accuracy.

## Modeling Summary

- `DecisionTreeClassifier` achieved the best validation accuracy around 0.79.
- `RandomForestClassifier` achieved the best validation accuracy around 0.803.
- `LogisticRegression` did not meet the minimum accuracy requirement.
- Final selected model: `RandomForestClassifier` with `n_estimators=30` and `max_depth=7`.
- Final test accuracy: approximately `0.804`.
- Baseline majority-class accuracy: approximately `0.6935`.

## Notes

- The notebook uses scikit-learn for model training and evaluation.
- The main objective is binary classification of ultra plan users.
- If desired, the notebook can be extended with feature engineering, cross-validation, and additional model comparison.
