---
name: Model Deployment
description: A skill for deploying machine learning models as scalable and secure APIs, handling everything from environment setup to cloud deployment.
license: MIT
---

## Workflow

This skill automates the deployment of machine learning models, making them accessible via a REST API. The process includes:

1.  **Environment Setup**: Creates a containerized environment with all necessary dependencies.
2.  **API Scaffolding**: Generates a lightweight web server (e.g., using Flask) to wrap the model.
3.  **Deployment**: Deploys the model to a cloud platform, making it available as a scalable and secure API endpoint.

## Usage

To use this skill, you need to provide the following:

*   A trained machine learning model file (e.g., in `.pkl`, `.h5`, or `.pth` format).
*   A `requirements.txt` file listing the Python dependencies.

The skill will then guide you through the deployment process, asking for necessary configurations such as the cloud provider and desired instance type.

## Example

### Input

*   **Model file**: `/home/ubuntu/models/iris_classifier.pkl`
*   **Requirements file**: `/home/ubuntu/models/requirements.txt`

### `requirements.txt`

```
scikit-learn==1.2.2
flask==2.2.2
```

### Output

The skill will generate a directory containing a `Dockerfile`, `app.py`, and other necessary files. It will then build a Docker image and deploy it to the selected cloud provider, providing you with a public API endpoint to access your model.

**Example API request:**

```bash
curl -X POST https://your-api-endpoint.com/predict -H "Content-Type: application/json" -d '{"features": [5.1, 3.5, 1.4, 0.2]}'
```
