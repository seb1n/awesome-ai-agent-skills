---
name: SQL Query Generation
description: Generate SQL queries from natural language prompts.
license: MIT
---

## Workflow

1. **Analyze Prompt**: Understand the user's natural language request for data.
2. **Identify Tables and Columns**: Determine the relevant tables and columns from the database schema.
3. **Construct Query**: Build the SQL query step-by-step, starting with simple `SELECT` statements and progressively adding `JOIN`, `WHERE`, `GROUP BY`, and `ORDER BY` clauses as needed.
4. **Validate and Refine**: Check the generated query for syntax errors and logical correctness. Refine the query based on validation results.
5. **Execute Query**: Run the validated SQL query against the database.
6. **Return Results**: Present the query results to the user in a clear and understandable format.

## Usage

This skill is used to translate natural language questions into SQL queries. It is particularly useful for data analysts, business intelligence professionals, and anyone who needs to interact with databases without writing SQL code manually.

## Example

**User Prompt**: "Show me the total sales for each product category in the last quarter."

**Generated SQL Query**:

```sql
SELECT
    pc.category_name,
    SUM(oi.quantity * oi.unit_price) AS total_sales
FROM
    order_items oi
JOIN
    products p ON oi.product_id = p.product_id
JOIN
    product_categories pc ON p.category_id = pc.category_id
JOIN
    orders o ON oi.order_id = o.order_id
WHERE
    o.order_date >= DATE('now', '-3 months')
GROUP BY
    pc.category_name
ORDER BY
    total_sales DESC;
```
