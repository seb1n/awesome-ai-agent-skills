---
name: context-retrieval
description: "Retrieves and synthesizes relevant information from a knowledge base to provide context for a given query."
license: "MIT"
---

## Workflow

The context-retrieval skill operates by first embedding the user's query into a high-dimensional vector space. This query embedding is then used to perform a similarity search against a pre-indexed knowledge base of document embeddings. The top-k most similar documents are retrieved and passed to a large language model (LLM) to synthesize a coherent and informative answer.

## Usage

To use this skill, you need a pre-existing knowledge base that has been indexed and embedded. The skill takes a user query as input and returns a string containing the synthesized answer.

## Example

```python
from context_retrieval import retrieve

query = "What are the latest advancements in AI-powered drug discovery?"
context = retrieve(query)
print(context)
```
