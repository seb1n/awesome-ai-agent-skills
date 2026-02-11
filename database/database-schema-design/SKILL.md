---
name: database-schema-design
description: Design a database schema for a new application, including defining tables, columns, and relationships.
license: MIT
---

# Database Schema Design

This skill enables the agent to design a database schema for a new application. The agent can define tables, columns, data types, and relationships to create a well-structured and efficient database.

## Workflow

1.  **Understand the application requirements:** The agent will work with the user to understand the data requirements of the application, including the entities, attributes, and relationships.
2.  **Create an entity-relationship diagram (ERD):** The agent will create an ERD to visually represent the database schema.
3.  **Define tables and columns:** The agent will define the tables and columns for the database, specifying the data types, constraints, and primary and foreign keys.
4.  **Normalize the database:** The agent will apply normalization techniques to reduce data redundancy and improve data integrity.
5.  **Generate SQL DDL scripts:** The agent will generate SQL Data Definition Language (DDL) scripts to create the database schema.

## Usage

To use this skill, provide the agent with a description of the application and its data requirements.

**Example:**

```
Design a database schema for a social media application.

- The application should support users, posts, comments, and likes.
- Users can follow other users.
- Posts can have multiple comments and likes.
```
