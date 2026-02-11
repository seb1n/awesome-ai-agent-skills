---
name: api-integration
description: "Integrate with any API using OpenAPI specifications. This skill allows the agent to understand and interact with web services, expanding its capabilities to new platforms and data sources."
license: MIT
---

## Workflow

The `api-integration` skill enables the agent to dynamically learn and use new APIs. The workflow is as follows:

1.  **Discover**: The agent searches for an OpenAPI (or Swagger) specification file for the target API. This is typically a JSON or YAML file.
2.  **Learn**: The agent parses the specification to understand the available endpoints, parameters, authentication methods, and response structures.
3.  **Interact**: The agent can then make calls to the API, using the learned information to construct valid requests and handle responses.

## Usage

To use this skill, you need to provide the agent with the URL to the OpenAPI specification. The agent will then be able to use the API.

For example, if you want the agent to use the Pet Store API, you would provide it with the following URL:

```
https://petstore.swagger.io/v2/swagger.json
```

The agent will then be able to perform actions like "add a new pet" or "find pets by status".

## Example

Here's an example of how the agent might use this skill to interact with a hypothetical "weather" API:

**User:** "What's the weather like in London?"

**Agent:**
1.  The agent is instructed to use the `api-integration` skill with the weather API's OpenAPI specification at `https://example.com/weather-api.json`.
2.  The agent reads the specification and discovers an endpoint `/weather` that accepts a `city` parameter.
3.  The agent makes a GET request to `https://api.example.com/weather?city=London`.
4.  The API returns a JSON response: `{"temperature": "15°C", "conditions": "Cloudy"}`.
5.  The agent then provides the user with the answer: "The weather in London is 15°C and cloudy."
