---
name: Hyperparameter Tuning
description: A skill for optimizing machine learning model hyperparameters to improve performance.
license: MIT
---

## Workflow

This skill automates the process of hyperparameter tuning for machine learning models. The workflow is as follows:

1.  **Define Search Space:** The user specifies the hyperparameters and their ranges to be explored.
2.  **Select Search Algorithm:** The user chooses a search algorithm, such as Grid Search, Random Search, or Bayesian Optimization.
3.  **Cross-Validation:** The skill performs cross-validation to evaluate the performance of each hyperparameter combination.
4.  **Return Best Parameters:** The skill returns the set of hyperparameters that yielded the best performance, along with the corresponding evaluation metric.

## Usage

To use this skill, you need to provide the following:

*   A machine learning model (e.g., a scikit-learn estimator).
*   A dataset for training and evaluation.
*   A dictionary defining the hyperparameter search space.
*   The desired search algorithm.

## Example

Here is an example of how to use the skill to tune the hyperparameters of a Support Vector Machine (SVM) classifier:

```python
from sklearn.svm import SVC
from sklearn.datasets import load_iris

# Load the dataset
iris = load_iris()
X, y = iris.data, iris.target

# Define the model
model = SVC()

# Define the hyperparameter search space
param_grid = {
    'C': [0.1, 1, 10, 100],
    'gamma': [1, 0.1, 0.01, 0.001],
    'kernel': ['rbf', 'poly', 'sigmoid']
}

# Specify the search algorithm
search_algorithm = 'GridSearchCV'

# The skill would then perform the search and return the best parameters
# best_params = {
#     'C': 10,
#     'gamma': 0.1,
#     'kernel': 'rbf'
# }
```
