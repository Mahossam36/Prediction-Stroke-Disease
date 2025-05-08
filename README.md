# 🧠 Stroke Prediction Machine Learning Project

This project uses a healthcare dataset to predict the likelihood of a person experiencing a stroke. It involves data cleaning, preprocessing, exploratory data analysis, feature encoding, scaling, and model training with evaluation.

---

## 📂 Dataset Information

- **Filename**: `healthcare-dataset-stroke-data.csv`
- **Total Records**: 5110
- **Features**:
  - `id`: Unique identifier
  - `gender`, `age`, `hypertension`, `heart_disease`
  - `ever_married`, `work_type`, `Residence_type`, `avg_glucose_level`, `bmi`, `smoking_status`
  - `stroke`: Target (0 or 1)

---

## 🔄 Workflow Overview

### 1. Data Exploration
- Displayed basic dataset info using `.head()`, `.info()`, `.describe()`

### 2. Data Cleaning
- **Missing Values**: Filled missing `bmi` with mean
- **Duplicates**: Verified no duplicates
- **Data Types**: Verified and casted if needed

### 3. Feature Encoding
- Label encoded categorical variables:
  - `gender`, `ever_married`, `work_type`, `Residence_type`, `smoking_status`

### 4. Outlier Handling
- Applied IQR method on `avg_glucose_level` and `bmi`:
  - Values below Q1 - 1.5 * IQR set to min
  - Values above Q3 + 1.5 * IQR set to max

### 5. Feature Scaling
- Used `MinMaxScaler` on `age`, `avg_glucose_level`, and `bmi`

### 6. Correlation Analysis
- Visualized with heatmap using seaborn
- Features were grouped by correlation with the target:
  - **High Correlation**: `age`, `avg_glucose_level`, `hypertension`
  - **Low Correlation**: `bmi`, `gender`, etc.
  - **Bad Correlation**: `id` (dropped)

---

## 🤖 Machine Learning Models

| Model                | Notes |
|---------------------|-------|
| **Logistic Regression** | Balanced classes using `class_weight='balanced'`, tuned C |
| **Decision Tree**        | Compared entropy vs gini, tuned `max_depth` |
| **K-Nearest Neighbors**  | Tuned K from 1 to 21 |
| **Support Vector Machine** | Used balanced class weights, tuned C |

### ⚙️ Evaluation Metrics
- Accuracy Score
- Classification Report:
  - Precision, Recall, F1-score
- Confusion Matrix (visualized with seaborn)

---

## 🛠️ Installation & Requirements

Install the dependencies:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn missingno
