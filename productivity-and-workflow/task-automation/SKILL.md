---
name: task-automation
description: Automate repetitive tasks and workflows using AI.
license: MIT
---

# Task Automation Skill

This skill allows the agent to automate repetitive tasks and workflows.

## Workflow

1.  **Define the Task:** Clearly define the task you want to automate.
2.  **Break Down the Task:** Break down the task into smaller, manageable steps.
3.  **Identify the Tools:** Identify the tools and resources needed for each step.
4.  **Write the Script:** Write a script to automate the task using the identified tools.
5.  **Test and Refine:** Test the script and refine it until it works as expected.

## Usage

This skill can be used to automate a wide range of tasks, including:

*   Sending automated emails
*   Generating reports
*   Scraping websites
*   Managing social media accounts

## Example

Here is an example of how to use this skill to automate the task of sending a daily report:

1.  **Define the Task:** Send a daily report to a list of recipients.
2.  **Break Down the Task:**
    *   Get the data for the report.
    *   Generate the report.
    *   Send the report to the recipients.
3.  **Identify the Tools:**
    *   Python for scripting
    *   Pandas for data manipulation
    *   smtplib for sending emails
4.  **Write the Script:**

    '''python
    import pandas as pd
    import smtplib

    # Get the data for the report
    data = {'col1': [1, 2], 'col2': [3, 4]}
    df = pd.DataFrame(data)

    # Generate the report
    report = df.to_string()

    # Send the report
    sender = 'your_email@example.com'
    receivers = ['recipient1@example.com', 'recipient2@example.com']
    message = f"""\
    Subject: Daily Report
    To: {", ".join(receivers)}
    From: {sender}

    {report}
    """

    with smtplib.SMTP('smtp.example.com', 587) as server:
        server.starttls()
        server.login('your_email@example.com', 'your_password')
        server.sendmail(sender, receivers, message)
    '''

5.  **Test and Refine:** Test the script and refine it as needed.
