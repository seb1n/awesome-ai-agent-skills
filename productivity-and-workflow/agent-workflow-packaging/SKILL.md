---
name: agent-workflow-packaging
description: Convert repeated AI agent prompts, runbooks, and operating procedures into reusable SKILL.md packages with triggers, guardrails, examples, and validation checks.
license: MIT
metadata:
  author: MemoAsh
  version: 1.0.0
---

# Agent Workflow Packaging

This skill enables an AI agent to transform a recurring workflow into a reusable agent skill. It is useful when a team repeatedly pastes the same prompt, checklist, AGENTS.md section, release runbook, code review rubric, or troubleshooting procedure into coding-agent sessions. The agent extracts the repeated steps, writes a portable `SKILL.md`, adds realistic examples, and defines validation checks so future sessions can run the workflow consistently.

## Workflow

1. **Confirm the workflow is repeatable.** Determine whether the source material describes a recurring task rather than a one-off request. A good candidate has repeated inputs, repeated steps, repeated failure modes, and a clear definition of done. If the source is a single ad hoc request, produce a short checklist instead of a full skill.

2. **Collect the source material.** Ask for or inspect the prompt, runbook, AGENTS.md section, issue thread, PR review pattern, error triage notes, or manual checklist. Capture the task name, user persona, inputs, outputs, tools, approval requirements, and verification commands.

3. **Extract activation triggers.** Identify the words or situations that should activate the skill. Good triggers are specific: "review Stripe billing PRs", "prepare a release candidate", "triage failing GitHub Actions", or "package this runbook as a skill". Avoid vague triggers such as "help with code" or "improve workflow".

4. **Define boundaries and safety rules.** State what the skill should do, what it should not do, when the agent must ask for missing inputs, and which operations require approval. Public posting, production deployment, destructive file operations, purchases, and credential changes should be approval-gated.

5. **Write the SKILL.md package.** Create a directory named in kebab-case and add `SKILL.md` with YAML frontmatter, overview, workflow steps, usage notes, examples, and edge cases. Keep instructions action-oriented so another agent can follow them without guessing.

6. **Add realistic examples.** Include at least one concrete example with real-looking file names, commands, issue titles, PR names, or output snippets. Show the expected input, the agent's actions, and the final artifact.

7. **Validate the package.** Check that frontmatter is present, the description says what and when, the workflow has clear inputs and outputs, examples are realistic, approval gates are explicit, and the done condition can be verified.

## Usage

Provide the workflow source and the intended reuse target. The agent will extract the stable procedure and produce a reusable skill package.

```
Turn this repeated prompt into a SKILL.md:

Every time we review a billing PR, check Stripe webhook replay safety,
idempotency keys, authorization, invoice status transitions, and tests.
Use pnpm test -- billing before saying the review is complete.

Output:
- productivity-and-workflow/payment-pr-review/SKILL.md
- two realistic examples
- validation checklist
```

## Skill Package Structure

Use this structure for a portable skill:

```yaml
---
name: payment-pr-review
description: Review payment-related pull requests for webhook replay safety, idempotency, authorization, invoice state bugs, and test coverage.
license: MIT
metadata:
  author: your-name
  version: 1.0.0
---
```

Then include these sections:

- `# Skill Name`
- `## Workflow`
- `## Usage`
- `## Examples`
- `## Edge Cases`

## Examples

### Example 1: Package a payment PR review prompt

**User Request:**
> Turn our payment PR review prompt into a reusable skill. We always check Stripe webhooks, idempotency, authorization, invoice state changes, and tests.

**Agent Output:**

```
productivity-and-workflow/payment-pr-review/SKILL.md
```

The skill includes:

- Triggers: billing PR, Stripe webhook, checkout, subscription, invoice, payment review.
- Required inputs: PR diff, changed payment files, related tests, and existing auth middleware.
- Workflow: read PR intent, inspect changed files, trace money movement, check idempotency, inspect tests, write prioritized findings.
- Approval rule: do not merge, deploy, refund, charge, or modify production payment settings.
- Validation: confirm the billing test command was run or explain why it could not be run.

**Verification Checklist:**

```
[x] Frontmatter contains name, description, license, author, and version
[x] Description includes concrete activation triggers
[x] Workflow has clear inputs and outputs
[x] Examples use realistic payment files and commands
[x] Public or destructive actions are approval-gated
```

### Example 2: Package a release runbook

**User Request:**
> We paste the same release checklist every Friday: update changelog, bump version, run tests, build Docker image, tag, push, and draft release notes. Package it as a skill.

**Agent Output:**

```
productivity-and-workflow/release-runbook/SKILL.md
```

The skill tells the agent to:

1. Read existing release docs and package metadata.
2. Detect the package manager and test command from the repo.
3. Update changelog and version files.
4. Run tests and build checks.
5. Prepare tag and release notes.
6. Stop before pushing tags or publishing unless the user approves.

**Expected Done Condition:**

```
Release draft prepared:
- CHANGELOG.md updated
- version bumped from 2.3.4 to 2.3.5
- pnpm test passed
- docker build completed
- release notes draft created
- publishing requires user approval
```

## Edge Cases

- **Source material is too vague:** Ask for one real example of the workflow being performed before writing a skill.
- **Workflow is not repeatable:** Produce a task checklist instead of a reusable skill.
- **Multiple workflows are mixed together:** Split them into separate skills, such as `payment-pr-review` and `release-runbook`.
- **Host platform differs:** Use platform-neutral instructions where possible. Mention platform-specific paths only when required, such as `.claude/skills`, `.codex/skills`, or `.github/skills`.
- **Verification cannot run locally:** State which command or inspection was skipped and what evidence is missing.
- **Dangerous actions are requested:** Require explicit approval before production deploys, public posts, destructive file changes, financial transactions, or credential updates.
