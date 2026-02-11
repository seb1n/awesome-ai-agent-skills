---
name: report-generation
description: A skill for generating professional reports from structured data.
license: MIT
---

## Workflow

1.  **Data Input**: The user provides structured data in a supported format (e.g., CSV, JSON).
2.  **Template Selection**: The user selects a report template from a predefined list or provides a custom template.
3.  **Report Generation**: The skill processes the data and populates the selected template to generate the report.
4.  **Output**: The generated report is saved as a PDF file.

## Usage

To use this skill, you need to provide the following inputs:

*   `data_file`: The path to the structured data file.
*   `template_id`: The ID of the report template to use.
*   `output_path`: The path to save the generated report.

## Example

```python
from skills.report_generation import ReportGenerator

generator = ReportGenerator()
generator.generate(
    data_file='data.csv',
    template_id='financial_summary',
    output_path='financial_report.pdf'
)
```
