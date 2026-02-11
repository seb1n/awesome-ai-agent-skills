---
name: code-documentation
description: A skill for automatically generating documentation for code.
license: MIT
---

## Workflow

This skill analyzes a given codebase and generates comprehensive documentation for it. The documentation includes descriptions of functions, classes, and modules, as well as usage examples.

## Usage

To use this skill, you need to provide the path to the source code you want to document. The skill will then process the code and generate a Markdown file containing the documentation.

## Example

```python
# example.py

def hello_world():
    """Prints 'Hello, World!' to the console."""
    print("Hello, World!")
```

Running the skill on this file would produce a `documentation.md` file with the following content:

```markdown
# Documentation for example.py

## Functions

### `hello_world()`

Prints 'Hello, World!' to the console.
```
