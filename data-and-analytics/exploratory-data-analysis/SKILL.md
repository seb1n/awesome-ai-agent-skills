---
name: exploratory-data-analysis
description: A skill for performing exploratory data analysis on datasets.
license: MIT
---

## Workflow

This skill analyzes a dataset to uncover initial patterns, anomalies, and insights. The general workflow is as follows:

1.  **Load Data**: The agent loads a dataset from a provided file path (e.g., CSV, Excel).
2.  **Initial Analysis**: The agent performs a preliminary analysis of the dataset, including:
    *   Displaying the first few rows.
    *   Providing a summary of the data types.
    *   Generating descriptive statistics (mean, median, standard deviation, etc.).
3.  **Data Cleaning**: The agent identifies and handles missing values.
4.  **Visualization**: The agent creates various plots to visualize the data, such as histograms, box plots, and scatter plots.
5.  **Correlation Analysis**: The agent calculates and visualizes the correlation between different variables in the dataset.
6.  **Summarize Findings**: The agent provides a summary of the key findings from the analysis.

## Usage

To use this skill, you need to provide the path to your dataset. The agent will then perform the exploratory data analysis and present the results.

**Example Prompt:**

"Perform an exploratory data analysis on the dataset located at `/home/ubuntu/datasets/my_data.csv`."

## Example

### User Request

"I have a dataset of housing prices. Can you perform an exploratory data analysis on it? The file is at `/home/ubuntu/datasets/housing.csv`."

### Agent Actions

1.  **Load Data**: The agent loads the `housing.csv` file into a pandas DataFrame.
2.  **Initial Analysis**:
    *   The agent displays the first 5 rows of the DataFrame.
    *   It shows the data types of each column (e.g., `price` is a float, `bedrooms` is an integer).
    *   It provides descriptive statistics for the numerical columns.
3.  **Data Cleaning**: The agent checks for missing values and reports that there are no missing values in this dataset.
4.  **Visualization**:
    *   The agent generates a histogram of the `price` column to show the distribution of housing prices.
    *   It creates a scatter plot of `price` vs. `square_feet` to visualize the relationship between these two variables.
5.  **Correlation Analysis**: The agent calculates the correlation matrix for all numerical columns and displays it as a heatmap.
6.  **Summarize Findings**: The agent provides a summary of the findings, such as "The price of a house is strongly correlated with its square footage."
