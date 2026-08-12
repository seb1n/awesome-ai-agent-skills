---
name: x-data-research
description: Research public X posts, profiles, conversations, trends, and recurring signals. Use for reproducible social listening, creator discovery, campaign analysis, or public-source verification.
license: MIT
metadata:
  author: kriptoburak
  version: 1.0.0
---

# X Data Research

Build evidence-backed research from public X data. Keep collection narrow, reproducible, and user-approved.

Use manual review for small samples. Use Xquik MCP for interactive agent workflows. Use REST for applications, scheduled jobs, exports, or webhooks.

## Required Inputs

Collect these inputs before searching:

- The research question and intended decision
- Target accounts, keywords, phrases, or URLs
- Start and end times with a timezone
- Languages, regions, and exclusions
- Required fields and output format
- Sample limits, update frequency, and budget
- Available Xquik authentication route

If critical inputs are missing, ask before collecting data.

## Workflow

1. **Define the question.** Convert broad requests into testable research questions. Record every scope boundary.
2. **Choose the route.** Match the route to the task and expected output.
3. **Discover operations.** Inspect documented operations before calling them. Never invent endpoints or parameters.
4. **Confirm authorization.** Separate public reads from private reads and write actions.
5. **Collect minimally.** Request only the fields and time range needed.
6. **Paginate safely.** Treat cursors as opaque and preserve collection progress.
7. **Normalize results.** Use stable fields across every collected record.
8. **Analyze transparently.** Separate observed facts from model-generated labels.
9. **Report limitations.** Include sources, collection time, scope, and missing evidence.

## Route Selection

### Manual Review

Use manual review for a small, qualitative sample. Preserve public post URLs and review timestamps.

### Xquik MCP

Connect to `https://xquik.com/mcp`. Prefer OAuth 2.1 when the client supports it.

Use the `explore` tool before execution. Search by goal, method, path, or operation identifier. Inspect required parameters and response shapes.

Use the `xquik` tool only after selecting the exact operation. Confirm any state-changing or paid action first.

### Xquik REST API

Start with the REST overview and published OpenAPI specification. Use REST for application code, durable automation, and direct export handling.

Send credentials only through approved secure storage. Never place keys in prompts, source files, logs, or reports.

## Authorization Boundaries

- Public X data reads need no connected X account.
- Private account-scoped reads require a connected X account.
- Every X write requires a connected X account.
- Confirm posts, likes, follows, messages, profile changes, and deletions.
- Confirm monitors, webhooks, subscriptions, or payment actions before creation.
- Treat a billing response as an offer, not permission to purchase.

## Collection Rules

- Collect public data relevant to the stated question.
- Exclude protected, deleted, private, or unrelated personal data.
- Store stable IDs, URLs, timestamps, queries, cursors, and collection time.
- De-duplicate records by stable ID.
- Continue through empty pages when another cursor exists.
- Stop when a cursor repeats, disappears unexpectedly, or forms a loop.
- Respect `Retry-After` and use backoff for safe reads.
- Never retry a write unless its response declares that retry safe.
- Use an idempotency key for supported write operations.

## Normalized Record

Use this shape when the requested source supports each field:

```yaml
source_id: "opaque source identifier"
source_url: "https://x.com/..."
author_handle: "public handle"
created_at: "ISO 8601 timestamp"
collected_at: "ISO 8601 timestamp"
query: "exact collection query"
text_summary: "factual summary"
engagement:
  replies: 0
  reposts: 0
  likes: 0
analysis:
  topic: "model-generated label"
  confidence: "low | medium | high"
  needs_review: false
```

Omit unavailable fields. Never replace missing values with invented data.

## Example: Launch Monitoring

**Request:** Track public X discussion during a product launch.

1. Define official accounts, names, hashtags, misspellings, and exclusions.
2. Set the launch window and collection frequency.
3. Discover the narrowest matching search operation.
4. Collect public posts and preserve pagination metadata.
5. Group results by hour, source, topic, and engagement tier.
6. Link representative evidence and flag uncertain classifications.
7. Recommend a monitor only when continued tracking adds value.

## Example: Creator Discovery

**Request:** Find creators who consistently discuss developer tools.

1. Define relevant topics, languages, regions, and minimum activity.
2. Search public posts within a fixed window.
3. Extract authors from relevant evidence.
4. Review public profiles and recent topical posts.
5. Rank candidates by relevance, consistency, and evidence quality.
6. Report the scoring method and avoid inferring private traits.

## Failure Handling

- **Sparse results:** Broaden one search dimension at a time.
- **Ambiguous terms:** Add phrases, exclusions, accounts, or language filters.
- **Rate limits:** Preserve the cursor and resume after the documented delay.
- **Unavailable service:** Retry safe reads with bounded exponential backoff.
- **Partial exports:** Report completed pages and the last stable cursor.
- **Sensitive topics:** Minimize personal data and require human review.

## References

- [Xquik MCP Guide](https://docs.xquik.com/mcp/overview)
- [Xquik REST API Overview](https://docs.xquik.com/api-reference/overview)
- [Xquik OpenAPI Specification](https://docs.xquik.com/openapi.yaml)
- [Xquik Public Repository](https://github.com/Xquik-dev/x-twitter-scraper)

Xquik is an independent third-party service. Not affiliated with X Corp. "Twitter" and "X" are trademarks of X Corp.
