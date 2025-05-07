# K-Nearest Neighbors Regression on Diabetes Dataset

This project applies a K-Nearest Neighbors (KNN) regression model to predict disease progression one year after baseline using the diabetes dataset provided by Scikit-learn. The study focuses on evaluating the model's effectiveness and understanding the impact of the number of neighbors (`k`) on prediction performance.

---

## 1. Objective

The goal is to predict a patient's diabetes progression based on 10 standardized medical features, including age, BMI, blood pressure, and various blood serum measurements. The KNN algorithm is selected for its simplicity and ability to model non-linear relationships.

---

## 2. Dataset Overview

- **Source**: Scikit-learn's `load_diabetes()` dataset
- **Samples**: 442
- **Features**: 10 numeric, standardized
- **Target**: A continuous value representing disease progression after one year

---

## 3. Preprocessing

- Features and target were extracted and standardized using `StandardScaler`.
- The dataset was split into training and testing sets (80/20).
- Scaling was critical for ensuring that KNN's distance metric works properly across all features.

---

## 4. Model Overview

- The model used a **K-Nearest Neighbors Regressor**.
- Initial `k` was set to 5, and predictions were made on the test set.
- Performance was evaluated using **Mean Squared Error (MSE)** and **R-squared (R²)** score.

---

## 5. Evaluation Results

- **Mean Squared Error**: 3047.45  
- **R-squared Score**: 0.4248

These results indicate the model explains roughly **42.5%** of the variance in disease progression. This reflects a fair fit for a basic distance-based model on real-world medical data.

---

## 6. Visualization Insights

### Actual vs. Predicted Scatter Plot

- A generally upward trend was observed, showing the model is directionally correct.
- The model tends to **underpredict high disease progression values**, reflecting the averaging nature of KNN.
- Variance increases for higher target values, showing **reduced confidence** in extreme cases.

### R² Score vs. Number of Neighbors (k)

- The best R² score (~0.45) was achieved at **k = 6**.
- **Low values of k (e.g., k = 1)** overfit and underperform.
- Performance plateaus for **k between 7 and 20**, indicating robustness to neighbor count in this range.

---

## 7. Conclusion

KNN regression serves as a useful baseline model for predicting diabetes progression. While performance is modest, it successfully demonstrates the relationship between medical features and disease outcomes using a non-parametric approach.

### Key Takeaways:
- KNN explains ~42.5% of the variance (R² score).
- It performs reasonably well without heavy tuning.
- The model smooths extreme predictions, especially in high disease progression cases.

---


