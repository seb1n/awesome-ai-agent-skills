---
name: OAuth 2.0 Setup
description: A guide to setting up OAuth 2.0 for API and service integrations.
license: MIT
---

## OAuth 2.0 Setup Skill

This skill provides a standardized workflow for setting up and managing OAuth 2.0 authentication within the agent environment. It is designed to simplify the process of integrating with external APIs and services that require OAuth 2.0, ensuring a secure and consistent authentication mechanism.

### Workflow

The OAuth 2.0 setup process is broken down into the following key steps:

1.  **Application Registration**: Before initiating the OAuth 2.0 flow, you must register your application with the service provider (e.g., Google, GitHub, Slack). This process typically involves creating a new application in the provider's developer console and specifying details such as the application name, website, and redirect URI.

2.  **Obtain Credentials**: Upon successful registration, the service provider will issue a unique **Client ID** and **Client Secret**. These credentials are used to identify your application and are essential for the OAuth 2.0 flow. They should be stored securely.

3.  **User Authorization**: The agent initiates the authorization process by redirecting the user to the service provider's authorization URL. This URL includes parameters such as the `client_id`, `redirect_uri`, `response_type`, and `scope`, which defines the permissions your application is requesting.

4.  **Authorization Code**: After the user grants permission, the service provider redirects the user back to the specified `redirect_uri` with an **authorization code** included in the URL parameters.

5.  **Token Exchange**: The agent exchanges the authorization code for an **access token** by making a POST request to the service provider's token endpoint. This request includes the `client_id`, `client_secret`, `authorization_code`, and `grant_type`.

6.  **Secure Token Storage**: The obtained access token (and optionally, a refresh token) must be stored securely. The agent should provide a mechanism for encrypted storage to protect these sensitive credentials.

7.  **Authenticated Requests**: With the access token, the agent can now make authenticated requests to the service provider's API on behalf of the user. The access token is typically included in the `Authorization` header of the API request.

8.  **Token Refresh**: Access tokens are often short-lived. If a refresh token was provided, the agent can use it to obtain a new access token without requiring the user to go through the authorization process again.

### Usage

This skill should be used whenever an integration with a third-party service requires OAuth 2.0 authentication. It provides a structured approach to guide the developer or agent through the setup process, ensuring that all necessary steps are completed correctly and securely. By following this skill, you can create a robust and reusable OAuth 2.0 implementation for your agent.

### Example

Here is an example of how this skill could be applied to integrate with the Google Calendar API:

1.  **Register Application**: Create a new project in the [Google API Console](https://console.developers.google.com/).
2.  **Enable API**: Enable the Google Calendar API for your project.
3.  **Create Credentials**: Create new OAuth 2.0 credentials, selecting "Web application" as the application type. Configure the authorized redirect URIs.
4.  **Get Credentials**: Note the **Client ID** and **Client Secret** provided by Google.
5.  **Authorization**: The agent constructs the authorization URL and directs the user to it.
6.  **Handle Callback**: The user is redirected back to your application with an authorization code.
7.  **Exchange Code**: The agent exchanges the code for an access token and a refresh token.
8.  **Store Tokens**: The tokens are stored securely.
9.  **API Calls**: The agent can now use the access token to make requests to the Google Calendar API, such as listing events or creating new ones.
