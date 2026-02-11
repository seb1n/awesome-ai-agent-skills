---
name: file-organization
description: "Automatically organizes files in a specified directory into subdirectories based on file type."
license: "MIT"
---

## Workflow

This skill organizes files within a designated directory by sorting them into subdirectories based on their file extensions. It iterates through each file in the source directory, determines the file type from its extension, and moves it to a corresponding subdirectory (e.g., all `.jpg` files are moved to an `images` directory).

## Usage

To use this skill, you need to provide the path to the directory that you want to organize. The skill will then handle the creation of subdirectories and the moving of files.

### Example

If you have a directory named `Downloads` with the following files:
- `document.pdf`
- `image.jpg`
- `archive.zip`
- `presentation.pptx`

After applying the skill, the `Downloads` directory will be structured as follows:
- `Downloads/`
  - `documents/`
    - `document.pdf`
  - `images/`
    - `image.jpg`
  - `archives/`
    - `archive.zip`
  - `presentations/`
    - `presentation.pptx`
