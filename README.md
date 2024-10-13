# Polynomial Regression on Orbital Dataset

This project performs polynomial regression on an orbital dataset that contains time and corresponding position data. The objective is to model the non-linear relationship between `time_steps` and the `y` (position) variable using polynomial features and a simple neural network.

## Dataset Overview

The dataset, `orbit - orbit.csv`, consists of the following key columns:
- `time_steps`: Time steps at which the position data is recorded.
- `y`: The corresponding position values at each time step.

The dataset is used to understand and predict the object's position based on the given time steps.

## Project Workflow

### 1. Data Loading and Exploration

The dataset is first loaded using `pandas` for inspection:
- **Data preview**: The first few rows are displayed using `df.head()`.
- **Data types and structure**: Information about the dataset's structure is checked using `df.info()`.
- **Missing values**: Null values are identified using `df.isnull().sum()`.

### 2. Data Visualization

A scatter plot is created to visualize the relationship between `time_steps` and `y`:
- **Scatter plot**: Uses `matplotlib` to plot `time_steps` vs. `y` to check for non-linear relationships.

### 3. Data Splitting

The data is split into training and testing sets using `train_test_split`:
- `x_train`, `x_test`: The time steps are split for training and testing.
- `y_train`, `y_test`: The corresponding position values are split for training and testing.

### 4. Polynomial Feature Transformation

To capture non-linear relationships, the `time_steps` are expanded using polynomial features:
- **Polynomial Degree**: Polynomial features of degree 3 are created using `PolynomialFeatures` from `scikit-learn`.

### 5. Neural Network Model

A simple neural network is built using Keras:
- **Model Architecture**: A sequential model with a single dense layer is used.
- **Input Dimensions**: The input dimension corresponds to the number of polynomial features generated.
- **Compilation**: The model is compiled with the Adam optimizer and mean squared error as the loss function.
- **Training**: The model is trained on the polynomial-transformed data for 100 epochs with a batch size of 32.

### 6. Prediction and Evaluation

After training, predictions are made on the test set:
- **Scatter Plot of Predictions**: The predicted positions are plotted alongside the actual positions for visual comparison.
- **R² Score**: The model’s performance is evaluated using the R² score.
