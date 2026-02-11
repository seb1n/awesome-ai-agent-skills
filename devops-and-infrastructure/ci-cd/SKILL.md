---
name: ci-cd
description: Set up a continuous integration and continuous delivery (CI/CD) pipeline for a software project.
license: MIT
---

# CI/CD Pipeline Setup

This skill enables the agent to set up a CI/CD pipeline for a software project. The agent can configure automated builds, tests, and deployments to streamline the development process.

## Workflow

1.  **Choose a CI/CD platform:** The agent will help the user select a suitable CI/CD platform, such as GitHub Actions, GitLab CI/CD, or Jenkins.
2.  **Configure the build process:** The agent will define the steps required to build the application, including compiling code, running linters, and packaging the application.
3.  **Set up automated tests:** The agent will configure the pipeline to run automated tests, such as unit tests, integration tests, and end-to-end tests.
4.  **Configure deployments:** The agent will define the steps required to deploy the application to different environments, such as staging and production.
5.  **Monitor the pipeline:** The agent will set up monitoring and alerting to ensure that the CI/CD pipeline is running smoothly.

## Usage

To use this skill, provide the agent with information about your project, including the programming language, framework, and hosting environment.

**Example:**

```
Set up a CI/CD pipeline for a Node.js application hosted on AWS.

- The application is built with Express.js and uses MongoDB as the database.
- We want to run unit tests with Jest and end-to-end tests with Cypress.
- We want to deploy the application to a staging environment for testing and a production environment for release.
```
