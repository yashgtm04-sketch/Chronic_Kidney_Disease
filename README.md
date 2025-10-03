# Chronic Kidney Disease Prediction 🩺

This project uses machine learning to predict the onset of Chronic Kidney Disease (CKD) based on a patient's health metrics. The primary goal is to build and evaluate accurate classification models to distinguish between patients with and without CKD.

## 📜 Table of Contents

- [Project Overview](#-project-overview)
- [Dataset](#-dataset)
- [Methodology](#-methodology)
- [Results](#-results)
- [How to Run](#-how-to-run)
- [Technologies Used](#-technologies-used)

## ✨ Project Overview

This notebook provides a complete walkthrough of a machine learning workflow for a classification problem. It begins with loading a raw dataset, proceeds with extensive data cleaning and preprocessing, trains multiple classification models, and finally evaluates their performance to identify the most effective one for predicting Chronic Kidney Disease.

---

## 💾 Dataset

The project uses the `kidney_disease.csv` dataset. This dataset contains 400 instances with various health-related features.

The target variable is **`classification`**, which indicates whether a patient has Chronic Kidney Disease (`ckd`) or not (`notckd`).

**Key features include:**
* `age`: Patient age (years)
* `bp`: Blood Pressure (mm/hg)
* `sg`: Urine Specific Gravity
* `al`: Albumin in urine
* `hemo`: Hemoglobin level (g/dl)
* `sc`: Serum Creatinine (mg/dl)
* `htn`: Hypertension (yes/no)
* `dm`: Diabetes Mellitus (yes/no)

---

## ⚙️ Methodology

The project follows a systematic approach to build and evaluate the prediction models.

### 1. Data Cleaning
* The irrelevant `id` column was dropped from the dataset.
* All columns were renamed for clarity and ease of use.
* Inconsistent string entries in categorical columns like `dm`, `cad`, and `classification` were corrected (e.g., `ckd\t` was changed to `ckd`).

### 2. Data Preprocessing
* **Encoding:** Categorical features (e.g., `htn`, `dm`, `rbc`) were converted into a numerical format (0s and 1s) using mapping.
* **Missing Value Imputation:** Missing values in numerical columns were filled using the **median** of each column, while missing values in categorical columns were filled with the **mode**.
* **Feature Scaling:** Numerical features were normalized using `MinMaxScaler` to scale them between 0 and 1, ensuring that no single feature dominates the model due to its scale.

### 3. Model Training
* The preprocessed data was split into training (80%) and testing (20%) sets.
* Three different classification models were trained on the training data:
    1.  **Logistic Regression**
    2.  **Random Forest Classifier**
    3.  **Gradient Boosting Classifier**

### 4. Model Evaluation
* The performance of each trained model was evaluated on the unseen test set.
* Standard classification metrics were used for evaluation: **Accuracy Score**, **Confusion Matrix**, and a detailed **Classification Report** (including precision, recall, and F1-score).

---

## 📊 Results

All three models demonstrated outstanding performance on the test data, achieving identical high accuracy scores. This indicates that the data preprocessing was highly effective.

| Model | Accuracy | Precision (Class 0) | Recall (Class 0) | F1-Score (Class 1) |
| :--- | :---: | :---: | :---: | :---: |
| **Logistic Regression** | 98.75% | 0.97 | 1.00 | 0.99 |
| **Random Forest** | 98.75% | 0.97 | 1.00 | 0.99 |
| **Gradient Boosting** | 98.75% | 0.97 | 1.00 | 0.99 |

The confusion matrix for all models was nearly perfect:
$$
\begin{pmatrix}
28 & 0 \\
1 & 51
\end{pmatrix}
$$
This matrix shows **28** correct `notckd` predictions, **51** correct `ckd` predictions, and only **1** error, where a `ckd` patient was incorrectly classified as `notckd`.



