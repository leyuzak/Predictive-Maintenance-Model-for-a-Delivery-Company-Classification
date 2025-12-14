# 🛠️ Predictive Maintenance Classification

## 📌 Project Overview
This project aims to build a **predictive maintenance classification model** for a delivery company.  
The objective is to predict whether a device or vehicle will experience a **failure (failure = 1)** based on historical sensor data.

The dataset is **highly imbalanced**, which reflects real-world predictive maintenance scenarios where failure events are rare.

---

## 🎯 Objectives
- Perform exploratory data analysis (EDA)
- Handle severe class imbalance using **SMOTE**
- Build a baseline classification model
- Train an advanced ensemble model
- Evaluate performance using metrics suitable for imbalanced datasets

---

## 📂 Dataset Description
- **Target variable:** `failure`
  - `0` → No failure
  - `1` → Failure
- **Features:** Multiple numerical sensor attributes
- **Removed columns:**
  - `date` (temporal identifier)
  - `device` (categorical identifier)

Failure events represent a very small portion of the dataset, making accuracy alone an unreliable metric.

---

## 🔍 Exploratory Data Analysis (EDA)
The following steps were performed:
- Dataset structure and summary statistics
- Class distribution analysis
- Visualization of imbalance between classes
- Initial feature inspection

EDA confirmed a **severe imbalance** in the target variable.

---

## ⚙️ Methodology

### Train-Test Split
- Data split into **80% training** and **20% testing**
- Stratified split used to preserve class distribution

### Baseline Model
- **Logistic Regression**
- `class_weight="balanced"` applied to reduce bias toward the majority class

### Handling Imbalanced Data
- **SMOTE (Synthetic Minority Oversampling Technique)** applied **only to the training set**
- Synthetic samples generated based on nearest neighbors of minority class instances
- Prevents data leakage by keeping the test set untouched

### Final Model
- **Random Forest Classifier**
- Trained on SMOTE-balanced training data
- Evaluated on the original imbalanced test data

---

## 📊 Evaluation Metrics
The following metrics were used:
- Recall
- Precision
- F1-score
- Confusion Matrix
- ROC-AUC Score

These metrics provide a more meaningful evaluation than accuracy for imbalanced classification problems.

---

## 📈 Results Summary
- Logistic Regression achieved higher recall but suffered from very low precision
- Random Forest achieved **ROC-AUC ≈ 0.82**, indicating good class separability
- Default decision threshold led to lower recall for failure cases
- Results suggest that threshold tuning could further improve failure detection

---

## 🧠 Key Insights
- SMOTE effectively balances minority class representation in the training data
- High ROC-AUC indicates the model can distinguish between failure and non-failure cases
- In predictive maintenance, **missing a failure is often more costly than false alarms**

---

## 🚀 Technologies Used
- Python
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn
- Imbalanced-learn (SMOTE)
- Jupyter Notebook

---

## 📌 Conclusion
This project demonstrates a complete machine learning workflow for **imbalanced classification problems**.  
By combining SMOTE with ensemble learning and appropriate evaluation metrics, the model provides a realistic approach to predictive maintenance tasks.
