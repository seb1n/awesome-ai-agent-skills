_**
name: Dependency Scanning
description: Scans project dependencies for known vulnerabilities.
license: MIT
**_

## Workflow

1. **Scan Project**: The agent scans the project's dependency files (e.g., `package.json`, `requirements.txt`).
2. **Identify Vulnerabilities**: It uses a vulnerability database to identify any known security issues in the dependencies.
3. **Generate Report**: A report is generated listing the vulnerabilities, their severity, and recommended actions.

## Usage

To use this skill, simply ask the agent to scan your project for vulnerabilities. For example:

> "Scan my project for security vulnerabilities."

## Example

```
> Scan my project for security vulnerabilities.

Scanning dependencies...

Found 3 vulnerabilities:

- **High**: `some-package` version 1.2.3 has a critical remote code execution vulnerability. Recommended action: Upgrade to version 1.2.4 or later.
- **Medium**: `another-package` version 2.0.1 has a cross-site scripting (XSS) vulnerability. Recommended action: Upgrade to version 2.1.0 or later.
- **Low**: `yet-another-package` version 3.4.5 has a denial-of-service (DoS) vulnerability. Recommended action: No immediate action required, but monitor for updates.
```
