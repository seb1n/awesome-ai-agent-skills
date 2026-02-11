---
name: ml-pipeline-creation
description: A skill to create, manage, and automate machine learning pipelines.
license: MIT
---

## Workflow

This skill enables the creation and management of machine learning (ML) pipelines, automating the process of training, evaluating, and deploying ML models. The workflow is designed to be flexible and adaptable to various ML tasks and frameworks.

1.  **Define Pipeline Structure**: The user specifies the stages of the ML pipeline, including data preprocessing, model training, model evaluation, and deployment. This is typically done in a configuration file (e.g., YAML or JSON).
2.  **Component Implementation**: Each stage of the pipeline is implemented as a separate component. These components are reusable and can be chained together to form a complete pipeline.
3.  **Pipeline Execution**: The skill executes the pipeline, running each component in the specified order. It handles data flow between components and manages dependencies.
4.  **Monitoring and Logging**: The skill provides tools for monitoring the pipeline's execution, logging results, and tracking experiments.
5.  **Deployment**: Once a model is trained and evaluated, the skill can automate its deployment to a serving environment.

## Usage

To use this skill, you need to provide a pipeline definition file and the implementation of the pipeline components.

### Example: Simple Scikit-learn Pipeline

Here's an example of how to define and run a simple ML pipeline using this skill.

**`pipeline.yaml`**

```yaml
name: simple-sklearn-pipeline
components:
  - name: data-preprocessing
    script: preprocess.py
    inputs:
      - raw_data: /path/to/raw_data.csv
    outputs:
      - processed_data: /path/to/processed_data.csv
  - name: train-model
    script: train.py
    inputs:
      - processed_data: /path/to/processed_data.csv
    outputs:
      - model: /path/to/model.pkl
  - name: evaluate-model
    script: evaluate.py
    inputs:
      - model: /path/to/model.pkl
      - test_data: /path/to/test_data.csv
    outputs:
      - metrics: /path/to/metrics.json
```

**`preprocess.py`**

```python
import pandas as pd
from sklearn.model_selection import train_test_split

# Load data
df = pd.read_csv('/path/to/raw_data.csv')

# Simple preprocessing
X = df.drop('target', axis=1)
y = df['target']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Save processed data
pd.concat([X_train, y_train], axis=1).to_csv('/path/to/processed_data.csv', index=False)
pd.concat([X_test, y_test], axis=1).to_csv('/path/to/test_data.csv', index=False)
```

**`train.py`**

```python
import pandas as pd
from sklearn.ensemble import RandomForestClassifier
import joblib

# Load processed data
df = pd.read_csv('/path/to/processed_data.csv')
X_train = df.drop('target', axis=1)
y_train = df['target']

# Train model
model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# Save model
joblib.dump(model, '/path/to/model.pkl')
```

**`evaluate.py`**

```python
import pandas as pd
import joblib
import json
from sklearn.metrics import accuracy_score

# Load model and test data
model = joblib.load('/path/to/model.pkl')
df = pd.read_csv('/path/to/test_data.csv')
X_test = df.drop('target', axis=1)
y_test = df['target']

# Evaluate model
y_pred = model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)

# Save metrics
with open('/path/to/metrics.json', 'w') as f:
    json.dump({'accuracy': accuracy}, f)

print(f'Model accuracy: {accuracy}')
```
