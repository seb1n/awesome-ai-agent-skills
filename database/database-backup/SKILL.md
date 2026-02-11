---
name: database-backup
description: "Backs up a database (e.g., PostgreSQL, MySQL, MongoDB) by creating a compressed backup file."
license: MIT
---

## Workflow

1.  **Identify Database Type**: The agent first determines the type of database to be backed up (e.g., PostgreSQL, MySQL, MongoDB) based on the user's request or by inspecting the environment.
2.  **Execute Backup Command**: The agent uses the appropriate command-line tool to create a backup of the specified database.
    *   For PostgreSQL: `pg_dump`
    *   For MySQL: `mysqldump`
    *   For MongoDB: `mongodump`
3.  **Compress Backup**: The resulting backup file is compressed to save space.
4.  **Store Backup**: The compressed backup file is saved to a specified location, or a default location if none is provided.

## Usage

To use this skill, instruct the agent to back up a database. You will need to provide the database name and type. You may also need to provide credentials if they are not already configured in the agent's environment.

## Example

**User Request:**

> "Please back up our 'production' PostgreSQL database."

**Agent Actions:**

1.  The agent identifies the database type as PostgreSQL and the database name as 'production'.
2.  The agent executes the `pg_dump` command to create a backup of the 'production' database.
3.  The backup file is compressed.
4.  The agent confirms that the backup has been created and provides the location of the backup file.
