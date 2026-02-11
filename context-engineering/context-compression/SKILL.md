---
name: context-compression
description: A skill for compressing context to fit within model token limits.
license: MIT
---

## Workflow

This skill is designed to condense large amounts of text into a more concise format, making it suitable for processing by language models with limited context windows. The workflow is as follows:

1.  **Input Text**: The user provides a long-form text document that needs to be compressed.
2.  **Summarization**: The skill uses a summarization model to extract the key information and main points from the text.
3.  **Output**: The skill returns a compressed version of the text that retains the essential information.

## Usage

To use this skill, you will need to provide the text you want to compress as input. The skill can be invoked through a function call, as shown in the example below.

## Example

```python
from skills.context_compression import compress

long_text = """
Artificial intelligence (AI) is intelligence demonstrated by machines, as opposed to the natural intelligence displayed by humans and other animals. AI research has been defined as the field of study of intelligent agents, which refers to any system that perceives its environment and takes actions that maximize its chance of successfully achieving its goals. The term "artificial intelligence" had previously been used to describe machines that mimic and display "human" cognitive skills that are associated with the human mind, such as "learning" and "problem-solving". This definition has since been rejected by major AI researchers who now describe AI in terms of rationality and acting rationally, which does not limit how intelligence can be articulated.
"""

compressed_text = compress(long_text)

print(compressed_text)
```
