# Supervised Learning: Linear Regression  
**Dataset**: California Housing Dataset  

## 1. Research Objective

This project applies **Linear Regression** to predict **California housing prices** using socio-economic and geographical features from the California Housing dataset. The target variable is the **median house value** of census blocks in California.  

The purpose is to evaluate how well a linear model can capture relationships between input features and housing prices. Model performance will be evaluated using metrics such as **Mean Squared Error (MSE)** and **R-squared Score**.

---

## 2. Dataset Description

- **Source**: Scikit-learn built-in `fetch_california_housing()`  
- **Observations**: ~20,000  
- **Features**:
  - `MedInc`: Median income in block group
  - `HouseAge`: Median house age
  - `AveRooms`: Average number of rooms per household
  - `AveBedrms`: Average number of bedrooms per household
  - `Population`: Block group population
  - `AveOccup`: Average household occupancy
  - `Latitude` & `Longitude`: Location

- **Target**:  
  - `MedHouseVal`: Median house value (in $100,000s)

The dataset is continuous, contains no missing values, and is suitable for regression analysis.

---

## 3. Linear Regression Implementation

The model is implemented using the `LinearRegression` class from `scikit-learn`. The workflow includes data preprocessing, model training, prediction, and performance evaluation.

```python
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score
import matplotlib.pyplot as plt

# Load and prepare data
data = fetch_california_housing(as_frame=True)
df = data.frame

X = df.drop(columns='MedHouseVal')
y = df['MedHouseVal']

# Train-test split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train model
model = LinearRegression()
model.fit(X_train, y_train)

# Predict
y_pred = model.predict(X_test)

# Evaluate
mse = mean_squared_error(y_test, y_pred)
r2 = r2_score(y_test, y_pred)

print("Mean Squared Error:", mse)
print("R-squared Score:", r2)

# Plot
plt.scatter(y_test, y_pred, alpha=0.5)
plt.plot([y.min(), y.max()], [y.min(), y.max()], 'r--')
plt.xlabel("Actual Median House Value")
plt.ylabel("Predicted Value")
plt.title("Actual vs Predicted Values - Linear Regression")
plt.grid(True)
plt.show()

## 4. Results and Interpretation

The Linear Regression model was evaluated on a test set using two standard metrics:

- **Mean Squared Error (MSE)**: 0.556  
  Indicates the average squared difference between predicted and actual housing values.

- **R-squared Score (R²)**: 0.576  
  The model explains approximately **57.6%** of the variance in the target variable (`MedHouseVal`), suggesting a moderate fit.

### Visualization

The scatter plot of actual vs predicted values shows a general upward trend, indicating that the model captures the overall pattern in the data. However, several key observations arise:

- **High-value homes** (actual value near 5) tend to be **underpredicted**, with the model rarely producing outputs above 5.
- **Mid-range values** exhibit more spread, indicating variance that the linear model does not fully explain.
- The **dashed red line** on the plot represents the ideal 1:1 prediction. The fact that many points deviate from this line—especially on the right—reflects limitations in the linear approximation.

---

## 5. Conclusion

This project demonstrates that **Linear Regression** can serve as a useful baseline for predicting housing prices using real-world data.


