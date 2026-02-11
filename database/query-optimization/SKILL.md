---
name: query-optimization
description: "Analyzes and optimizes SQL queries to improve database performance."
license: "MIT"
---

## Workflow

The query-optimization skill analyzes a given SQL query and provides optimization suggestions. The workflow is as follows:

1.  **Analyze Query:** The user provides an SQL query to be analyzed.
2.  **Identify Bottlenecks:** The skill identifies potential performance bottlenecks in the query, such as inefficient joins, missing indexes, or expensive operations.
3.  **Generate Suggestions:** Based on the analysis, the skill generates a list of optimization suggestions.
4.  **Provide Optimized Query:** The skill provides an optimized version of the original query.

## Usage

To use this skill, provide the SQL query you want to optimize. The skill will return a list of suggestions and an optimized query.

### Input

*   `query` (string): The SQL query to be optimized.

### Output

*   `suggestions` (list): A list of optimization suggestions.
*   `optimized_query` (string): The optimized SQL query.

## Example

### Input

```sql
SELECT *
FROM orders
WHERE status = 'shipped' AND order_date >= '2023-01-01';
```

### Output

**Suggestions:**

*   "Consider creating a composite index on the `status` and `order_date` columns of the `orders` table to speed up the query."
*   "Avoid using `SELECT *` and instead specify the columns you need."

**Optimized Query:**

```sql
SELECT order_id, customer_id, order_date, total_amount
FROM orders
WHERE status = 'shipped' AND order_date >= '2023-01-01';
```
