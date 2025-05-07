# Gradient Boosting Classification on Titanic Dataset

This project applies a **Gradient Boosting Classifier** to predict passenger survival on the Titanic based on demographic and ticket features. The model is evaluated using accuracy, precision/recall metrics, AUC score, and feature importance.

---

## 1. Objective

To predict whether a passenger survived the Titanic disaster (`Survived = 1`) or not (`Survived = 0`) using structured passenger data. Gradient Boosting is used to handle potential non-linearities and feature interactions.

---

## 2. Dataset Overview

- **Dataset**: Titanic (from seaborn / Kaggle)
- **Target Variable**: `survived`
- **Sample Size**: 891 passengers (after preprocessing)
- **Features Used**:
  - Categorical: `sex`, `embarked`, `pclass`, `alone`
  - Numerical: `age`, `fare`, `sibsp`, `parch`

Missing values in `age` and `embarked` were handled via median and mode imputation respectively. Categorical variables were label encoded.

---

## 3. Model & Training

- **Algorithm**: `GradientBoostingClassifier` from `sklearn`
- **Hyperparameters**:
  - `n_estimators`: 100
  - `learning_rate`: 0.1
  - `max_depth`: 3
  - `random_state`: 42

Train-test split: 80% training / 20% testing.

---

## 4. Model Evaluation

**Accuracy**: `0.79`  

**Classification Report**:
- Class 0 (did not survive):  
  - Precision: 0.78, Recall: 0.88, F1: 0.82
- Class 1 (survived):  
  - Precision: 0.81, Recall: 0.68, F1: 0.74

**Macro Avg F1-Score**: `0.78`  
**Weighted Avg F1-Score**: `0.79`

### Interpretation:
- The model predicts non-survivors well (high recall = 0.88), but has some difficulty capturing all survivors.
- Balanced precision and recall across both classes.
- Suggests possible class imbalance or overlap in survival features.

---

## 5. ROC Curve & AUC

- **AUC Score**: `0.821`
- The ROC curve indicates strong separability between the two classes.
- The model performs significantly better than random (baseline AUC = 0.5).

---

## 6. Feature Importance

Top features ranked by importance:

| Feature    | Importance |
|------------|-------------|
| `sex`      | ~45%        |
| `pclass`   | ~18%        |
| `age`      | ~18%        |
| `fare`     | ~10%        |
| `sibsp`    | ~6%         |

### Insights:
- **Sex** is the dominant predictor (consistent with historical survival patterns).
- **Passenger class** and **age** also significantly affect survival.
- `embarked`, `parch`, and `alone` had minimal influence on the model's decisions.

---

## 7. Conclusion

Gradient Boosting achieves **strong performance** in Titanic survival prediction:

- **Accuracy**: 79%
- **AUC**: 0.82
- Clear feature importance and well-calibrated precision/recall balance

### Recommendations:
- Explore hyperparameter tuning (`max_depth`, `learning_rate`)
- Use SMOTE or `class_weight` to improve recall on survivors
- Engineer additional features such as `family_size` or `title`

This project showcases how Gradient Boosting can effectively model structured tabular data and provide interpretable feature insights in binary classification problems.

