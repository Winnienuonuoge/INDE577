# Supervised Learning: Logistic Regression  
**Dataset**: Pima Indians Diabetes Dataset

## 1. Research Objective

This project applies Logistic Regression to predict the likelihood of diabetes based on medical diagnostic features such as glucose level, BMI, and insulin levels. This is a binary classification problem where the goal is to distinguish between diabetic and non-diabetic patients.

## 2. Dataset Description

- **Source**: UCI Machine Learning Repository  
- **Samples**: 768 female patients  
- **Features**:
  - Pregnancies
  - Glucose
  - BloodPressure
  - SkinThickness
  - Insulin
  - BMI
  - DiabetesPedigreeFunction
  - Age
- **Target Variable**:  
  - Outcome: 0 = Non-diabetic, 1 = Diabetic

## 3. Logistic Regression Implementation

```python
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import classification_report, confusion_matrix, roc_auc_score, roc_curve

# Load dataset
url = "https://raw.githubusercontent.com/jbrownlee/Datasets/master/pima-indians-diabetes.data.csv"
columns = ['Pregnancies', 'Glucose', 'BloodPressure', 'SkinThickness', 'Insulin',
           'BMI', 'DiabetesPedigreeFunction', 'Age', 'Outcome']
df = pd.read_csv(url, names=columns)

# Train-test split
X = df.drop("Outcome", axis=1)
y = df["Outcome"]
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train model
model = LogisticRegression(max_iter=200)
model.fit(X_train, y_train)

# Predict & Evaluate
y_pred = model.predict(X_test)
print(confusion_matrix(y_test, y_pred))
print(classification_report(y_test, y_pred))
print("ROC-AUC Score:", roc_auc_score(y_test, model.predict_proba(X_test)[:, 1]))

# ROC Curve
fpr, tpr, _ = roc_curve(y_test, model.predict_proba(X_test)[:, 1])
plt.plot(fpr, tpr, label="ROC Curve (AUC = {:.2f})".format(roc_auc_score(y_test, model.predict_proba(X_test)[:, 1])))
plt.plot([0, 1], [0, 1], 'k--')
plt.xlabel("False Positive Rate")
plt.ylabel("True Positive Rate")
plt.title("ROC Curve - Logistic Regression")
plt.legend()
plt.grid(True)
plt.show()
```
## 4. Results and Interpretation

The model achieved an overall **accuracy of 75%**, with class-specific performance as follows:

- **Class 0 (Non-Diabetic)**:
  - Precision: 0.81
  - Recall: 0.79
  - F1-score: 0.80

- **Class 1 (Diabetic)**:
  - Precision: 0.64
  - Recall: 0.67
  - F1-score: 0.65

The model performs better at identifying **non-diabetic patients**, while performance on the diabetic class is slightly lower, which is a common challenge due to potential class imbalance or overlapping feature distributions.

### ROC Curve Analysis

The ROC curve yields an **AUC score of 0.81**, indicating strong classification ability. AUC > 0.80 is generally considered good, suggesting the model successfully distinguishes between diabetic and non-diabetic patients. The ROC curve stays well above the diagonal baseline, especially at low false positive rates.

---

## 5. Conclusion

The Logistic Regression model demonstrates strong baseline performance in predicting diabetes status based on medical diagnostic features.

