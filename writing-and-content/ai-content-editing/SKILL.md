---
name: AI Content Editing
description: Pre-publication quality gate for AI-generated or AI-assisted content. Strips AI writing patterns — sycophantic openers, stock vocabulary, hedging stacks, em-dash overuse — using the unslop CLI, then applies an editorial pass. Use before publishing READMEs, blog posts, release notes, PR descriptions, documentation, or social copy.
license: MIT
metadata:
  author: AI Agent Skills Community
  version: 1.0.0
---

# AI Content Editing

This skill enables the agent to catch and remove AI writing patterns before content goes public. It runs [unslop](https://github.com/MohamedAbdallah-14/unslop) on the draft to strip mechanical patterns automatically, then applies an editorial pass for anything that remains. Code blocks, URLs, file paths, and technical terms pass through unchanged.

## What Gets Removed

**Automatic (via unslop)**:
- Sycophantic openers: "Great question!", "Certainly!", "Absolutely!"
- Stock vocabulary: leverage, utilize, streamline, robust, seamlessly, cutting-edge, delve, empower, game-changing
- Hedging stacks: "it's worth noting that", "it's important to consider", "it should be noted"
- Filler transitions: "Furthermore,", "Moreover,", "In conclusion,", "Last but not least,"
- Em-dash overuse (multiple em-dashes per paragraph)

**What unslop preserves**:
- All code blocks (fenced and inline)
- URLs, file paths, and technical terms
- Library names, API names, framework names

## Workflow

1. **Receive the draft**: Accept content as a file path or inline text. Identify the content type (README, blog post, release notes, PR description, social copy, documentation).

2. **Run unslop**:
   - File mode: `unslop path/to/draft.md`
   - Pipe mode: `cat draft.md | unslop --stdin --deterministic`
   - Aggressive mode: `unslop --aggressive path/to/draft.md`

3. **Review unslop output**: Check for AI patterns that unslop may not catch — hollow openers, passive voice chains, over-structured lists, and content-type-specific issues.

4. **Apply editorial fixes**: Make targeted edits. Do not rewrite from scratch. The goal is removal and tightening, not replacement.

5. **Return the result**: Deliver the cleaned content with a brief summary of what was changed and why.

## Content Type Standards

| Type | First line rule | Common patterns to fix |
|------|-----------------|------------------------|
| README | State what the tool does, then how to install | "This library provides...", "This tool allows you to..." |
| Release notes | "Fixed X so Y no longer Z" | "Resolved an issue where", passive voice throughout |
| PR description | Change first, context second, testing last | Long preambles, missing test evidence |
| Blog post | First sentence is the thesis | "In this post, I will explore...", "Today we're going to look at..." |
| Social copy | Specific claim in first line | "Excited to share", "Thrilled to announce" |
| Documentation | Lead with the behavior, not the concept | "This section covers", "We will discuss" |

## Post-Unslop Editorial Checklist

- First sentence makes a specific, testable claim
- No passive voice chains longer than two sentences
- No hollow openers ("This document covers...", "This post explores...")
- Lists of 5+ items converted to prose where natural
- Reading level appropriate for the audience (technical content: Grade 10-12)
- All code and URLs preserved exactly

## Usage

Provide the draft content as a file path or paste it inline. Specify the content type if known. The agent runs unslop first, then applies the editorial checklist, and returns the cleaned version with a short summary of changes.

Install unslop: `npm install -g unslop`

## Examples

### Example 1: Cleaning a README

**Input**:
```
## Introduction

This library is a powerful and robust solution that leverages cutting-edge algorithms to seamlessly process data. It's worth noting that it also provides comprehensive support for multiple formats. Furthermore, it integrates with most popular frameworks.
```

**unslop output** (automatic removal):
```
## Introduction

This library processes data and supports multiple formats. It integrates with most popular frameworks.
```

**Editorial pass** (hollow opener → specific claim):
```
## Introduction

Processes CSV, JSON, and Parquet files in under 50ms on a single thread. Works with pandas, Polars, and DuckDB out of the box.
```

---

### Example 2: Release Notes

**Input**:
```
## v2.1.0

We're excited to share that this release includes several important improvements. Moreover, we've fixed a critical bug that was causing issues for certain users. Furthermore, performance has been enhanced.
```

**After unslop + editorial pass**:
```
## v2.1.0

Fixed a race condition in the connection pool that caused intermittent 503s under high load (#342). Reduced cold-start time by 40% by lazy-loading the schema validator.
```

---

### Example 3: PR Description

**Input**:
```
This PR addresses the issue where the authentication flow was not working correctly in certain edge cases. It's important to note that this change may affect users who are using custom auth providers.
```

**After unslop + editorial pass**:
```
Fixes token refresh for custom auth providers when the access token expires during an in-flight request (#289).

Custom auth provider users will need to re-authenticate once after deploying — refresh tokens issued before this change are not compatible with the new flow.

Tested against Auth0, Clerk, and a custom JWT provider. Added regression test in `auth.test.ts`.
```

## Best Practices

- **Run unslop first, edit second**: Let the tool handle the mechanical patterns. Manual editing time should go toward improving specificity and clarity, not stripping filler words.
- **Never rewrite the whole piece**: If content needs a complete rewrite, that is a drafting problem, not an editing problem. Flag it and return the original with notes.
- **Preserve technical precision**: Do not replace precise technical language with simpler words if the precision is necessary. "Race condition" is correct; "timing bug" may be imprecise for a technical audience.
- **Check code blocks are intact**: After any editing pass, verify that all fenced code blocks, inline code, and URLs are character-for-character identical to the input.
- **Match the audience register**: A README for a CLI tool used by engineers can be terse and technical. Documentation for a consumer product needs plainer language. Apply the checklist in context.

## Edge Cases

- **unslop not installed**: Run `npm install -g unslop` before calling. Verify with `unslop --version`.
- **Content is entirely code**: If the draft is mostly code with brief inline comments, skip unslop and only review the comment text manually.
- **Non-English content**: unslop targets English AI patterns. For non-English content, skip unslop and apply the editorial checklist manually, adapting the patterns to the target language's equivalent AI-writing tells.
- **Content has legitimate em-dashes**: If a draft uses em-dashes intentionally and correctly (one per paragraph maximum), `--aggressive` mode may over-remove them. Use standard mode instead.
- **Social copy under 280 characters**: For X/Twitter posts, run unslop in pipe mode, then check the character count. Tightening often brings overlong posts into limit without further cuts.
