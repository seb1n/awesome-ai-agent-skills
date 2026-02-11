---
name: data-cleaning
description: "Clean and preprocess data from various sources to ensure data quality and consistency."
license: "MIT"
---

## Workflow

The data cleaning skill is designed to automate the process of identifying and correcting errors, inconsistencies, and inaccuracies in datasets. The typical workflow involves the following steps:

1.  **Data Ingestion**: Load the dataset from a specified source, such as a CSV file, database, or API.
2.  **Initial Assessment**: Perform a preliminary analysis of the data to identify potential issues, such as missing values, duplicates, and incorrect data types.
3.  **Cleaning Operations**: Apply a series of cleaning operations based on the assessment, which may include:
    *   Handling missing values (e.g., imputation, removal).
    *   Removing duplicate records.
    *   Correcting data types.
    *   Standardizing formats (e.g., dates, addresses).
    *   Resolving inconsistencies.
4.  **Validation**: Verify that the cleaning operations have been successful and that the data is now consistent and accurate.
5.  **Output**: Save the cleaned dataset to a new file or database table.

## Usage

To use the data cleaning skill, you need to provide the path to the dataset and specify the cleaning operations to be performed. You can configure the skill to handle different types of data and cleaning tasks.

## Example

Here is an example of how to use the data cleaning skill to clean a CSV file named `sales_data.csv`:

```python
from data_cleaning_skill import clean_data

# Specify the path to the dataset
data_path = "path/to/sales_data.csv"

# Define the cleaning operations
cleaning_config = {
    "missing_values": "impute_mean",
    "duplicates": "remove",
    "data_types": {
        "order_date": "datetime",
        "price": "float"
    }
}

# Clean the data
cleaned_data = clean_data(data_path, cleaning_config)

# Save the cleaned data
cleaned_data.to_csv("path/to/cleaned_sales_data.csv", index=False)
```
