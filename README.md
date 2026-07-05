# Awesome AI Agent Skills

A community-shared collection of reusable skills for AI coding agents. Works with Claude Code, Cursor, Kilo Code, Windsurf, OpenAI Codex, and any AI tools that support skills or custom instructions.

- [Context Kit](https://github.com/JDDavenport/context-kit) — 4 PCA templates + 5 Claude Code skills for persistent personal context. MIT, one-command install.
## Source of Truth

- Author skills only under `skills/<skill-name>/`.
- Assign each skill to exactly one installable bundle in `plugin-groups.json`.
- Treat `.claude-plugin/marketplace.json`, `.agents/plugins/marketplace.json`, `plugins/**`, and generated README tables as sync outputs.
- Do not edit `plugins/<plugin-name>/skills/**` directly; those are Codex plugin package copies regenerated from `skills/`.
- Run `npm run sync` after changing skills or plugin grouping, then run `npm run validate`.

## What are Skills?

Skills are self-contained instruction sets that teach AI agents specific workflows, guidelines, or capabilities. Each skill includes:
- A `SKILL.md` with metadata and instructions
- Optional reference documentation for detailed guidance
- Reusable across any project

## Installation

### Claude Code

**Step 1: Add the marketplace**

```
/plugin marketplace add thienanblog/awesome-ai-agent-skills
```

**Step 2: Install skills**

```
# Install a plugin (can bundle multiple skills)
/plugin install project-development-skills@awesome-ai-agent-skills

# Install Laravel guidelines
/plugin install laravel-app-skills@awesome-ai-agent-skills

# Install Docker local development skill
/plugin install devops-skills@awesome-ai-agent-skills

# Install office web UI skill
/plugin install office-web-ui-skills@awesome-ai-agent-skills
```

**Updating the marketplace**

```
/plugin marketplace update
```

Claude Code marketplace entries use `source: "./"`, `strict: false`, and explicit `skills` arrays so this repository can curate multiple related skill folders into one installable plugin without copying them into a Claude-specific plugin package. See the official Claude Code docs for [plugin marketplaces](https://code.claude.com/docs/en/plugin-marketplaces) and [plugin structure](https://code.claude.com/docs/en/plugins).

### OpenAI Codex

Add this repository as a Codex marketplace:

```bash
codex plugin marketplace add thienanblog/awesome-ai-agent-skills
```

Then install the plugin you want:

```text
codex
/plugins
```

In the plugin browser:

1. Choose the **Awesome AI Agent Skills** marketplace.
2. Open one of these plugins:
   - `project-development-skills`
   - `laravel-app-skills`
   - `devops-skills`
   - `office-web-ui-skills`
3. Select **Install plugin**.
4. Start a new thread and ask Codex normally, or type `@` to choose the plugin or one of its bundled skills explicitly.

To refresh after this repository updates:

```bash
codex plugin marketplace upgrade awesome-ai-agent-skills
```

Codex also supports installing from a local checkout while developing this repository:

```bash
git clone https://github.com/thienanblog/awesome-ai-agent-skills.git
cd awesome-ai-agent-skills
codex plugin marketplace add .
```

This repository includes a Codex-compatible marketplace at `.agents/plugins/marketplace.json` and plugin packages under `plugins/`. The layout follows OpenAI's docs: marketplace entries point at `./plugins/<plugin-name>`, plugin manifests live in `.codex-plugin/plugin.json`, and bundled skills live inside the plugin root. See OpenAI's [Plugins](https://developers.openai.com/codex/plugins) and [Build plugins](https://developers.openai.com/codex/plugins/build) docs.

The repeated skill folders under `plugins/<plugin-name>/skills/` are generated Codex package copies. If they differ from `skills/<skill-name>/`, edit the canonical skill folder and rerun `npm run sync`.

### Skills CLI

The open `skills` CLI works with Codex, Claude Code, Cursor, and many other agents.

On macOS:

```bash
brew install skills
skills add thienanblog/awesome-ai-agent-skills --list
skills add thienanblog/awesome-ai-agent-skills --skill project-development-mindset
```

Without installing globally:

```bash
npx skills add thienanblog/awesome-ai-agent-skills --list
npx skills add thienanblog/awesome-ai-agent-skills --skill project-development-mindset
npx skills init my-skill
```

You can also copy individual skill instructions directly into your AI agent's context or system prompt.

## Available Skills

<!-- SKILLS_TABLE_START -->
| Skill | Description |
|-------|-------------|
| [agents-md-generator](./skills/agents-md-generator) | Generate or update AGENTS.md/CLAUDE.md files for AI coding agents through auto-scanning project files combined with interactive Q&A. Supports multiple tech stacks, development environments, source-of-truth rules, reuse-first implementation guidance, testing/debugging/performance quality gates, UI visual QA guidance, and preserves customizations when updating. |
| [debugging-workflow](./skills/debugging-workflow) | Reproduce, isolate, and fix software bugs without guessing. Use when the user reports errors, stack traces, crashes, regressions, logs, broken behavior with unknown cause, flaky behavior, incorrect business logic, UI bugs, integration failures, failing tests or CI failures with unclear root cause, or asks to debug, investigate, diagnose, or find the root cause of a problem. |
| [design-system-generator](./skills/design-system-generator) | Generate or update a project-specific DESIGN_SYSTEM.md that enforces consistent UI/UX across SPAs, traditional server-rendered sites, and hybrid systems. Use for design tokens, reusable component rules, UI source-of-truth conventions, animation/transition/custom class rules, accessibility gates, visual QA, Playwright screenshot guidance, and production asset/manifest requirements. |
| [docker-local-dev](./skills/docker-local-dev) | Generate Docker Compose and Dockerfile configurations for local development through interactive Q&A. Supports single-app and monorepo PHP/Laravel, WordPress, Drupal, Joomla, Node.js, and Python stacks with live reload, dependency installer jobs, Nginx/reverse proxy routing, databases, Redis, queues, schedulers, and email testing. Use when designing local dev stacks that differ from optimized production images. |
| [documentation-guidelines](./skills/documentation-guidelines) | Create, reorganize, or update documentation for monorepos or single-project repos using root docs indexes, unique repo/module/feature identifiers, repo-owned detailed docs, cross-repo relationship maps, machine-readable frontmatter, API contracts, workflows, runbooks, testing, and debugging guidance. |
| [laravel-11-12-app-guidelines](./skills/laravel-11-12-app-guidelines) | Guidelines and workflow for working on Laravel 11 or Laravel 12 applications across common stacks (API-only or full-stack), including optional Docker Compose/Sail, Inertia + React, Livewire, Vue, Blade, Tailwind v4, Fortify, Wayfinder, PHPUnit, Pint, and Laravel Boost MCP tools. Use when implementing features, fixing bugs, or making UI/backend changes while following project-specific instructions (AGENTS.md, docs/). |
| [office-web-ui-system](./skills/office-web-ui-system) | Design, verify, and refactor admin dashboard, internal dashboard, customer/user management dashboard, back-office console, and reporting UI. Use only for dashboard-style management systems with operational workflows such as metrics, stat cards, filters, data tables, CRUD/list/detail pages, forms, side panels, admin shells, Playwright/browser UI verification, screenshot-based dashboard fixes, or visual QA for operational interfaces. Do not use for general UI/UX design, marketing pages, landing pages, portfolios, product sites, games, or consumer app screens unless the task is specifically an admin or management dashboard. |
| [performance-optimization](./skills/performance-optimization) | Diagnose and improve performance with measurements and source-of-truth constraints. Use when the user reports slowness, latency, high CPU, high memory, slow queries, N+1 issues, large payloads, slow builds, slow tests, rendering lag, bundle size, Core Web Vitals, caching, pagination, image/font loading, queues, background jobs, or asks to profile, optimize, speed up, or reduce resource usage. |
| [project-development-mindset](./skills/project-development-mindset) | Universal project development workflow for safe, maintainable software changes. Use when creating or modifying code, documentation, UI/UX, tests, architecture, design systems, debugging workflows, performance work, deployment preparation, or multi-repository features. Enforces source-of-truth-first discovery, reuse before creating new code, cohesive file boundaries, project memory alignment, testing, and visual QA for UI tasks. |
| [testing-verification](./skills/testing-verification) | Plan, add, repair, and run tests and verification for software changes. Use when the user asks for tests, coverage, QA, acceptance criteria, regression checks, CI test failures, Playwright or browser verification, UI screenshot comparison, visual regression, or when a code change needs a focused test strategy across frontend, backend, API, or full-stack workflows. |
| [vps-docker-traefik-deploy](./skills/vps-docker-traefik-deploy) | Plan and implement secure production deployments of Docker Compose applications on self-hosted VPS or cloud servers using Docker Engine, Docker Compose, Traefik, private registries, SSH tunnels, least-privilege users, persistent volumes, backups, DNS, and storage growth planning. Use when an AI agent needs to design, review, document, or execute a real deploy for websites, APIs, websockets, workers, databases, and object storage integrations on Ubuntu or Debian style Linux hosts. |
<!-- SKILLS_TABLE_END -->

## Plugin Groups

Plugins bundle related skills so you can install by domain. The source of truth is `plugin-groups.json`.

<!-- PLUGINS_TABLE_START -->
| Plugin | Description | Skills |
|--------|-------------|--------|
| [project-development-skills](./plugin-groups.json) | A cohesive workflow bundle for project setup, source-of-truth development, testing, debugging, performance, documentation, design systems, and production deployment planning. | [project-development-mindset](./skills/project-development-mindset)<br>[testing-verification](./skills/testing-verification)<br>[debugging-workflow](./skills/debugging-workflow)<br>[performance-optimization](./skills/performance-optimization)<br>[agents-md-generator](./skills/agents-md-generator)<br>[documentation-guidelines](./skills/documentation-guidelines)<br>[design-system-generator](./skills/design-system-generator)<br>[vps-docker-traefik-deploy](./skills/vps-docker-traefik-deploy) |
| [laravel-app-skills](./plugin-groups.json) | Guidelines for building Laravel 11/12 apps across common stacks and tooling. | [laravel-11-12-app-guidelines](./skills/laravel-11-12-app-guidelines) |
| [devops-skills](./plugin-groups.json) | Skills for Docker-based local development environment configuration. | [docker-local-dev](./skills/docker-local-dev) |
| [office-web-ui-skills](./plugin-groups.json) | Skills for designing and refactoring admin, internal, and back-office web interfaces. | [office-web-ui-system](./skills/office-web-ui-system) |
<!-- PLUGINS_TABLE_END -->

## Repository Cleanup

This repository has been narrowed to a smaller, cohesive set of skills that are intended to work together. Apologies to contributors whose community skills were removed during this cleanup; the goal is to keep this repository focused on quality-controlled project development workflows instead of hosting unrelated skill experiments.

## Contributing

We welcome contributions! Here's a quick start:

1. Fork this repository
2. Create a skill folder: `skills/your-skill-name/`
3. Add a `SKILL.md` with metadata:
   ```yaml
   ---
   name: your-skill-name
   description: What the skill does and when to use it.
   ---
   ```
4. Add the skill to `plugin-groups.json` so it belongs to exactly one plugin.
5. **Sync and validate locally before pushing:**
   ```bash
   npm install
   npm run sync
   npm run validate
   ```
6. Submit a pull request

See **[CONTRIBUTING.md](./CONTRIBUTING.md)** for detailed guidelines, validation instructions, and troubleshooting.

## Validation Workflow

- `plugin-groups.json` is the source of truth for plugin membership.
- `npm run sync` regenerates `.claude-plugin/marketplace.json`, `.agents/plugins/marketplace.json`, `plugins/**`, and the generated tables in `README.md`.
- `npm run validate` checks skill metadata, plugin assignments, Claude marketplace consistency, and Codex plugin package consistency.
- Pull request CI reruns `npm run sync` and fails if generated files are out of date.

## For AI Agents

See [CLAUDE.md](./CLAUDE.md) for instructions on how to work with this repository, including how to group skills into plugins and update the marketplace when new skills are added.

## Compatibility

This skill format is designed to be universal and works with:
- Claude Code (Anthropic)
- OpenAI Codex
- Cursor
- Kilo Code
- GitHub Copilot
- Windsurf
- Any AI coding assistant that supports custom instructions or skills

## License

MIT