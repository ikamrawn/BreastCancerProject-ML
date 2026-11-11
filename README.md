# Breast Cancer Classification

## Introduction

This project uses machine learning algorithms to classify breast tumors as either **Benign** or **Malignant**.

The main goal is to train and compare different classification models and investigate how using different numbers of features affects their performance.

## Dataset

The project uses the **Breast Cancer Wisconsin Diagnostic Dataset**.

- Number of samples: 569
- Number of features: 30
- Target variable: Diagnosis
- Benign (B): 0
- Malignant (M): 1

Dataset source: [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic)

## Data Preprocessing

The following steps were performed:

1. Loading the dataset using Pandas.
2. Removing unnecessary columns such as ID and empty columns.
3. Converting diagnosis labels into numerical values.
4. Separating input features and target labels.
5. Splitting the data into training and testing sets.
6. Applying feature scaling using StandardScaler.

## Feature Selection

Two different feature sets were used:

- **10 Features:** Only the mean values of the original features.
- **30 Features:** All available numerical features.

The purpose was to compare the performance of each algorithm using these two feature configurations.

## Machine Learning Models

Seven classification algorithms were implemented:

1. Naive Bayes
2. K-Nearest Neighbors (KNN)
3. Decision Tree
4. Random Forest
5. Support Vector Machine (SVM)
6. Logistic Regression
7. Artificial Neural Network (ANN)

## Evaluation Metrics

The models were evaluated using three main metrics:

- **Accuracy:** Measures the overall percentage of correct predictions.
- **Recall:** Measures how many actual malignant cases were correctly identified.
- **F1-Score:** Combines Precision and Recall into a single metric.

These metrics were used to compare the performance of the models on both feature sets.

## Results and Comparison

The experimental results showed that using all 30 features improved the performance of some algorithms, while others performed similarly or better with only 10 features.

Logistic Regression and SVM showed particularly good performance when using all 30 features.

Based on the experimental results, Logistic Regression with 30 features achieved the best overall performance.

### Final Model Performance

The selected Logistic Regression model achieved the following results on the test dataset:

| Metric | Score |
|---|---:|
| Accuracy | 97.08% |
| Precision | 98.36% |
| Recall | 93.75% |
| F1-Score | 96.00% |

## Confusion Matrix

The confusion matrix of the final model showed:

| | Predicted Benign | Predicted Malignant |
|---|---:|---:|
| Actual Benign | 106 | 1 |
| Actual Malignant | 4 | 60 |

Out of 171 test samples, 166 were correctly classified.

## Overfitting Analysis

Training and testing accuracy were compared for Logistic Regression and KNN.

The small difference between training and testing accuracy suggests good generalization, with no strong indication of overfitting.

However, this comparison alone cannot prove that a model is completely free of overfitting.

## Conclusion

This project demonstrates how different machine learning algorithms can be applied to breast cancer classification.

The comparison between 10 and 30 features showed that the number of features can affect model performance differently depending on the algorithm.

Among the seven evaluated models, Logistic Regression using all 30 features achieved the best overall results.

## Tools and Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

## Disclaimer

This project is developed for educational purposes only. Its predictions are not intended for real-world medical diagnosis.
