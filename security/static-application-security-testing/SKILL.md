---
name: Static Application Security Testing
description: Analyzes source code to find security vulnerabilities using static analysis tools.
license: MIT
---

## Workflow

This skill automates Static Application Security Testing (SAST) on a given codebase to identify potential security vulnerabilities. The workflow is as follows:

1.  **Language Detection**: The skill first determines the primary programming language of the target repository.
2.  **Tool Selection**: Based on the detected language, it selects an appropriate open-source SAST tool.
3.  **Code Analysis**: The selected tool is then used to scan the entire codebase for security flaws, misconfigurations, and anti-patterns.
4.  **Report Generation**: Finally, the skill generates a report of the findings, including the vulnerability type, location (file and line number), and severity.

## Usage

To use this skill, you need to provide the path to the source code repository you want to analyze. The skill will handle the rest of the process automatically.

### Example

Let's say you have a Python-based project in the `/home/ubuntu/my-python-app` directory. You can invoke the skill as follows:

```
Analyze the source code in /home/ubuntu/my-python-app for security vulnerabilities using SAST.
```

The skill will then perform the analysis and output a report detailing any found vulnerabilities, such as insecure use of `pickle`, hardcoded passwords, or SQL injection risks.
