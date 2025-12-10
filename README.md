# ⚾ KNN Salary Prediction Using the Baseball Dataset

This project explores how well **k-Nearest Neighbors (KNN) Regression** can predict Major League Baseball (MLB) player salaries based on seasonal and career performance statistics.
The notebook includes data preprocessing, model training, hyperparameter tuning, visualization, and performance evaluation using RMSE.

---

## 📌 **Project Objectives**

* Build a KNN regression model to predict `Salary`
* Clean and preprocess the data (missing values, encoding, scaling)
* Experiment with multiple values of *k*
* Perform **manual hyperparameter tuning** (RMSE-based search)
* Perform **automated hyperparameter tuning** using **GridSearchCV**
* Evaluate model performance using:

  * **RMSE (Root Mean Squared Error)**
  * **Cross-Validation RMSE**
* Visualize the effect of *k* on prediction error

---

## 📂 **Dataset Description**

The dataset contains both seasonal and career-level player statistics:

### **Seasonal Performance Metrics**

* `AtBat`, `Hits`, `HmRun`, `Runs`, `RBI`, `Walks`

### **Career Performance Metrics**

* `CAtBat`, `CHits`, `CHmRun`, `CRuns`, `CRBI`, `CWalks`

### **Fielding Statistics**

* `PutOuts`, `Assists`, `Errors`

### **Categorical Variables**

* `League`
* `Division`
* `NewLeague`

### 🎯 **Target Variable**

* `Salary`

---

## 🛠 **Technologies Used**

* Python
* Pandas, NumPy
* Scikit-learn
* Matplotlib
* Jupyter Notebook

---

## 🔧 **Preprocessing Pipeline**

1. **Drop missing values**
2. **Split features and target variable**
3. **One-Hot Encode** categorical variables
4. **Scale numerical features** using `StandardScaler`
5. **Train-test split** (hold-out evaluation)

Preprocessing ensures that KNN — a distance-based model — works effectively.

---

# 🔍 **Manual Hyperparameter Tuning (RMSE-based Search)**

To understand how the number of neighbors (*k*) affects model accuracy, KNN was trained with **k = 1 to 29**.
For each value, the model predicted on the **test set**, and **RMSE** was calculated.
<img width="809" height="417" alt="Ekran Resmi 2025-12-10 23 47 39" src="https://github.com/user-attachments/assets/138202bd-44ee-40c8-a3c1-b82bc2c3ca26" />


### **Insights**

* Very small k (1–3) → **overfitting**, extremely high RMSE
* Best performance occurs around **k = 6–10**
* Larger k values (15–30) → **underfitting**, RMSE increases slightly
* This U-shape pattern is typical for KNN

---

# 🔧 **Automated Hyperparameter Optimization (Grid Search)**

A more robust hyperparameter selection was done using **10-fold Cross-Validation** and **RMSE scoring**:

### **Grid Search Setup**

* Parameter grid: `n_neighbors = 1–30`
* Scoring metric: `neg_mean_squared_error`
* Cross-validation: 10 folds

### **Grid Search Results**

```
Best k (CV, RMSE): 11
Best CV RMSE: 312.71
Test RMSE with tuned model: 360.51
```

### Interpretation

* Cross-validation selects *k = 11* as the best value
* However, the test RMSE (~360.51) is slightly higher than the CV score
* This difference is normal due to:

  * Different data distribution in the test set
  * Variance between CV folds and test partition
  * KNN’s sensitivity to local neighborhood structure

---

# 📊 **Performance Comparison**

| Model Version              | Method                 | Test RMSE |
| -------------------------- | ---------------------- | --------- |
| Baseline KNN               | No tuning              | ~361.49   |
| Manual Tuning              | Best region (k = 6–10) | ~356–360  |
| Grid Search (CV Optimized) | Best k = 11            | 360.51    |

### Key Takeaways

* Manual tuning found excellent performance around k = 6–10
* Grid Search chose k = 11 because it performed consistently well across CV folds
* Both approaches yield similar error levels → model is stable

---

# 🧠 **Conclusion**

This project demonstrates:

* The importance of **scaling and preprocessing** for KNN
* How **manual** and **automated** tuning methods complement each other
* How RMSE behaves across different *k* values
* The value of **cross-validation** in selecting stable hyperparameters
* That KNN can estimate MLB player salaries reasonably well, but performance is sensitive to hyperparameter selection

The notebook provides a complete, reproducible workflow for KNN regression and model tuning.

---
