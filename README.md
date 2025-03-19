# COMP1916: Credit Card Fraud Detection with Machine Learning

The dataset can be accessed through this link:https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud/data

## Overview
This repository contains an in-depth analysis and machine learning model selection for detecting fraudulent transactions in credit card data. The project is based on a dataset containing **284,807 transactions**, with only **492 fraudulent cases**, highlighting a severe **class imbalance problem (0.172%)**.

This project follows a structured pipeline from **data preprocessing** to **model evaluation**, implementing multiple machine learning techniques to enhance fraud detection accuracy.

## Table of Contents
- [Introduction](#introduction)
- [Data Preprocessing](#data-preprocessing)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Feature Engineering](#feature-engineering)
- [Machine Learning Models](#machine-learning-models)
- [Results & Model Performance](#results--model-performance)
- [Limitations & Future Work](#limitations--future-work)
- [How to Use](#how-to-use)
- [Dependencies](#dependencies)

## Introduction
Fraud detection in credit card transactions is critical for financial security. This project aims to detect fraudulent transactions using **anonymized PCA-transformed features** and machine learning models. The dataset contains transaction details such as **Time, Amount, and 28 anonymized PCA components**, along with a binary **Class** label (1 = Fraud, 0 = Legitimate).

## Data Preprocessing
The dataset is preprocessed as follows:
- No missing values were found.
- Features, except for `Time` and `Amount`, were transformed via **Principal Component Analysis (PCA)**.
- The `Amount` feature showed high skewness, requiring scaling.
- The `Class` variable was imbalanced (0.172% fraud cases), requiring **resampling techniques**.

## Exploratory Data Analysis (EDA)
- **Distribution of transactions**: Fraud cases are rare, requiring advanced detection methods.
- **Correlation analysis**: PCA-transformed features have minimal correlations.
- **Time-based fraud patterns**: Fraud cases analyzed over transaction time.
- **Transaction Amount analysis**: Fraud cases across different amounts.

## Feature Engineering
- **Feature Scaling**: Standardized `Amount` using `StandardScaler`.
- **Outlier Detection**: Implemented **Isolation Forest** and **Local Outlier Factor** for anomaly detection.
- **Dimensionality Reduction**: PCA ensures confidentiality while preserving data patterns.

## Machine Learning Models
The following machine learning models were implemented and compared:
1. **Isolation Forest** (Anomaly detection)
2. **Local Outlier Factor (LOF)** (Density-based fraud detection)
3. **One-Class SVM** (Separates normal and fraudulent transactions)
4. **k-Nearest Neighbors (kNN)** (Applied from the PyOD library for fraud detection)
5. **Neural Networks** (Deep learning approach using TensorFlow & Keras)

## Results & Model Performance
Model performance was evaluated using **Precision-Recall Curve, Confusion Matrix, and Classification Report**. Given the imbalanced data, **Precision, Recall, and F1-score** were prioritized over accuracy.

| Model                 | Precision | Recall  | F1-score |
|-----------------------|-----------|--------|---------|
| Isolation Forest     | 0.28      | 0.68   | 0.39    |
| Local Outlier Factor | 0.45      | 0.57   | 0.50    |
| One-Class SVM        | 0.35      | 0.52   | 0.42    |
| kNN (PyOD)           | 0.48      | 0.60   | 0.53    |
| Neural Network       | **0.89**  | **0.91**  | **0.90**  |

- **Neural Networks performed best**, achieving the highest precision and recall.
- **Anomaly detection models** (Isolation Forest, LOF) struggled with the low fraud rate.
- **Ensemble and hybrid approaches** could improve fraud detection further.

## Limitations & Future Work
- **Class imbalance issue**: Fraud detection remains challenging due to the extreme class imbalance.
- **Model trade-offs**: High precision models may miss some fraud cases, while high recall models may produce more false positives.
- **Future improvements**:
  - **SMOTE or ADASYN** for better fraud resampling.
  - **Hyperparameter tuning** to optimize precision-recall trade-off.
  - **Exploring XGBoost, LightGBM, and GAN-based fraud detection models**.

## How to Use
1. Clone this repository:
   ```sh
   git clone https://github.com/YOUR_USERNAME/COMP1916-Fraud-Detection.git
   cd COMP1916-Fraud-Detection
   ```
2. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
3. Run the Jupyter Notebook:
   ```sh
   jupyter notebook
   ```
   Open `COMP 1916 Assessment (1).ipynb` and execute the cells.

## Dependencies
- Python 3.x
- Jupyter Notebook
- NumPy, Pandas, Matplotlib, Seaborn
- Scikit-learn, PyOD (for outlier detection)
- TensorFlow & Keras (for Neural Networks)

## License
This project is under the MIT License.

## .gitignore
```
# Ignore Jupyter notebook checkpoints
.ipynb_checkpoints/

# Ignore temporary files
*.pyc
*.pyo
*.pyd
__pycache__/

# Ignore virtual environment
venv/
.env/

# Ignore dataset files
*.csv
*.xlsx
