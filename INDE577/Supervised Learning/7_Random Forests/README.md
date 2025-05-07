# Random Forest Classification on Mushroom Dataset

This project applies a **Random Forest Classifier** to the UCI Mushroom dataset to accurately predict whether a mushroom is **edible or poisonous** based on its physical characteristics. The dataset contains fully categorical features, making it ideal for tree-based models like Random Forests.

---

## 1. Objective

To build a predictive model using Random Forests that classifies mushrooms as **edible (`e`) or poisonous (`p`)**, based on 22 categorical attributes. The project also aims to identify the most important features contributing to the classification.

---

## 2. Dataset Overview

- **Dataset Name**: Mushroom (UCI ML Repository)
- **Samples**: 8,124 mushrooms
- **Features**: 22 categorical (e.g., cap-shape, gill-color, odor)
- **Target**: `class` — edible (`e`) or poisonous (`p`)
- **Missing values**: Present in `stalk-root` (represented as `?`)
- **Data Source**: Fetched via `ucimlrepo` (ID = 73)

---

## 3. Preprocessing

- Used `LabelEncoder` to convert all categorical features into numerical format.
- Missing values (`?`) were retained as a unique category during encoding.
- Dataset was split into **training (80%)** and **testing (20%)** sets.

---

## 4. Model and Training

- Used `RandomForestClassifier` from Scikit-learn.
- Initial configuration: `n_estimators=100`, `random_state=42`.
- Trained the model on the encoded feature set and target labels.

---

## 5. Evaluation Results

**Classification Metrics**:
- **Accuracy**: 1.00
- **Precision, Recall, F1-score**: All scores were **1.00** for both classes.
- **Confusion Matrix**:
  - Edible: 843 correctly classified
  - Poisonous: 782 correctly classified
  - No misclassifications

**Interpretation**:
- The Random Forest model achieved **perfect classification performance**.
- The model demonstrates excellent generalization on test data with **zero false positives or false negatives**.

---

## 6. Feature Importance Analysis

Top 5 most important features:
1. `odor` — dominant indicator of edibility
2. `gill-size`
3. `gill-color`
4. `spore-print-color`
5. `population`

**Insights**:
- `odor` alone contributed to more than 16% of the model’s decision power.
- Traits such as `veil-type`, `gill-attachment`, and `cap-shape` had negligible importance, suggesting redundancy or weak correlation with edibility.

---

## 7. Hyperparameter Tuning (GridSearchCV)

Performed 5-fold cross-validation on:
- `n_estimators`: 50, 100, 200
- `max_depth`: None, 5, 10
- `max_features`: 'sqrt', 'log2'

**Best Parameters Found**:
- `n_estimators`: 50
- `max_depth`: None
- `max_features`: 'sqrt'

**Best CV Accuracy**: 1.00

**Interpretation**:
- The model achieves perfect performance with even a modest number of trees.
- The default unconstrained depth (`None`) effectively captures all feature interactions.

---

## 8. Conclusion

- The **Random Forest Classifier** achieved **100% accuracy** on the Mushroom dataset.
- The most critical feature was clearly **odor**, followed by other gill-related characteristics.
- The model demonstrates excellent performance, strong interpretability, and resilience to categorical feature complexity.
- This project highlights how Random Forests can deliver highly accurate and interpretable results on structured classification tasks.

---


