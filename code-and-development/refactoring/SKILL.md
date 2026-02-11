---
name: refactoring
description: "Improve code quality and maintainability through automated refactoring."
license: "MIT"
---

## Workflow

This skill helps refactor code by analyzing it for potential improvements and applying automated refactoring techniques. The typical workflow involves:

1.  **Analyze Code**: The agent analyzes the user-provided code to identify areas for refactoring, such as code smells, complex logic, or poor performance.
2.  **Suggest Refactorings**: Based on the analysis, the agent suggests specific refactorings, explaining the benefits of each suggestion.
3.  **Apply Refactorings**: Upon user approval, the agent applies the selected refactorings to the code.
4.  **Test Refactored Code**: The agent runs existing tests or generates new ones to ensure that the refactored code behaves as expected and that no regressions were introduced.

## Usage

To use this skill, provide the code you want to refactor and specify the desired refactoring goals. For example, you can ask the agent to "refactor this Python code to improve its readability" or "refactor this JavaScript function to reduce its complexity."

You can also provide more specific instructions, such as "extract this block of code into a separate function" or "rename this variable to be more descriptive."

## Example

**User Request**: "Refactor the following Python function to be more concise and readable."

**Original Code**:
```python
def process_data(data):
    results = []
    for item in data:
        if item['value'] > 10:
            new_item = {}
            new_item['id'] = item['id']
            new_item['processed_value'] = item['value'] * 2
            results.append(new_item)
    return results
```

**Refactored Code**:
```python
def process_data(data):
    return [
        {"id": item["id"], "processed_value": item["value"] * 2}
        for item in data
        if item["value"] > 10
    ]
```
