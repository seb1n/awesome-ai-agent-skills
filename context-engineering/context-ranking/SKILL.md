---
name: Context Ranking
description: Ranks and filters context to improve the performance of language models.
license: MIT
---

## Workflow

1.  **Analyze Context**: The skill first analyzes the provided context to understand its structure and content.
2.  **Rank by Relevance**: It then ranks the different parts of the context based on their relevance to the current query or task.
3.  **Filter and Summarize**: Finally, it filters out irrelevant information and summarizes the most important points to create a condensed and focused context.

## Usage

This skill is most effective when used as a pre-processing step before feeding context to a large language model. It helps to reduce noise and improve the model's ability to generate accurate and relevant responses.

## Example

```python
from context_ranking import rank_context

query = "What are the main features of the new product?"
context = """
The new product, called 'InnovateX', is a revolutionary tool for developers. 
It offers a wide range of features, including an intuitive user interface, 
powerful debugging tools, and seamless integration with popular version control systems. 
InnovateX is also highly customizable, allowing users to tailor it to their specific needs.
The product is scheduled to be released in the third quarter of this year.
"""

ranked_context = rank_context(query, context)

print(ranked_context)
```
