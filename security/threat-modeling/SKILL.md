---
name: threat-modeling
description: "Conducts automated threat modeling for software applications and systems to identify and prioritize potential security vulnerabilities."
license: "MIT"
---

## Workflow

The threat-modeling skill automates the process of identifying and assessing security threats in software applications and infrastructure. It follows a structured workflow:

1.  **System Analysis**: The agent gathers information about the system's architecture, data flows, and components by analyzing provided documentation, code repositories, and infrastructure-as-code (IaC) files.
2.  **Threat Identification**: Using established threat modeling methodologies like STRIDE (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege), the skill identifies potential threats applicable to the system.
3.  **Vulnerability Analysis**: For each identified threat, the skill analyzes the system's design and implementation to find potential vulnerabilities that could be exploited.
4.  **Risk Assessment**: The skill prioritizes the identified vulnerabilities based on their potential impact and likelihood of exploitation, providing a ranked list of risks.
5.  **Mitigation Suggestions**: For high-priority risks, the skill suggests specific mitigation strategies and security controls that can be implemented to reduce or eliminate the threats.

## Usage

To use the threat-modeling skill, provide it with access to the application's source code, design documents, and any relevant architectural diagrams. You can instruct the agent to perform a threat modeling assessment with a prompt like:

> "Analyze our new e-commerce platform for security threats. The source code is in the `/src` directory, and the architecture diagram is at `docs/architecture.png`."

The agent will then execute the threat modeling workflow and provide a detailed report of its findings.

## Example

### Input

-   **Prompt**: "Perform a threat model on our user authentication service. The code is in `/auth-service`."
-   **`/auth-service/main.go`**: (Go source code for the authentication service)
-   **`/auth-service/Dockerfile`**: (Dockerfile for the service)

### Output

The agent would produce a Markdown report containing:

-   **Threat Model Summary**: An overview of the threat modeling process and key findings.
-   **Identified Threats (STRIDE)**:
    -   **Spoofing**: Potential for attackers to impersonate legitimate users.
    -   **Tampering**: Risk of unauthorized modification of user session data.
    -   **Information Disclosure**: Possibility of leaking sensitive user data.
-   **Vulnerability Details**:
    -   **VULN-001 (High)**: Insecure password storage (plaintext passwords).
    -   **VULN-002 (Medium)**: Lack of rate limiting on login attempts.
-   **Recommended Mitigations**:
    -   **For VULN-001**: "Implement strong password hashing using an algorithm like bcrypt or Argon2."
    -   **For VULN-002**: "Introduce rate limiting and account lockout mechanisms to prevent brute-force attacks."
