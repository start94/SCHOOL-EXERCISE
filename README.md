# 🧠 Malignant Breast Tumor Detection

This repository contains a machine learning project developed as part of the "Profession AI School" exercise. The objective is to build a classification model capable of identifying **malignant breast tumors** with **high accuracy, high AUC, and perfect recall on the test set.

 🎯 Objective

The model must meet the following performance criteria on the test dataset:
- Accuracy ≥ 0.98  
- AUC ≥ 0.98  
- Recall = 1.0 (i.e., no false negatives)

 📂 Dataset

The dataset used is the **Wisconsin Breast Cancer Dataset**, provided by ProfessionAI:

- 📥 Source: [breast_cancer.csv](https://raw.githubusercontent.com/ProfAI/machine-learning-fondamenti/main/datasets/breast_cancer.csv)
- Each instance represents features extracted from a breast mass, and the target is whether it is **malignant (M)** or **benign (B)**.

⚙️ Workflow and Techniques

1. **Data Cleaning & Preprocessing**
- **Dropped the `ID number`** column as it carries no predictive power.
- Converted categorical labels (`M`, `B`) to binary integers (`1`, `0`) using mapping for compatibility with ML algorithms.
- Features and labels were separated into `X` and `y`.

 2. **Data Splitting**
- The dataset was split into **training** and **test** sets with a 70/30 ratio using `train_test_split`.

 3. **Feature Scaling**
- Applied **StandardScaler** to normalize feature values. This is essential for algorithms like Logistic Regression to converge properly and improve performance.

4. **Model Training**
- Chose **Logistic Regression** with `class_weight='balanced'` to handle potential class imbalance.
  - 📌 Reason: Logistic Regression is simple, interpretable, and performs well on linearly separable data. Balanced weighting ensures equal importance to both classes.

 5. **Threshold Tuning**
- Adjusted the **classification threshold** (e.g., to 0.25) to **maximize recall**, ensuring **no malignant cases are missed**.
  - 📌 Why? In medical applications, especially cancer detection, false negatives (missing a malignant case) are unacceptable.

 6. **Evaluation Metrics**
- Evaluated the model using:
  - **Accuracy**
  - **AUC (Area Under ROC Curve)**
  - **Recall**, **Precision**
  - **Confusion Matrix** (with custom heatmap function)

7. **Prediction on New Data**
- Loaded an external dataset (`breast_cancer_pred.csv`) and generated predictions with probabilities.
- Saved results as an Excel file: `breast_cancer_prediction.xlsx`.

## 📊 Results

On the test dataset:
- ✅ **Accuracy** ≥ 0.98  
- ✅ **AUC** ≥ 0.98  
- ✅ **Recall** = 1.0  
- The model successfully avoids false negatives while maintaining strong performance on all metrics.

## 📁 Output

- `breast_cancer_prediction.xlsx` – Excel file containing:
  - Patient ID
  - Prediction (0 = Benign, 1 = Malignant)
  - Confidence Probability

## 💡 Conclusion

This project demonstrates how a carefully tuned and evaluated **Logistic Regression** model, enhanced by threshold adjustment and data scaling, can effectively detect malignant tumors with high confidence. The approach prioritizes **recall** to align with the critical nature of medical diagnostics.
