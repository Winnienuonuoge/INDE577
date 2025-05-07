# Perceptron Model Implementation

## Overview

This project involves the implementation of a single-layer Perceptron, a foundational type of neural network, to classify banknotes as either genuine or forged based on statistical features extracted from wavelet-transformed images. The Perceptron is one of the simplest yet historically significant binary classifiers, providing the conceptual basis for modern neural networks.

## Theoretical Foundation

The Perceptron is a type of linear classifier that makes decisions by computing a weighted sum of the input features and passing the result through a sign (step) function. Introduced by Frank Rosenblatt in 1957, it was one of the earliest models of supervised learning for binary classification.

## Applications

Though simple, the Perceptron forms the basis of more complex learning systems and has applications in:

- Binary classification tasks in finance and security,
- Feature selection and linearly separable signal analysis,
- Educational tools for demonstrating supervised learning concepts.

## Dataset Description

The dataset used is the **Banknote Authentication Dataset** from the UCI Machine Learning Repository. It consists of:

- 1372 instances,
- 4 numerical features:
  - `variance` of wavelet-transformed image,
  - `skewness`,
  - `curtosis`,
  - `entropy`,
- A binary target variable:
  - `0` for genuine banknotes,
  - `1` for forged banknotes.

This dataset is nearly linearly separable and ideal for demonstrating the behavior of the Perceptron model.

## Implementation Details

The notebook `Perceptron.ipynb` includes the following steps:

- **Data Preprocessing**:
  - Standardization using `StandardScaler`.
  - Label encoding: class labels are converted from \{0, 1\} to \{-1, +1\}.
- **Model Training**:
  - Manual implementation of the Perceptron Learning Algorithm.
- **Evaluation**:
  - Accuracy score computed on the full dataset.
  - 2D PCA visualization to examine separability.

## Results

The Perceptron classifier achieved over 98% accuracy on the training dataset. A 2D PCA projection showed clear visual separation between genuine and forged notes, reinforcing the suitability of linear classification for this task.

- **Accuracy**: >98%
- **Convergence**: Reached within a small number of epochs
- **Visualization**: PCA plot illustrates effective class separation

## Conclusion

This implementation demonstrates that even simple models like the Perceptron can perform well on linearly separable datasets. While it lacks the flexibility of more advanced models like logistic regression or neural networks, it remains a valuable tool for learning and experimentation. The clear performance on the Banknote Authentication dataset validates its utility in educational and low-complexity classification tasks.

