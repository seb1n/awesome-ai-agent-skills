---
name: kubernetes-deployment
description: "Deploy and manage applications on Kubernetes."
license: "MIT"
---

## Workflow

This skill enables the agent to deploy and manage applications on a Kubernetes cluster. It provides a streamlined workflow for handling Kubernetes deployments, services, and pods.

1.  **Configure kubectl**: Ensure `kubectl` is configured to connect to the desired Kubernetes cluster.
2.  **Define Deployment**: Create a Kubernetes deployment manifest file (e.g., `deployment.yaml`) that specifies the application container image, replicas, and other configuration.
3.  **Apply Deployment**: Use `kubectl apply -f deployment.yaml` to create or update the deployment on the cluster.
4.  **Expose Service**: If needed, create a service manifest file (e.g., `service.yaml`) to expose the deployment to internal or external traffic.
5.  **Apply Service**: Use `kubectl apply -f service.yaml` to create the service.
6.  **Monitor Status**: Check the status of the deployment and pods using `kubectl get deployments`, `kubectl get pods`, and `kubectl logs`.

## Usage

To use this skill, you need to have `kubectl` installed and configured in the agent's environment. You will also need to provide the necessary Kubernetes manifest files for your application.

### Commands

-   `kubectl apply -f <deployment-file.yaml>`: Deploy an application from a manifest file.
-   `kubectl get deployments`: List deployments in the current namespace.
-   `kubectl get pods`: List pods in the current namespace.
-   `kubectl logs <pod-name>`: View logs for a specific pod.
-   `kubectl delete deployment <deployment-name>`: Delete a deployment.

## Example

Here is an example of deploying a simple Nginx web server on Kubernetes.

**`deployment.yaml`**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

**`service.yaml`**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: LoadBalancer
```

**Deployment Steps**

1.  Save the above YAML content to `deployment.yaml` and `service.yaml`.
2.  Run `kubectl apply -f deployment.yaml`.
3.  Run `kubectl apply -f service.yaml`.
4.  Run `kubectl get pods` to see the Nginx pods being created.
5.  Run `kubectl get services` to get the external IP of the Nginx service.
