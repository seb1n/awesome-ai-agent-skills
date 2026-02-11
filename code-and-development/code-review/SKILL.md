---
name: code-review
description: Conduct a thorough code review of a given file or pull request, checking for bugs, style violations, and performance issues.
license: MIT
---

# Code Review

This skill enables the agent to perform a detailed code review on a given file or pull request. The agent will analyze the code for potential bugs, adherence to coding style guidelines, and performance bottlenecks.

## Workflow

1.  **Analyze the code:** The agent will read the provided code and build an understanding of its functionality and structure.
2.  **Check for bugs:** The agent will look for common programming errors, such as null pointer exceptions, off-by-one errors, and resource leaks.
3.  **Verify style compliance:** The agent will check the code against a predefined set of coding style guidelines (e.g., PEP 8 for Python, Google Java Style Guide for Java).
4.  **Identify performance issues:** The agent will look for inefficient algorithms, unnecessary object allocations, and other performance anti-patterns.
5.  **Generate a review report:** The agent will produce a detailed report of its findings, including specific code snippets and suggestions for improvement.

## Usage

To use this skill, provide the agent with the path to the file or the URL of the pull request you want to be reviewed.

**Example:**

```
/path/to/your/file.py
```

```
https://github.com/user/repo/pull/123
```
