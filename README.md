# 🧑 Credit Risk Prediction (Python & SQL) - Jul 2025

This project predicts high-risk loan applicants using machine learning and provides insights through SQL reporting and visualizations. The goal is to identify potential loan defaulters and assist financial institutions in decision-making.

---

### Dataset
- The dataset contains financial and loan-related features such as Loan Amount, Funded Amount, Interest Rate, Employment Duration, Home Ownership, and Debit-to-Income ratio.  
- Total Entries: 67463  
- Columns: 28  
- Target Column: `Loan Status` (0 = Non-Default, 1 = Default)  

---

### Data Exploration & Preprocessing
- Removed irrelevant columns (`ID`, `Batch Enrolled`, `Grade`, `Sub Grade`, etc.) and features with single values.  
- Converted categorical variables into numerical form using mapping and label encoding for features like Employment Duration, Verification Status, Application Type, and Initial List Status.  
- Handled missing values (none found).  
- Detected and capped outliers using the **Interquartile Range (IQR)** method.  

---

### Handling Imbalanced Data
- The dataset was imbalanced (majority class: 0, minority class: 1).  
- Applied **oversampling** to balance classes, resulting in a dataset with ~122,000 examples.  

---

### Model Selection & Training
- Split dataset: 70% training, 30% testing.  
- Models trained:
  - Decision Tree Classifier  
  - Random Forest Classifier  
  - Logistic Regression, GaussianNB, KNN (tested)  
  - XGBoost (tested)  

- **Hyperparameter tuning** was applied to Decision Tree and Random Forest.  
- **Random Forest** was selected as the final model due to its superior performance.  

---

### Results
- Random Forest achieved ~99% accuracy on the test set after hyperparameter tuning.  
- Decision Tree accuracy: ~96%  

**Key Metrics (Random Forest):**  
- Accuracy: 0.99  
- F1-Score: 0.99  

---

### SQL Export & Visualization
- Predicted loan statuses were exported to an **SQLite database (`credit_risk.db`)** for reporting purposes.  
- Visualized the distribution of predicted high-risk vs low-risk applicants using bar charts.  

**Example Bar Chart:**
[Bar plot showing predicted high-risk (1) vs low-risk (0) applicants]

X-axis: Prediction (0 = Low Risk, 1 = High Risk)

Y-axis: Number of Applicants (Low Risk ~1500, High Risk ~500)


**Example Table of Predictions:**

| Loan ID | Funded Amount | Interest Rate | Home Ownership | Loan Status | prediction |
|---------|---------------|---------------|----------------|-------------|------------|
| 1001    | 15000         | 0.13          | RENT           | 0           | 0          |
| 1002    | 25000         | 0.15          | MORTGAGE       | 1           | 1          |
| 1003    | 12000         | 0.10          | OWN            | 0           | 0          |
| 1004    | 18000         | 0.12          | RENT           | 1           | 1          |
| 1005    | 22000         | 0.14          | RENT           | 0           | 0          |

---

### Conclusion
This project demonstrates the end-to-end pipeline for credit risk prediction:  
1. Data preprocessing and feature engineering  
2. Handling imbalanced datasets  
3. Model selection and hyperparameter tuning  
4. Exporting predictions to SQL  
5. Visualizing results for actionable insights  

Random Forest was chosen as the final model for its robustness, accuracy, and ability to handle imbalanced data. The project provides a realistic approach to automating risk assessment in financial lending.

--- 