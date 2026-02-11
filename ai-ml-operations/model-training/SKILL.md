---
name: model-training
description: Train a machine learning model on a given dataset, and evaluate its performance.
license: MIT
---

# Model Training

This skill enables the agent to train a machine learning model on a given dataset. The agent can handle data preprocessing, model selection, training, and evaluation.

## Workflow

1.  **Data preprocessing:** The agent will preprocess the data, including handling missing values, feature scaling, and encoding categorical variables.
2.  **Model selection:** The agent will help the user select an appropriate machine learning model for the given task, such as classification, regression, or clustering.
3.  **Model training:** The agent will train the selected model on the training data, using appropriate techniques to prevent overfitting.
4.  **Model evaluation:** The agent will evaluate the performance of the trained model on a separate test dataset, using relevant metrics such as accuracy, precision, recall, and F1-score.
5.  **Save the trained model:** The agent will save the trained model to a file so that it can be used for making predictions on new data.

## Usage

To use this skill, provide the agent with the dataset, the target variable, and the type of machine learning task.

**Example:**

```
Train a classification model to predict customer churn.

- Dataset: /path/to/customer_data.csv
- Target variable: 'churn'
- Task: Binary classification
```
