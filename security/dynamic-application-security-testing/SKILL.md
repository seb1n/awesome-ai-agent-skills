---
name: dynamic-application-security-testing
description: A skill to perform dynamic application security testing (DAST) on web applications to identify security vulnerabilities.
license: MIT
---

## Workflow

This skill automates the process of dynamic application security testing (DAST) for web applications. It leverages popular open-source tools to scan a target URL for common security vulnerabilities.

1.  **Target Specification**: The user provides the target URL of the web application to be scanned.
2.  **DAST Scan**: The skill initiates a DAST scan using a tool like OWASP ZAP or Nikto. The scan actively probes the application for vulnerabilities such as SQL injection, cross-site scripting (XSS), and insecure server configurations.
3.  **Report Generation**: Upon completion of the scan, the skill generates a report detailing the findings. The report includes a list of identified vulnerabilities, their severity levels, and recommendations for remediation.
4.  **Result Delivery**: The skill provides the generated report to the user.

## Usage

To use this skill, you need to provide the URL of the web application you want to test.

**Input**

*   `url`: The URL of the web application to be scanned.

## Example

**Task**: Perform a dynamic application security test on the web application at `http://example.com`.

**Input**

```json
{
  "url": "http://example.com"
}
```

**Output**

The skill will output a report file (e.g., `dast-report.json` or `dast-report.html`) containing the security vulnerabilities found in the application.
