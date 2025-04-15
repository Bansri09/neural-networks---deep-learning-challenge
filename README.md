
---

# **Alphabet Soup Charity Neural Network Analysis**

---

## Overview of the Analysis:

The purpose of this analysis is to assess the performance of a deep learning model built to solve a classification problem using the **Alphabet Soup dataset**. The goal is to evaluate how well the model predicts whether funded charity organizations will be successful, identify areas for improvement, and provide recommendations for optimizing model performance.

This analysis covers:

- Data preprocessing steps
- Model architecture design
- Training outcomes
- Optimization strategies and their effects

---

##  Results:

---

###  **Data Preprocessing**

**• Target Variable:**

- The target variable is: `IS_SUCCESSFUL`  
  This is a binary classification problem where:
  - `1` = Application was successful
  - `0` = Application was not successful

**• Feature Variables:**

All remaining variables after cleaning and encoding were used as features, including:

- `APPLICATION_TYPE`, `AFFILIATION`, `CLASSIFICATION`, `USE_CASE`, `ORGANIZATION`, `INCOME_AMT`, `SPECIAL_CONSIDERATIONS`, and `ASK_AMT`.

Categorical features were converted to numerical using **one-hot encoding** (`pd.get_dummies()`), and rare categories were grouped into `"Other"` to reduce noise.

**• Variables to Remove:**

- `EIN` and `NAME` were removed as they are identifiers and provide no predictive value.

---

###  **Compiling, Training, and Evaluating the Model**

**• Neurons, Layers, and Activation Functions:**

- **Original Model Architecture:**
  - 1st Hidden Layer: 80 neurons, `ReLU`
  - 2nd Hidden Layer: 30 neurons, `ReLU`
  - Output Layer: 1 neuron, `Sigmoid`
  
- **Optimized Model Architecture:**
  - 1st Hidden Layer: 256 neurons, `ReLU`
  - 2nd Hidden Layer: 128 neurons, `ReLU`
  - 3rd Hidden Layer: 64 neurons, `ReLU`
  - Output Layer: 1 neuron, `Sigmoid`

The output layer uses **sigmoid activation** for binary classification.

---

###  **Achieving Target Model Performance**

**Original model results:**

- **Loss:** 0.5729  
- **Accuracy:** **72.57%**

**Optimized model results (after 150 epochs):**

- **Loss:** Approx. 0.56  
- **Accuracy:** **~74.2%**

The optimized model showed a slight improvement in accuracy (~1.6%), but still fell just short of the **75% performance threshold**.

---

###  **Steps Taken to Improve Performance**

1. **Increased model complexity:**
   - Added a 3rd hidden layer
   - Increased neurons in each layer

2. **Improved data representation:**
   - Combined rare categorical values into `"Other"` to simplify noisy variables
   - Scaled numerical features using `StandardScaler`

3. **Training enhancements:**
   - Increased training duration to **150 epochs**
   - Used **validation split** for better generalization

> Note: While your code did not include `Dropout` or `LeakyReLU`, those are excellent next-step optimization techniques that could be tested further.

---

## Summary:

**Overall Results:**

- The deep learning model performed well, improving from an initial accuracy of **72.57%** to **74.2%** after optimization.
- Though it didn't cross the 75% threshold, the model was clearly enhanced through structural and preprocessing adjustments.

---

### Recommendation for a Different Model:

While the neural network showed promising results, alternative models may better handle structured/tabular data:

**Recommended Models:**

- **Random Forest Classifier:**
  - Handles categorical variables and non-linear relationships effectively
  - Provides feature importance for explainability
  - Lower risk of overfitting

- **XGBoost:**
  - Great for boosting performance in classification problems
  - Often outperforms neural networks on structured data

- **Ensemble Methods (e.g., Stacking or Voting Classifiers):**
  - Combine strengths of multiple models
  - Improve generalization and reduce overfitting


