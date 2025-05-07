# Neural Network Classification on Wine Quality (White)

This project uses a Multi-Layer Perceptron (MLP) to classify white wine samples as either **good** or **not good** based on physicochemical properties. The dataset is sourced from the UCI Machine Learning Repository and focuses on binary classification using a threshold on wine quality scores.

---

## 1. Dataset Overview

- **Dataset**: `winequality-white.csv`
- **Source**: UCI Machine Learning Repository
- **Samples**: 4,898 white wine instances
- **Features**: 11 numeric attributes related to wine chemistry (e.g., acidity, sugar, pH)
- **Label**: `quality` (integer score from 0 to 10)

For this project, we define a **binary classification** target:
- `quality >= 6` → **1 (Good wine)**
- `quality < 6` → **0 (Not good wine)**

---

## 2. Preprocessing

- Converted `quality` column into a binary label called `quality_binary`
- Split features and labels:  
  `X = wine properties`, `y = quality_binary`
- Applied **standardization** using `StandardScaler` to ensure stable training
- Divided data into training and testing sets with an 80/20 split

---

## 3. Model Architecture

The model is a fully connected **feedforward neural network (MLP)** with the following architecture:

- Input layer: 11 features
- Hidden layer 1: 32 neurons, ReLU activation
- Hidden layer 2: 16 neurons, ReLU activation
- Output layer: 1 neuron, Sigmoid activation (binary classification)

---

## 4. Compilation

The model is compiled using:

- **Optimizer**: Adam (learning rate = 0.001)
- **Loss function**: Binary crossentropy
- **Metrics**: Accuracy and AUC (Area Under Curve)

---

## 5. Training

- Epochs: 30
- Batch size: 32
- Validation split: 20% of training data used for validation
- Tracked metrics: Accuracy and Validation Accuracy

---

## 6. Evaluation on Test Data

```text
Test Loss: 0.4572
Test Accuracy: 0.7765
Test AUC: 0.8417
```
---

## 7. Training vs Validation Accuracy

During training, both training and validation accuracy were tracked across 30 epochs.

### Accuracy Plot:
![Training vs Validation Accuracy](training_vs_validation_accuracy.png)

### Analysis:
- The **training accuracy** increased steadily and reached approximately **82%** by the final epoch.
- **Validation accuracy** peaked around **77%** and then plateaued, indicating that the model started to slightly overfit after about 20 epochs.
- The gap between training and validation accuracy (~5%) suggests **mild overfitting**, though the model still generalizes reasonably well.

### Recommendations:
- Use **early stopping** to halt training once validation accuracy stops improving (e.g., around epoch 20–22).
- Consider adding **Dropout layers** to reduce overfitting further.
- You could experiment with:
  - Additional hidden layers
  - Different batch sizes
  - Regularization (L1 or L2) to improve generalization


