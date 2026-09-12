# Student Dropout Risk Prediction

## Overview

This project predicts the academic outcome of university students using machine learning.

The project uses the UCI Student Dropout and Academic Success dataset, which contains information about students' demographic background, academic performance, and other factors.

Three classification approaches are evaluated:

- Baseline model
- K-Nearest Neighbors (KNN)
- Support Vector Machine (SVM)

The main goal is to compare these models and identify which one performs best at predicting student outcomes.

## Dataset

The dataset used in this project is the **Predict Students' Dropout and Academic Success** dataset from the UCI Machine Learning Repository.

It contains:

- **4,424 student records**
- **36 input features**
- **1 target variable**
- **3 target classes**

The target classes are:

- **Dropout**
- **Enrolled**
- **Graduate**

The features include information about students' demographic background, admission details, and academic performance during their first and second semesters.

The dataset does not contain missing values or duplicate records.

Dataset source:

https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success

## Project Workflow

The project follows these main steps:

1. Load and inspect the dataset
2. Perform exploratory data analysis (EDA)
3. Check for missing values and duplicate records
4. Split the data into training and testing sets
5. Scale the features using StandardScaler
6. Train a baseline classifier
7. Train a KNN classifier
8. Train an SVM classifier
9. Compare model performance
10. Analyze classification errors
11. Evaluate the best-performing model

## Machine Learning Models

### 1. Baseline

A `DummyClassifier` using the most frequent class was used as the baseline.

This provides a simple reference point for evaluating the machine learning models.

### 2. K-Nearest Neighbors (KNN)

KNN classifies a student based on the classes of its nearest training examples.

The model was trained with:

- `n_neighbors = 5`
- Standardized features

### 3. Support Vector Machine (SVM)

SVM was used as the main classification model.

The model was trained with:

- RBF kernel
- Standardized features

The performance of all three models was compared using Accuracy and Macro F1-score.

## Results

The models were evaluated on the test set containing 885 students.

SVM achieved the best overall performance among the tested models, with an accuracy of **75.82%** and a Macro F1-score of **67.85%**.

KNN also performed better than the baseline, achieving an accuracy of **66.78%**.

The baseline accuracy was **49.94%**, which provides a reference point for evaluating the machine learning models.

## Error Analysis

The SVM model correctly classified 671 out of 885 test students and incorrectly classified 214 students.

The most common prediction errors were:

| Actual Class | Predicted Class | Number |
|--------------|-----------------|-------:|
| Enrolled     | Graduate        | 75     |
| Dropout      | Graduate        | 44     |
| Dropout      | Enrolled        | 34     |
| Enrolled     | Dropout         | 28     |
| Graduate     | Enrolled        | 22     |
| Graduate     | Dropout         | 11     |

The **Enrolled** class was the most difficult class for the model to identify correctly.

This can be explained partly by the academic performance of the three groups. Graduate students generally had stronger academic results, while Dropout students had lower results. Enrolled students were generally between these two groups, making them more difficult to distinguish.

## Project Structure

```text
student-dropout-risk-prediction/
│
├── data/
│   └── data.csv
│
├── notebooks/
│   ├── 01_eda.ipynb
│   └── 02_modeling.ipynb
│
├── figures/
│   ├── target_distribution.png
│   ├── age_distribution.png
│   ├── admission_grade_by_target.png
│   ├── first_semester_grade_by_target.png
│   ├── second_semester_grade_by_target.png
│   ├── approved_courses_by_target.png
│   ├── correlation_matrix.png
│   ├── model_comparison.png
│   ├── svm_confusion_matrix.png
│   └── svm_f1_by_class.png
│
├── results/
│   └── model_comparison.csv
│
├── requirements.txt
├── .gitignore
└── README.md

## Technologies

- Python
- Pandas
- Matplotlib
- Scikit-learn
- Jupyter Notebook
- Git
- GitHub

## Conclusion

This project demonstrates the use of machine learning classification techniques to predict student academic outcomes.

Three approaches were tested: a baseline classifier, KNN, and SVM. Among them, SVM achieved the best performance with an accuracy of **75.82%** and a Macro F1-score of **67.85%**.

The analysis also showed that the Enrolled class is more difficult to predict than the Dropout and Graduate classes.

The results suggest that academic performance features can provide useful information for identifying different student outcomes.

## Future Work

Possible improvements to the project include:

- Testing additional classification algorithms
- Hyperparameter tuning
- Feature selection
- Handling class imbalance
- Testing the model on new student data
- Developing a simple interface for academic advisors

## References

- UCI Machine Learning Repository. Predict Students' Dropout and Academic Success.
  https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success

- Scikit-learn documentation.
  https://scikit-learn.org/