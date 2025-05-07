# Regression Tree Analysis on Air Quality Dataset

This project applies a **Decision Tree Regressor** to predict **carbon monoxide concentration (`CO(GT)`)** based on sensor measurements from the **Air Quality UCI Dataset**. The goal is to evaluate model performance, interpret its structure, and identify the most important factors contributing to urban air pollution.

---

## 1. Objective

To predict the **CO(GT)** (Carbon Monoxide concentration in mg/m³) using features such as chemical sensor outputs and weather data from urban air quality records. Decision Trees were selected for their interpretability and ability to model non-linear interactions.

---

## 2. Dataset Overview

- **Name**: AirQualityUCI.csv
- **Source**: UCI Machine Learning Repository
- **Samples**: ~9,300 hourly observations
- **Features**: 15 numeric variables including:
  - Chemical gas sensor readings (e.g., `C6H6(GT)`, `NOx(GT)`)
  - Environmental parameters (e.g., `Temperature`, `Relative Humidity`)
- **Target variable**: `CO(GT)` — concentration of carbon monoxide

---

## 3. Preprocessing

- Missing values coded as `-200` were replaced with `NaN`
- Dropped rows where the target value (`CO(GT)`) was missing
- Removed timestamp columns (`Date`, `Time`)
- Mean imputation applied to remaining missing values
- Standardization applied to features before model training

---

## 4. Modeling Approach

- A **DecisionTreeRegressor** was trained to predict `CO(GT)`
- The model depth was controlled to avoid overfitting
- Evaluation was performed using **Mean Squared Error (MSE)** and **R-squared (R²)** score
- Additional visualization included:
  - Prediction vs Actual scatter plot
  - Regression tree structure
  - Feature importance bar chart

---

## 5. Evaluation Results

**Performance Metrics:**
- **Mean Squared Error (MSE)**: `0.25`
- **R-squared Score (R²)**: `0.8779`

These results indicate the model explains **87.8%** of the variance in carbon monoxide levels, with a very low prediction error.

---

## 6. Result Interpretation

### ✅ Actual vs Predicted Plot:
- Predicted values align well with actual values along the identity line.
- The model slightly **underpredicts higher CO levels**, but overall tracks the true trend accurately.

### ✅ Tree Structure:
- The trained decision tree produces a balanced, interpretable structure.
- Rules can be visualized to understand how sensor thresholds lead to specific CO(GT) predictions.

### ✅ Feature Importance:
- **C6H6(GT)** (benzene) is the most dominant predictor, contributing over **60%** of importance.
- Other significant features include **PT08.S2(NMHC)** and **NOx(GT)**.
- Most remaining features (e.g., humidity, temperature) have minimal impact.

---

## 7. Conclusion

The regression tree model proves highly effective at predicting carbon monoxide concentration from urban air sensor data. Key takeaways:

- **Strong performance** (R² ≈ 0.88) shows the model captures real-world pollution patterns well.
- The tree structure is **interpretable**, making it useful for environmental decision-making.
- A small number of features, especially **C6H6(GT)**, dominate the prediction process, highlighting potential pollutant relationships.

---
