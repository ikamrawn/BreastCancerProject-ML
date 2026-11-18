# Breast Cancer Classification Using Machine Learning

## Project Overview

This project focuses on predicting whether a breast tumor is **Benign (non-cancerous)** or **Malignant (cancerous)** using supervised machine learning algorithms.

The main objective is to compare different classification algorithms and investigate how the number of input features affects their performance.

Two feature configurations are evaluated:
- **10 Features:** Only the mean values of the available features.
- **30 Features:** All available numerical features.

The project also compares model performance using multiple evaluation metrics to identify the most suitable classification algorithm.

## Dataset

The project uses the **Wisconsin Breast Cancer Diagnostic (WDBC)** dataset.

- Total samples: 569
- Total numerical features: 30
- Target variable: Diagnosis
- Classes:
  - `B` → Benign (0)
  - `M` → Malignant (1)

The dataset contains numerical measurements extracted from digitized images of fine needle aspirate (FNA) samples.

Dataset source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic)

## Data Preprocessing

The following preprocessing steps were performed:

1. Removed unnecessary columns, including the ID column and empty columns.
2. Converted diagnosis labels into binary numerical values.
3. Separated input features (X) from the target variable (y).
4. Created two feature sets:
   - 10 mean features.
   - All 30 numerical features.
5. Split the dataset into training and testing sets using a stratified 70/30 split.
6. Applied StandardScaler to standardize features where necessary.

The same train-test split was used for both feature configurations to ensure a fair comparison.

## Machine Learning Algorithms

Seven supervised classification algorithms were implemented:

| Algorithm | Configuration |
|---|---|
| Naive Bayes | GaussianNB |
| K-Nearest Neighbors | KNN (k=5) |
| Decision Tree | Maximum depth = 5 |
| Random Forest | 100 estimators |
| Support Vector Machine | RBF kernel |
| Logistic Regression | Maximum iterations = 2000 |
| Artificial Neural Network | MLP (64, 32) |

Each algorithm was evaluated using both feature configurations, resulting in 14 model experiments.

## Model Evaluation

The following metrics were used to evaluate model performance:

- **Accuracy:** Overall percentage of correctly classified samples.
- **Precision:** Percentage of positive predictions that are actually positive.
- **Recall:** Percentage of actual positive samples correctly identified.
- **F1-Score:** Harmonic mean of Precision and Recall.
- **ROC-AUC:** Measures the model's ability to distinguish between the two classes.

Since detecting malignant tumors is particularly important, Recall for the Malignant class received special attention.

### Cross-Validation

A 5-Fold Stratified Cross-Validation strategy was applied to the training data.

This approach provides a more reliable estimate of model performance by evaluating each model across multiple training and validation splits.

## Results

### 1. Cross-Validation Results (30 Features)

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Naive Bayes | 92.95% | 91.19% | 89.79% | 90.42% | 98.57% |
| KNN | 95.97% | 98.51% | 90.46% | 94.25% | 98.38% |
| Decision Tree | 91.70% | 90.94% | 86.41% | 88.40% | 89.12% |
| Random Forest | 93.96% | 92.59% | 91.82% | 91.91% | 98.34% |
| SVM | 97.23% | 97.87% | 94.55% | 96.15% | 99.29% |
| Logistic Regression | **98.24%** | **100.00%** | **95.26%** | **97.57%** | 99.26% |
| ANN | 92.70% | 94.05% | 85.72% | 89.64% | 98.21% |

Logistic Regression achieved the best overall cross-validation performance, while SVM achieved the highest ROC-AUC.

### 2. Feature Comparison

Using all 30 features improved the performance of several algorithms, particularly Logistic Regression and SVM.

However, the improvement was not consistent across all models. For example, KNN achieved higher accuracy with 30 features but slightly lower Recall. ANN and Decision Tree also showed lower Recall with the larger feature set.

These results suggest that increasing the number of features does not necessarily improve every classification algorithm.

### 3. Final Model: Logistic Regression

Based on the cross-validation results, Logistic Regression using all 30 features was selected as the final model.

Its performance on the independent test set was:

| Metric | Result |
|---|---:|
| Accuracy | 97.08% |
| Malignant Precision | 98.36% |
| Malignant Recall | 93.75% |
| Malignant F1-Score | 96.00% |
| ROC-AUC | 99.75% |

### 4. Confusion Matrix

The final model produced the following confusion matrix on the test set:

| | Predicted Benign | Predicted Malignant |
|---|---:|---:|
| Actual Benign | 106 | 1 |
| Actual Malignant | 4 | 60 |

Out of 171 test samples, 166 were correctly classified.

The model correctly identified 60 out of 64 malignant cases, while 4 malignant cases were incorrectly classified as benign.

### 5. ROC Curve Comparison

Logistic Regression and SVM were also compared using their ROC curves on the test set.

| Model | Test ROC-AUC |
|---|---:|
| Logistic Regression | 99.75% |
| SVM | 99.72% |

Both models demonstrated excellent class separation, with ROC curves located very close to the top-left corner.

Logistic Regression was retained as the final model due to its slightly better overall cross-validation performance.

## Overfitting Analysis

Training and testing accuracy were compared for Logistic Regression and KNN using all 30 features.

The difference between training and testing accuracy provides an initial indication of how well a model generalizes to unseen data.

- When training and testing accuracy are close, the model shows no strong indication of overfitting.
- A considerably higher training accuracy may indicate that the model has learned patterns specific to the training data.
- A small difference does not prove that a model is completely free of overfitting.

Cross-validation results were also considered to provide a more reliable assessment of model generalization.

## Conclusion

The experimental results indicate that Logistic Regression using all 30 features achieved the best overall performance among the seven evaluated classification algorithms.

With a test accuracy of 97.08% and a malignant-class Recall of 93.75%, it demonstrated strong classification performance on the selected dataset.

The comparison also showed that using more features does not always lead to better results, as the impact of additional features depends on the classification algorithm.

Overall, this project demonstrates the application and comparison of several supervised machine learning algorithms for binary classification.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## Disclaimer

This project is an educational machine learning experiment. Its results should not be considered a substitute for professional medical diagnosis or clinical validation.
