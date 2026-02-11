---
name: debugging
description: Debug a piece of code by identifying and fixing errors, and explaining the root cause of the issue.
license: MIT
---

# Debugging

This skill equips the agent with the ability to debug code. The agent can identify errors, propose fixes, and provide explanations for the root cause of the problem.

## Workflow

1.  **Understand the code and the error:** The agent will analyze the provided code and the error message or description of the unexpected behavior.
2.  **Identify the root cause:** The agent will use various debugging techniques, such as analyzing stack traces, examining variable values, and stepping through the code, to pinpoint the root cause of the error.
3.  **Propose a fix:** The agent will suggest a code modification to fix the error.
4.  **Explain the fix:** The agent will explain why the proposed fix works and how it addresses the root cause of the problem.

## Usage

To use this skill, provide the agent with the code snippet that is causing the error, along with the error message or a description of the problem.

**Example:**

```python
# Code with a bug
def divide(a, b):
    return a / b

result = divide(10, 0)
print(result)
```

**Error Message:**

```
ZeroDivisionError: division by zero
```
