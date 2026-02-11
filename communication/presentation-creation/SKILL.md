---
name: presentation-creation
description: Create professional presentations from a detailed outline.
license: MIT
---

## Workflow

This skill enables the creation of professional presentations from a detailed outline provided in a Markdown file. The workflow consists of the following steps:

1.  **Outline Creation**: The user provides a detailed outline of the presentation in a Markdown file. This file should specify the content for each slide.
2.  **Presentation Generation**: The `slides` tool is used to generate the presentation. The tool takes the path to the Markdown file, the total number of slides, and the generation mode (`html` or `image`) as input.
3.  **Output**: The `slides` tool generates the presentation, which can then be exported to various formats like PDF or PPTX.

## Usage

To use this skill, you need to have a Markdown file with the presentation outline. Then, you can use the `slides` tool to generate the presentation.

## Example

Here is an example of how to use the `slides` tool to create a presentation:

```tool_code
print(default_api.slides(brief="Generate a 5-slide presentation from the 'presentation_outline.md' file.", slide_content_file_path="/home/ubuntu/presentation_outline.md", slide_count=5, generate_mode="html"))
```
