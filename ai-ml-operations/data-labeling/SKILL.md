---
name: data-labeling
description: A skill for labeling various types of data for machine learning models.
license: MIT
---

## Workflow

This skill provides a structured workflow for data labeling, a crucial step in preparing data for machine learning models. The process involves:

1.  **Defining the Labeling Task:** Clearly outline the data to be labeled, the types of labels to be applied, and the specific instructions for the labeling process.
2.  **Data Ingestion:** Import the dataset that requires labeling. This can be a collection of images, text files, audio clips, or other data formats.
3.  **Labeling Interface:** Utilize a user-friendly interface to apply labels to the data points. This skill can be integrated with various labeling tools or provide a simple built-in interface.
4.  **Quality Assurance:** Implement a review process to ensure the accuracy and consistency of the labels. This may involve multiple reviewers or automated checks.
5.  **Exporting Labeled Data:** Export the labeled dataset in a format that is compatible with machine learning frameworks such as TensorFlow or PyTorch.

## Usage

To use this skill, you will need to provide the following:

*   **A dataset:** The collection of data to be labeled.
*   **Labeling guidelines:** A clear set of instructions for how to label the data.
*   **Labeling schema:** The set of possible labels that can be applied.

The skill can be initiated with a command, specifying the dataset and the labeling configuration.

## Example

Here is an example of how to use the data labeling skill to label a dataset of images for a cat and dog classification model.

1.  **Dataset:** A folder containing 1000 images of cats and dogs.
2.  **Labeling Guidelines:**
    *   Draw a bounding box around each cat and dog in the image.
    *   Label the bounding box as either 'cat' or 'dog'.
3.  **Labeling Schema:**
    *   cat
    *   dog

The skill would then launch a labeling interface where the user can draw bounding boxes and assign labels to the images. Once the labeling is complete, the skill would export a JSON file containing the image file names and their corresponding bounding box coordinates and labels.
