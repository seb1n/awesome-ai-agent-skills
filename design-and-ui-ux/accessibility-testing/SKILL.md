---
name: accessibility-testing
description: A skill for testing web accessibility to ensure compliance with WCAG standards.
license: MIT
---

# Accessibility Testing Skill

This skill enables the agent to perform automated accessibility tests on web pages to identify and report violations of the Web Content Accessibility Guidelines (WCAG).

## Workflow

1.  **Receive URL**: The user provides a URL to a web page for accessibility testing.
2.  **Launch Browser**: The agent launches a headless browser and navigates to the specified URL.
3.  **Run Audit**: It executes an accessibility audit using a specialized tool (e.g., Axe-core) to analyze the page's DOM.
4.  **Process Results**: The audit results are processed to extract detailed information about any accessibility violations, including their severity and impact.
5.  **Generate Report**: A comprehensive report is generated, summarizing the findings. The report includes a list of specific issues, code snippets, and actionable recommendations for remediation.

## Usage

This skill is designed for developers, designers, and QA testers who need to ensure their web applications are accessible to people with disabilities. It can be used for one-off tests or integrated into a continuous integration/continuous deployment (CI/CD) pipeline for automated regression testing.

## Example

**User Request**: "Please run an accessibility check on the homepage of `https://my-company-website.com`."

**Agent Action**:

1.  The agent activates the `accessibility-testing` skill.
2.  It navigates to `https://my-company-website.com` in a headless browser.
3.  It runs a full accessibility scan.
4.  The agent then presents a summary of the results to the user, such as:

> "I found 15 accessibility issues on the homepage. The most critical issues are:
> *   **Color Contrast**: 5 instances of text with insufficient color contrast.
> *   **Missing Alt Text**: 3 images are missing alternative text.
> *   **Form Labels**: 2 form fields do not have corresponding labels.
>
> A detailed report has been saved to `accessibility_report.json`."
