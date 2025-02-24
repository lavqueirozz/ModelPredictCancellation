# Subscription Cancellation Prediction Model

This project focuses on building a machine learning model to predict subscription cancellations using a classification approach. The model is designed to analyze customer data and identify patterns that may lead to subscription cancellations, helping businesses take proactive measures to retain customers.

## Table of Contents
1. [Introduction](#introduction)
2. [Data Analysis and Collection](#data-analysis-and-collection)
3. [Data Preprocessing](#data-preprocessing)
4. [Feature Engineering](#feature-engineering)
5. [Model Training](#model-training)
6. [Results](#results)
7. [Conclusion](#conclusion)

## Introduction
The goal of this project is to predict whether a customer will cancel their subscription based on various features such as contract duration, payment history, and customer demographics. The model uses a **K-Nearest Neighbors (KNN)** classifier to make predictions.

## Data Analysis and Collection
The dataset contains **448,447 rows** and **24 columns**, including both numerical and categorical features. Key categorical features include:
- `SITUACAO` (Subscription Status)
- `NOME_PRODUTO` (Product Name)
- `DURACAO_CONTRATO` (Contract Duration)
- `SEXO` (Gender)
- `FORMA_AQUISICAO` (Acquisition Method)

### Key Insights:
- The most popular product is the **Basic Plan (30 canais HD)**.
- The preferred contract duration is **48 months**.
- Missing values were found in the `QT_FILHOS` (Number of Children) and `DT_CANCELAMENTO` (Cancellation Date) columns.

## Data Preprocessing
### Handling Missing Values:
- Missing values in the `QT_FILHOS` column were filled with the median value.
- Outliers in the `QT_FILHOS`, `QT_PC_PAGAS` (Number of Paid Installments), and `QT_PC_PAGA_EM_DIA` (Number of Installments Paid on Time) columns were addressed by filtering out values exceeding 48 months.

### Data Transformation:
- Categorical variables were encoded using **Label Encoding**.
- A new feature, `NIVEL_PAGAMENTO` (Payment Level), was created to categorize customers based on their payment history.

## Feature Engineering
- The `NIVEL_PAGAMENTO` feature was created using the `pd.cut` function to categorize customers into **BAD**, **MEDIUM**, **GOOD**, and **GREAT** based on their payment history.

## Model Training
### Data Balancing:
- The dataset was imbalanced, with more active customers than inactive ones. To address this, the **SMOTE (Synthetic Minority Over-sampling Technique)** was applied to balance the dataset.

### Model Training:
- The data was split into training and testing sets.
- The **K-Nearest Neighbors (KNN)** classifier was used to train the model.
- The model was trained with different values of `k` (number of neighbors) to find the optimal value.

### Results:
- The best accuracy was achieved with **k = 7**, resulting in a **97% accuracy** on the test set.

## Conclusion
The model successfully predicts subscription cancellations with a high accuracy rate of **97%**. This can help businesses identify at-risk customers and implement retention strategies to reduce churn.

## How to Use
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/subscription-cancellation-prediction.git
   ```
2. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Jupyter notebook:
   ```bash
   jupyter notebook ModelPredictCancellation.ipynb
   ```

## Dependencies
- Python 3.x
- Pandas
- NumPy
- Scikit-learn
- Imbalanced-learn
- Matplotlib
- Seaborn
