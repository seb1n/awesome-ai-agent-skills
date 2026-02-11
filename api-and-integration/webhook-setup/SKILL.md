---
name: webhook-setup
description: "Set up and manage webhooks to receive real-time notifications and data from other applications."
license: "MIT"
---

## Workflow

1.  **Get Webhook URL:** Obtain the unique webhook URL from the source application where you want to receive events.
2.  **Configure Webhook:** In the source application, navigate to the webhook settings and add a new webhook, pasting the URL.
3.  **Select Events:** Choose the specific events that should trigger the webhook.
4.  **Save and Test:** Save the webhook configuration and send a test event to ensure it's working correctly.

## Usage

Use this skill to automate workflows by connecting different applications. For example, you can receive a notification in a chat application when a new issue is created in a project management tool.

## Example

To receive a Slack notification for a new GitHub commit:

1.  In Slack, create an incoming webhook and copy the URL.
2.  In your GitHub repository settings, go to "Webhooks" and click "Add webhook".
3.  Paste the Slack webhook URL in the "Payload URL" field.
4.  Select "Just the push event" and click "Add webhook".
