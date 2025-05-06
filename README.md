# 🧠 PROFESSION AI SCHOOL EXERCISE  
## Malignant Breast Tumor Detection

This project aims to build a binary classification model capable of detecting **malignant breast tumors** from diagnostic features extracted from cell nuclei. The model must meet the following evaluation criteria:

- ✅ **Accuracy ≥ 0.98** on the test set  
- ✅ **AUC ≥ 0.98** on the test set  
- ✅ **Recall = 1.0** (zero false negatives)

---

## 📂 Dataset

The dataset is provided by [ProfessionAI](https://github.com/ProfAI/machine-learning-fondamenti) and contains 569 samples with 30 numeric features, derived from digitized images of fine needle aspirate (FNA) of breast masses.

- Each row represents a tumor sample
- The `diagnosis` column contains:
  - `M` = Malignant
  - `B` = Benign

---

## 🔧 Steps Performed

### 1. **Data Cleaning**
- Removed non-informative column `ID number`
- Converted the `diagnosis` column into binary values:
  - `1` = Malignant
  - `0` = Benign

### 2. **Data Exploration**
- Verified class distribution:
  - ~37% malignant, ~63% benign
- Used `value_counts()` and percentage checks

### 3. **Train/Test Split**
- Divided data into 70% training and 30% test set using `train_test_split()`

### 4. **Feature Scaling**
- Applied **StandardScaler** to normalize all features to zero mean and unit variance — important for logistic regression convergence

### 5. **Model Selection**
- Trained a **Logistic Regression** model with `class_weight="balanced"` to counter class imbalance
- Logistic regression was chosen for its interpretability and efficiency on small-to-medium datasets

### 6. **Performance Evaluation**
- Evaluated model using:
  - `classification_report()`
  - Custom **confusion matrix plot** with precision and recall annotation
- Metrics evaluated at **custom threshold = 0.25** to maximize **recall**

### 7. **ROC and AUC**
- Computed **AUC = 0.9988** using `roc_auc_score()`
- Plotted **ROC curve** using `RocCurveDisplay.from_estimator()`

### 8. **Threshold Tuning**
- Predictions adjusted using a threshold of **0.25** instead of the default 0.5
  - Goal: ensure **no false negatives** (recall = 1)
  - Slight trade-off in precision accepted

### 9. **Deployment on Unseen Data**
- Loaded an external test set (`breast_cancer_pred.csv`)
- Applied the same scaler and model
- Used threshold = **0.30** for real-world inference
- Saved predictions and probabilities to an Excel file:  
  `breast_cancer_prediction.xlsx`

---

## ✅ Results

| Metric        | Value (Test Set) |
|---------------|------------------|
| Accuracy      | ≥ 0.98 ✅         |
| Recall        | 1.00 ✅           |
| AUC           | 0.9988 ✅         |

---

## 📦 Output File

- `breast_cancer_prediction.xlsx`  
  Contains:
  - `ID number`
  - `prediction` (0 = Benign, 1 = Malignant)
  - `probability` (confidence score)

---

## 📌 Requirements

This project uses:
- Python 3.x
- pandas, numpy
- matplotlib, seaborn
- scikit-learn

To install all requirements:

```bash
pip install -r requirements.txt
