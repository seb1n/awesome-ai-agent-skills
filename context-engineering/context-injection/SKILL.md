---
name: context-injection
description: Injects contextual information into prompts to improve AI model performance.
license: MIT
---

# Context Injection Skill

This skill enhances AI model performance by dynamically injecting relevant contextual information into prompts.

## Workflow

1.  **Identify Need for Context**: Determine when a task requires additional information to be completed accurately.
2.  **Gather Context**: Collect the necessary contextual data from available sources.
3.  **Inject Context**: Insert the gathered information directly into the prompt before execution.
4.  **Execute Prompt**: Run the modified prompt to leverage the provided context for a more informed response.

## Usage

Use this skill whenever an AI model's performance can be improved by providing it with specific, relevant information. This is particularly useful for tasks involving summarization, analysis, or question-answering based on a given document or set of data.

## Example

**Original Prompt:**
```
Summarize the quarterly financial report.
```

**Prompt with Injected Context:**
```
Summarize the following quarterly financial report: [Insert full text of the financial report here]
```
