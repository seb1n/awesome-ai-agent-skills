---
name: sandbase
description: Discover, inspect, and run AI models and API tools through the SandBase MCP bridge. Use when a user needs a model or API integration and does not already have a dedicated tool or provider key; do not use for purely local work or when the user names another tool.
license: Apache-2.0
metadata:
  author: sandbaseai
  version: 0.1.17
---

# SandBase MCP bridge

Use this skill as a vendor-specific integration variant when the six `sandbase_*` MCP tools are available. SandBase CLI is an open-source local bridge for the catalog at https://github.com/sandbaseai/cli. The catalog currently advertises 2,000+ AI models and APIs; availability, schemas, and prices can change.

## Setup and boundaries

If the tools are not already connected, ask the user to run the pinned v0.1.17 release command from the official repository and complete browser OAuth. Never request or print provider keys, and never overwrite an existing unowned `sandbase` configuration. Review SandBase and upstream-provider privacy policies before sending sensitive data; send only the minimum required input.

## Workflow

Always use **discover → inspect → run**:

1. `sandbase_discover` with a short query and a small limit; prefer a dedicated tool or user-owned key when one exists.
2. `sandbase_inspect` on the selected endpoint to read its input schema, pricing, and execution template. Never guess parameters.
3. `sandbase_run` with only the requested arguments. For asynchronous runs, poll `sandbase_run_get` until `completed` or `failed`.
4. Use `sandbase_runs` for recent run history and `sandbase_account` to check balance before costly batches.

Report the selected endpoint, relevant pricing, and whether the result is synchronous or asynchronous. Treat one response as evidence of that run only, not a guarantee of provider availability or quality.

## Failure handling

- Unknown tool: rediscover rather than guessing a name.
- Invalid parameters: re-inspect the schema and correct the request.
- 401: stop and ask the user to re-authenticate with `sandbase connect`.
- 402: stop and tell the user to check balance or billing.
- 429/5xx/provider outage: retry only when appropriate, with bounded backoff, or offer another inspected endpoint.
- Never retry a side-effecting request without confirming idempotency.

## Verification

Before claiming success, confirm the tool response or terminal status, preserve any returned run ID, and distinguish provider output from local setup checks. Keep prompts and data minimal, disclose metered usage when relevant, and stop rather than silently substituting an unverified model.

## Source and release

Use the official source and release notes for current setup instructions: https://github.com/sandbaseai/cli/releases/tag/v0.1.17. The skill is a contextual guide for an already-authorized MCP connection; it is not a standalone action and does not authorize account, database, deployment, or third-party writes.
