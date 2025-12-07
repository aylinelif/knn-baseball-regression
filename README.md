# ⚾ KNN Salary Prediction with Baseball Dataset

This project applies the **k-Nearest Neighbors (KNN)** algorithm to predict MLB players' salaries based on their performance statistics.  
The dataset includes both seasonal and career-level metrics such as hits, home runs, runs, walks, and fielding statistics.

The goal is to explore how well distance-based machine learning models can estimate player salary.

---

## 📌 Project Objectives
- Apply **KNN Regression** to predict `Salary`
- Perform **data cleaning** and handle missing values
- Scale numerical features for KNN
- Convert categorical features using **One-Hot Encoding**
- Evaluate the model using R² Score and RMSE
- Experiment with different **k values** to determine the optimal one

---

## 📂 Dataset Description
The dataset includes the following features:

- `AtBat`, `Hits`, `HmRun`, `Runs`, `RBI`, `Walks`
- `CAtBat`, `CHits`, `CHmRun`, `CRuns`, `CRBI`, `CWalks`
- `PutOuts`, `Assists`, `Errors`
- `League`, `Division`, `NewLeague` (categorical)
- `Salary` (target variable)

---

## 🛠 Technologies Used
- Python
- Pandas / NumPy
- Scikit-learn
- Matplotlib / Seaborn (optional for visualization)
- Jupyter Notebook

---

## 🔧 Preprocessing Steps
1. Remove missing values  
2. Separate features (X) and target (y)  
3. One-Hot Encode categorical variables  
4. Scale numerical features using `StandardScaler`  
5. Train-test split 
