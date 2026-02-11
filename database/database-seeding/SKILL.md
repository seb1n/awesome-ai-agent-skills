---
name: database-seeding
description: "Seed a database with realistic test data for development and testing."
license: "MIT"
---

## Workflow

This skill facilitates the process of populating a database with initial data, which is crucial for development and testing environments. The workflow involves defining data schemas, generating mock data based on those schemas, and inserting the data into the specified database. This ensures that developers have a consistent and realistic dataset to work with, which helps in identifying potential issues early in the development cycle.

## Usage

To use this skill, you will need to provide the database connection details and the data schema. The skill will then generate and insert the data automatically. The following steps outline the usage process:

1.  **Configure Database Connection**: Provide the necessary credentials and endpoint for the database you want to seed.
2.  **Define Data Schema**: Specify the tables, columns, and data types for the data you want to generate. You can also define relationships between tables.
3.  **Run Seeding Process**: Execute the skill to start the data generation and insertion process.

## Example

Here is an example of how to use the `database-seeding` skill to populate a `users` table with 100 records:

```python
from database_seeding import Seeder

# 1. Configure database connection
db_connection = {
    "host": "localhost",
    "port": 5432,
    "user": "admin",
    "password": "password",
    "database": "test_db"
}

# 2. Define data schema
user_schema = {
    "table": "users",
    "count": 100,
    "columns": {
        "id": "uuid",
        "first_name": "first_name",
        "last_name": "last_name",
        "email": "email",
        "created_at": "timestamp"
    }
}

# 3. Run seeding process
seeder = Seeder(db_connection)
seeder.seed(user_schema)

print("Database seeding completed successfully.")
```
