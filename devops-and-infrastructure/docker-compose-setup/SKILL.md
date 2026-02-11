---
name: docker-compose-setup
description: "Sets up and runs services defined in a docker-compose.yml file."
license: "MIT"
---

## Workflow

This skill automates the process of setting up and running multi-container Docker applications using `docker-compose`. It checks for the presence of a `docker-compose.yml` file in the current directory, and if found, it runs `docker-compose up -d` to build, (re)create, start, and attach to containers for a service.

## Usage

To use this skill, simply ensure that a valid `docker-compose.yml` file is present in the root of your project directory. The skill will then handle the rest.

### Example

1.  **Create a `docker-compose.yml` file:**

    ```yaml
    version: '3.8'
    services:
      web:
        image: nginx:latest
        ports:
          - "8080:80"
      db:
        image: postgres:latest
        environment:
          POSTGRES_PASSWORD: password
    ```

2.  **Run the skill:**

    The agent will detect the `docker-compose.yml` file and execute the following command:

    ```bash
    docker-compose up -d
    ```

3.  **Result:**

    The `nginx` and `postgres` services will be running in the background. You can then access the `nginx` service at `http://localhost:8080`.
