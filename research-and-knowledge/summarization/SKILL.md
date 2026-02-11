---
name: summarization
description: "Summarize long-form text, such as articles, reports, and documents, into concise and informative summaries."
license: "MIT"
---

### Workflow

The summarization skill follows a straightforward workflow designed to provide quick and accurate summaries of textual content.

1.  **Input Text**: The user provides the text to be summarized. This can be a block of text, a file path, or a URL pointing to a document.
2.  **Summarization**: The skill processes the input text and generates a summary. The length and style of the summary can be adjusted based on user preferences.
3.  **Output**: The generated summary is returned to the user as a text string.

### Usage

To use the summarization skill, you need to provide the text you want to summarize. You can also specify the desired length of the summary (e.g., short, medium, long).

#### Parameters

*   `text` (string, required): The text to be summarized.
*   `length` (string, optional, default: "medium"): The desired length of the summary. Possible values are "short", "medium", and "long".
*   `source` (string, optional): The source of the text, such as a URL or file path.

### Example

Here's an example of how to use the summarization skill:

**Input:**

```json
{
  "text": "The quick brown fox jumps over the lazy dog. This is a classic sentence used for testing typewriters and fonts. It contains all the letters of the English alphabet.",
  "length": "short"
}
```

**Output:**

```json
{
  "summary": "A classic sentence containing all letters of the alphabet, used for testing typewriters."
}
```
