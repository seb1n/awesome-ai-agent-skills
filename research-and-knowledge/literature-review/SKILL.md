---
name: literature-review
description: "Conduct a comprehensive literature review on a given topic, synthesizing information from multiple academic sources."
license: "MIT"
---

## Workflow

1.  **Search for relevant academic papers:** Use the `search` tool with the `research` type to find papers, articles, and other academic documents related to the specified topic.
2.  **Analyze search results:** Review the search results and use the `browser` tool to navigate to the most relevant papers.
3.  **Extract key information:** Read the papers and extract key findings, methodologies, and conclusions. Use the `file` tool to save this information.
4.  **Synthesize the literature:** Organize the extracted information, identify common themes and research gaps, and create a coherent synthesis of the literature.
5.  **Generate the review:** Write the final literature review as a Markdown document, including a reference list.

## Usage

To use this skill, you need to provide a research topic. The agent will then follow the workflow to generate a literature review.

### Example

**User request:**

> Conduct a literature review on the impact of artificial intelligence on the job market.

**Agent actions:**

1.  `search(type="research", queries=["impact of artificial intelligence on the job market", "AI and employment", "automation and the future of work"])`
2.  ... (browser, file, etc.)
3.  ... (synthesis)
4.  ... (write final document)
