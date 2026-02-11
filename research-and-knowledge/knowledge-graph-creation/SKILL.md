---
name: Knowledge Graph Creation
description: "Create a knowledge graph from unstructured text by extracting entities and relationships, and then visualizing the graph."
license: "MIT"
---

## Workflow

1.  **Extract Entities and Relationships**: Use a language model to extract key entities (nodes) and the relationships between them (edges) from the input text.
2.  **Structure the Data**: Format the extracted entities and relationships into a structured format, such as JSON or CSV, that can be used to build the graph.
3.  **Visualize the Graph**: Use a graph visualization library to create a visual representation of the knowledge graph.

## Usage

This skill can be used to:

*   Summarize complex documents and articles.
*   Identify key concepts and their connections in a body of text.
*   Build a knowledge base from unstructured data.

## Example

**Input Text:**

"John, a software engineer at Google, is working on a new project with his colleague, Mary. The project is focused on developing a new machine learning model."

**Extracted Entities and Relationships:**

*   **Entities**: John, Mary, Google, machine learning model
*   **Relationships**:
    *   John -> works at -> Google
    *   John -> works with -> Mary
    *   John -> works on -> machine learning model
    *   Mary -> works with -> John
    *   Mary -> works on -> machine learning model

**Graph Visualization:**

(A visual representation of the graph with nodes and edges)
