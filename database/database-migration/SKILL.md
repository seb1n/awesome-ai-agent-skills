---
name: database-migration
description: A skill for migrating databases from one system to another, ensuring data integrity and minimal downtime.
license: MIT
---

## Workflow

1. **Analyze Source and Target Databases**: The agent first connects to both the source and target database systems to analyze their schemas, data types, and any existing constraints or triggers.
2. **Generate Migration Script**: Based on the analysis, the agent generates a migration script (e.g., SQL, Python) that maps data from the source to the target schema. This script handles data transformations and resolves any compatibility issues.
3. **Execute Migration**: The agent executes the migration script in a controlled environment. It provides real-time progress updates and logs any errors or warnings.
4. **Verify Data Integrity**: After the migration, the agent performs a verification step to ensure that all data has been transferred correctly and that data integrity is maintained. This may involve checksums, row counts, and other validation techniques.
5. **Report and Cleanup**: Finally, the agent generates a detailed report of the migration process, including any issues encountered and their resolution. It also cleans up any temporary files or connections.

## Usage

To use this skill, you need to provide the connection details for both the source and target databases. The agent will then guide you through the migration process.

```python
# Example of how to invoke the skill

default_api.run_skill(
    'database-migration',
    source_db={
        'type': 'postgresql',
        'host': 'source.db.example.com',
        'port': 5432,
        'user': 'admin',
        'password': 'password',
        'database': 'sourcedb'
    },
    target_db={
        'type': 'mysql',
        'host': 'target.db.example.com',
        'port': 3306,
        'user': 'admin',
        'password': 'password',
        'database': 'targetdb'
    }
)
```

## Example

A user wants to migrate their user data from a PostgreSQL database to a MySQL database. They provide the connection details for both databases. The agent analyzes the schemas, generates a Python script using the `psycopg2` and `mysql-connector-python` libraries to transfer the data, executes the script, verifies the data, and provides a report.
