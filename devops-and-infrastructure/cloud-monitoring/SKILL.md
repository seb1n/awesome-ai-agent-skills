---
name: cloud-monitoring
description: A skill for monitoring cloud infrastructure and applications, providing real-time insights into performance, health, and costs.
license: MIT
---

## Workflow

This skill enables the agent to monitor cloud environments by integrating with various cloud providers and monitoring services. The typical workflow is as follows:

1.  **Configuration**: The user specifies the cloud provider (e.g., AWS, GCP, Azure) and the services to monitor.
2.  **Metric Collection**: The agent collects metrics from the specified services, such as CPU utilization, memory usage, network traffic, and application-level performance data.
3.  **Alerting**: The agent can be configured to trigger alerts based on predefined thresholds or anomalous behavior.
4.  **Reporting**: The agent can generate reports and dashboards to visualize the collected data and provide insights into the health and performance of the cloud infrastructure.

## Usage

To use this skill, you need to provide the following information:

*   **Cloud Provider**: The name of the cloud provider (e.g., `aws`, `gcp`, `azure`).
*   **Services**: A list of services to monitor (e.g., `ec2`, `s3`, `lambda`).
*   **Metrics**: The specific metrics to collect for each service.
*   **Alerting Rules**: The conditions under which to trigger alerts.

### Example

Here is an example of how to use the `cloud-monitoring` skill to monitor an AWS EC2 instance:

```json
{
  "skill": "cloud-monitoring",
  "provider": "aws",
  "services": [
    {
      "name": "ec2",
      "instance_id": "i-1234567890abcdef0",
      "metrics": ["cpu_utilization", "memory_usage"],
      "alerts": [
        {
          "metric": "cpu_utilization",
          "threshold": 80,
          "operator": ">"
        }
      ]
    }
  ]
}
```

This example configures the agent to monitor the CPU utilization and memory usage of a specific EC2 instance. An alert will be triggered if the CPU utilization exceeds 80%.
