# MSCS 634 — Lab 4: Regression Analysis with Regularization Techniques

## Purpose of the Lab
The purpose of this lab was to explore and compare a variety of regression techniques using the **Diabetes** dataset from scikit-learn.  
The lab focused on implementing:

- Simple Linear Regression  
- Multiple Linear Regression  
- Polynomial Regression  
- Ridge Regression  
- Lasso Regression  

The goal was to understand how different modeling approaches handle predictive complexity, multicollinearity, and overfitting, and to evaluate model performance using **MAE, MSE, RMSE, and R²**.

---

## Key Insights from the Regression Analysis

### 1. Simple vs. Multiple Regression  
- **BMI alone** provides a moderate fit (R² ≈ 0.45), confirming it is a strong individual predictor.  
- **Multiple linear regression** using all 10 features significantly improved performance (R² ≈ 0.52), demonstrating that diabetes progression is influenced by multiple variables.

### 2. Polynomial Regression  
- While polynomial models introduced curvature and reduced bias slightly, they did **not** outperform the multivariate linear model.  
- Higher-degree polynomials (e.g., 5) displayed clear **overfitting**, with minimal gains in R².

### 3. Ridge and Lasso Regularization  
- **Ridge Regression (α = 1)** delivered the best generalization performance (R² ≈ 0.53), stabilizing coefficients in the presence of correlated features.  
- **Lasso (α = 1)** produced a slightly simpler and more interpretable model by shrinking several coefficients to **zero**, showing which features are most important.

### 4. Overall Takeaway  
The dataset’s structure is largely **linear**, and incorporating all features provides meaningful improvement.  
Regularization methods (especially Ridge) help control overfitting and coefficient instability, making them the most effective models for this dataset.

---

## Challenges & Decisions Made

### 1. Handling Multicollinearity  
The correlation matrix showed strong relationships among several serum measurements (e.g., `s1`, `s2`, `s4`, `s5`).  
To address this, both Ridge and Lasso were tested. Ridge performed best, confirming its usefulness in stabilizing correlated predictors.

### 2. Choosing Polynomial Degrees  
Polynomial degrees of **2**, **3**, and **5** were tested.  
Although higher degrees captured more curvature, they risked overfitting without meaningful performance gains.  
A decision was made to limit analysis to degree 3 for balanced comparison.

### 3. Model Evaluation Consistency  
All models were evaluated using a consistent set of metrics (MAE, MSE, RMSE, R²) and the same train-test split to ensure fair comparison.

### 4. Regularization Parameter (α) Selection  
Multiple α values were tested manually, and performance and coefficient behavior were compared.  
Ridge and Lasso both showed improved generalization, with Ridge ultimately providing the best R².

