# Awesome AI Agent Skills

[eye-art-polyphemus](./design-and-ui-ux/eye-art-polyphemus)

<!-- skill-count: 104 -->

**104 ready-to-use AI agent skills for Claude Code, OpenAI Codex, Gemini CLI, Cursor, GitHub Copilot, Windsurf, and other tools that support the open Agent Skills standard.**

Every skill is a complete, self-contained `SKILL.md` workflow for agent engineering, MCP, multi-agent systems, security, coding, research, data, DevOps, documents, marketing, sales, and more—not a link to another repository.

[![Skills Count](https://img.shields.io/badge/Skills-104-blue?style=flat-square)](https://github.com/seb1n/awesome-ai-agent-skills)
[![GitHub stars](https://img.shields.io/github/stars/seb1n/awesome-ai-agent-skills?style=flat-square&logo=github)](https://github.com/seb1n/awesome-ai-agent-skills/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](./LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](./CONTRIBUTING.md)
[![Validate Skills](https://github.com/seb1n/awesome-ai-agent-skills/actions/workflows/validate-skills.yml/badge.svg)](https://github.com/seb1n/awesome-ai-agent-skills/actions/workflows/validate-skills.yml)
[![Browse on skills.sh](https://img.shields.io/badge/Browse-skills.sh-black?style=flat-square)](https://skills.sh/seb1n/awesome-ai-agent-skills)

⭐ If this library saves you time, star the repository to bookmark it and help more agent builders discover it.

[Quick start](#quick-start-install-agent-skills) · [Production demo](#production-agent-stack-demo) · [Starter packs](#starter-packs) · [Browse 104 skills](#skills-index) · [Supported agents](#supported-agents) · [Contribute](#contributing)

## Quick Start: Install Agent Skills

Use the open-source [Skills CLI](https://github.com/vercel-labs/skills) to choose skills and install them for your detected agents:

```bash
npx skills add seb1n/awesome-ai-agent-skills
```

List all available skills without installing:

```bash
npx skills add seb1n/awesome-ai-agent-skills --list
```

Install one skill directly:

```bash
npx skills add seb1n/awesome-ai-agent-skills --skill agent-evaluation
```

Install several complementary skills by repeating `--skill`:

```bash
npx skills add seb1n/awesome-ai-agent-skills \
  --skill agent-evaluation \
  --skill agent-observability \
  --skill human-in-the-loop
```

### Starter Packs

| Pack | Recommended skills |
|------|--------------------|
| Production Agent Stack | [agent-evaluation](./agent-engineering/agent-evaluation), [agent-observability](./agent-engineering/agent-observability), [tool-schema-design](./agent-engineering/tool-schema-design), [human-in-the-loop](./agent-engineering/human-in-the-loop), [prompt-injection-defense](./agent-security/prompt-injection-defense), [agent-red-teaming](./agent-security/agent-red-teaming) |
| Multi-Agent Systems | [multi-agent-orchestration](./agent-engineering/multi-agent-orchestration), [mcp-server-building](./agent-engineering/mcp-server-building), [agent-evaluation](./agent-engineering/agent-evaluation) |
| Agent Security | [prompt-injection-defense](./agent-security/prompt-injection-defense), [agent-red-teaming](./agent-security/agent-red-teaming), [skill-supply-chain-audit](./agent-security/skill-supply-chain-audit) |
| Document Work | [pdf-processing](./documents-and-files/pdf-processing), [spreadsheet-analysis](./documents-and-files/spreadsheet-analysis), [presentation-creation](./communication/presentation-creation) |

### Production Agent Stack Demo

**Can a poisoned GitHub issue hijack a deployment agent?** Run the offline demo with deterministic outcomes to compare a fragile agent boundary with a controlled stack built from six complementary skills:

```bash
python3 demos/production-agent-stack/run_demo.py --check
```

The committed fixtures move from **1/5 to 5/5 checks passed**, with strict tool-schema, approval-policy, trust-boundary, trace-privacy, evaluation, and red-team evidence. The demo uses local mock effects only—no API keys, network requests, model calls, shell invocation, or real deployment.

[Explore the Production Agent Stack demo →](./demos/production-agent-stack/README.md)

## What Are Agent Skills?

Agent Skills are reusable instruction packages that teach an AI agent when and how to complete a task. Each skill follows the open [Agent Skills standard](https://agentskills.io/specification): a `SKILL.md` file with activation metadata and step-by-step guidance, plus optional scripts, references, and assets. Agents load a skill only when it is relevant, keeping context focused.

## Why This Library?

Unlike collections that send you to external repositories, **Awesome AI Agent Skills** keeps every workflow in one inspectable, installable library.

- **Ready to use:** Install a single skill, a starter pack, or choose from the complete catalog.
- **Cross-agent compatible:** Use the same skills with Claude Code, OpenAI Codex, Gemini CLI, Cursor, GitHub Copilot, Windsurf, and other compatible tools.
- **Validated structure:** CI checks names, activation descriptions, links, duplicates, catalog synchronization, skill count, and bundled Python syntax.
- **Progressive disclosure:** Deeper skills bundle focused scripts, references, and assets without loading everything into context.
- **Broad real-world coverage:** Build agents for engineering, security, data, research, documents, compliance, finance, marketing, sales, and customer success.
- **Open source:** The library is MIT licensed and open to review, adaptation, and contribution.

## Supported Agents

The Skills CLI detects supported agents automatically. For manual installation, copy a skill directory into the appropriate project or global path:

| Platform | Project Path | Global Path |
|----------|-------------|-------------|
| Claude Code | `.claude/skills/` | `~/.claude/skills/` |
| OpenAI Codex | `.agents/skills/` | `~/.agents/skills/` |
| Gemini CLI | `.gemini/skills/` | `~/.gemini/skills/` |
| Cursor | `.cursor/skills/` | `~/.cursor/skills/` |
| GitHub Copilot | `.github/skills/` | `~/.copilot/skills/` |
| Windsurf | `.windsurf/skills/` | `~/.codeium/windsurf/skills/` |

## Skills Index

Browse all 104 skills by category, or use the full searchable index below.

| Agent Building | Technical | Business & Knowledge |
|----------------|-----------|----------------------|
| [Agent Engineering](./agent-engineering/) | [Code & Development](./code-and-development/) | [Communication](./communication/) |
| [Agent Security](./agent-security/) | [Data & Analytics](./data-and-analytics/) | [Customer Success](./customer-success/) |
| [Context Engineering](./context-engineering/) | [Database](./database/) | [Finance & Accounting](./finance-and-accounting/) |
| [AI/ML Operations](./ai-ml-operations/) | [DevOps & Infrastructure](./devops-and-infrastructure/) | [Legal & Compliance](./legal-and-compliance/) |
| [API & Integration](./api-and-integration/) | [Documents & Files](./documents-and-files/) | [Marketing & SEO](./marketing-and-seo/) |
| [Security](./security/) | [Design & UI/UX](./design-and-ui-ux/) | [Sales](./sales/) |
| [Productivity & Workflow](./productivity-and-workflow/) | [Research & Knowledge](./research-and-knowledge/) | [Writing & Content](./writing-and-content/) |

### AI/ML Operations

| Skill | Description |
|-------|-------------|
| [data-labeling](./ai-ml-operations/data-labeling) | Create labeled datasets for machine learning model training |
| [hyperparameter-tuning](./ai-ml-operations/hyperparameter-tuning) | Optimize model hyperparameters for better performance |
| [ml-pipeline-creation](./ai-ml-operations/ml-pipeline-creation) | Build end-to-end machine learning pipelines |
| [model-deployment](./ai-ml-operations/model-deployment) | Deploy trained models to production environments |
| [model-training](./ai-ml-operations/model-training) | Train machine learning models on given datasets |

### Agent Engineering

| Skill | Description |
|-------|-------------|
| [agent-evaluation](./agent-engineering/agent-evaluation) | Design reproducible evaluations, graders, baselines, and release gates for AI agents |
| [agent-observability](./agent-engineering/agent-observability) | Instrument agent traces, metrics, cost attribution, dashboards, and investigations |
| [human-in-the-loop](./agent-engineering/human-in-the-loop) | Design auditable approval gates, escalation paths, and safe state transitions |
| [mcp-server-building](./agent-engineering/mcp-server-building) | Build and verify secure, interoperable Model Context Protocol servers |
| [multi-agent-orchestration](./agent-engineering/multi-agent-orchestration) | Coordinate bounded multi-agent workflows, handoffs, shared state, and recovery |
| [tool-schema-design](./agent-engineering/tool-schema-design) | Design precise model-facing tool schemas with explicit side effects and safe defaults |

### Agent Security

| Skill | Description |
|-------|-------------|
| [agent-red-teaming](./agent-security/agent-red-teaming) | Plan authorized adversarial tests for agent behavior, tools, memory, and controls |
| [prompt-injection-defense](./agent-security/prompt-injection-defense) | Defend agent workflows against direct and indirect prompt injection |
| [skill-supply-chain-audit](./agent-security/skill-supply-chain-audit) | Audit skill bundles for malicious instructions, unsafe scripts, provenance, and excessive permissions |

### API & Integration

| Skill | Description |
|-------|-------------|
| [api-design](./api-and-integration/api-design) | Design RESTful APIs with resources, endpoints, and data models |
| [api-integration](./api-and-integration/api-integration) | Integrate third-party APIs into applications |
| [graphql-api-design](./api-and-integration/graphql-api-design) | Design GraphQL schemas, queries, and mutations |
| [oauth-2-0-setup](./api-and-integration/oauth-2-0-setup) | Implement OAuth 2.0 authentication flows |
| [webhook-setup](./api-and-integration/webhook-setup) | Configure webhooks for event-driven integrations |

### Code & Development

| Skill | Description |
|-------|-------------|
| [code-documentation](./code-and-development/code-documentation) | Generate comprehensive code documentation |
| [code-review](./code-and-development/code-review) | Review code for bugs, style violations, and performance issues |
| [debugging](./code-and-development/debugging) | Identify and fix errors with root cause analysis |
| [refactoring](./code-and-development/refactoring) | Improve code quality and maintainability |
| [testing](./code-and-development/testing) | Write and run unit, integration, and end-to-end tests |
| [version-control](./code-and-development/version-control) | Manage Git workflows, branching, and merging |

### Communication

| Skill | Description |
|-------|-------------|
| [chatbot-conversation-design](./communication/chatbot-conversation-design) | Design conversational flows for chatbots |
| [email-drafting](./communication/email-drafting) | Draft professional emails for various purposes |
| [meeting-transcription](./communication/meeting-transcription) | Transcribe and summarize meeting recordings |
| [presentation-creation](./communication/presentation-creation) | Create slide decks and presentations |
| [report-generation](./communication/report-generation) | Generate structured business and technical reports |

### Customer Success

| Skill | Description |
|-------|-------------|
| [churn-analysis](./customer-success/churn-analysis) | Identify at-risk accounts and churn indicators |
| [customer-feedback-analysis](./customer-success/customer-feedback-analysis) | Analyze NPS, CSAT, and qualitative feedback for themes |
| [knowledge-base-article-writing](./customer-success/knowledge-base-article-writing) | Write help center articles and FAQ entries |
| [onboarding-playbook-creation](./customer-success/onboarding-playbook-creation) | Design customer onboarding workflows and checklists |
| [ticket-triage](./customer-success/ticket-triage) | Classify, prioritize, and route support tickets |

### Context Engineering

| Skill | Description |
|-------|-------------|
| [context-compression](./context-engineering/context-compression) | Compress context to reduce token usage |
| [context-injection](./context-engineering/context-injection) | Inject relevant context into agent prompts |
| [context-optimization](./context-engineering/context-optimization) | Optimize context for improved agent performance |
| [context-ranking](./context-engineering/context-ranking) | Rank and prioritize context by relevance |
| [context-retrieval](./context-engineering/context-retrieval) | Retrieve relevant context from knowledge bases |

### Data & Analytics

| Skill | Description |
|-------|-------------|
| [data-analysis](./data-and-analytics/data-analysis) | Analyze datasets to extract insights and identify trends |
| [data-cleaning](./data-and-analytics/data-cleaning) | Clean and preprocess raw data for analysis |
| [data-visualization](./data-and-analytics/data-visualization) | Create charts, graphs, and interactive visualizations |
| [exploratory-data-analysis](./data-and-analytics/exploratory-data-analysis) | Perform initial data exploration and profiling |
| [sql-query-generation](./data-and-analytics/sql-query-generation) | Generate optimized SQL queries from natural language |

### Database

| Skill | Description |
|-------|-------------|
| [database-backup](./database/database-backup) | Create and manage database backups |
| [database-migration](./database/database-migration) | Plan and execute database schema migrations |
| [database-schema-design](./database/database-schema-design) | Design normalized database schemas |
| [database-seeding](./database/database-seeding) | Populate databases with test or initial data |
| [query-optimization](./database/query-optimization) | Optimize slow database queries |

### Design & UI/UX

| Skill | Description |
|-------|-------------|
| [accessibility-testing](./design-and-ui-ux/accessibility-testing) | Test interfaces for WCAG compliance |
| [frontend-design](./design-and-ui-ux/frontend-design) | Design and build frontend interfaces |
| [logo-design](./design-and-ui-ux/logo-design) | Create logo concepts and brand identity |
| [user-flow-mapping](./design-and-ui-ux/user-flow-mapping) | Map user journeys and interaction flows |
| [wireframing](./design-and-ui-ux/wireframing) | Create wireframes and low-fidelity mockups |

### Documents & Files

| Skill | Description |
|-------|-------------|
| [pdf-processing](./documents-and-files/pdf-processing) | Extract, transform, create, and visually verify PDF documents safely |
| [spreadsheet-analysis](./documents-and-files/spreadsheet-analysis) | Analyze and modify spreadsheets while preserving formulas, structure, and auditability |

### Finance & Accounting

| Skill | Description |
|-------|-------------|
| [budget-planning](./finance-and-accounting/budget-planning) | Create and manage budgets with variance analysis |
| [expense-categorization](./finance-and-accounting/expense-categorization) | Classify expenses by category, department, and tax deductibility |
| [financial-modeling](./finance-and-accounting/financial-modeling) | Build financial projections, P&L, and DCF models |
| [financial-report-generation](./finance-and-accounting/financial-report-generation) | Generate balance sheets, cash flow statements, and financial summaries |
| [invoice-processing](./finance-and-accounting/invoice-processing) | Extract, validate, and categorize invoice data |

### DevOps & Infrastructure

| Skill | Description |
|-------|-------------|
| [ci-cd](./devops-and-infrastructure/ci-cd) | Set up CI/CD pipelines for automated builds and deployments |
| [cloud-monitoring](./devops-and-infrastructure/cloud-monitoring) | Configure cloud monitoring and alerting |
| [docker-compose-setup](./devops-and-infrastructure/docker-compose-setup) | Create Docker Compose configurations for multi-service apps |
| [infrastructure-as-code](./devops-and-infrastructure/infrastructure-as-code) | Define infrastructure using Terraform, Pulumi, or CloudFormation |
| [kubernetes-deployment](./devops-and-infrastructure/kubernetes-deployment) | Deploy and manage applications on Kubernetes |

### Legal & Compliance

| Skill | Description |
|-------|-------------|
| [compliance-checklist-generation](./legal-and-compliance/compliance-checklist-generation) | Create compliance checklists for SOC2, HIPAA, PCI-DSS, and GDPR |
| [contract-review](./legal-and-compliance/contract-review) | Analyze contracts for risks, obligations, and key clauses |
| [eu-ai-act-readiness](./legal-and-compliance/eu-ai-act-readiness) | Assess EU AI Act readiness with dated evidence, gaps, owners, and counsel review |
| [license-analysis](./legal-and-compliance/license-analysis) | Analyze open-source license compatibility and obligations |
| [privacy-policy-drafting](./legal-and-compliance/privacy-policy-drafting) | Draft privacy-policy language and a jurisdiction-aware review checklist |
| [terms-of-service-generation](./legal-and-compliance/terms-of-service-generation) | Draft Terms of Service documents for web apps and SaaS |

### Marketing & SEO

| Skill | Description |
|-------|-------------|
| [analytics-reporting](./marketing-and-seo/analytics-reporting) | Generate marketing analytics reports |
| [content-strategy](./marketing-and-seo/content-strategy) | Develop content marketing strategies |
| [keyword-research](./marketing-and-seo/keyword-research) | Research and analyze keywords for SEO |
| [seo-optimization](./marketing-and-seo/seo-optimization) | Optimize webpages for search engine visibility |
| [social-media-posting](./marketing-and-seo/social-media-posting) | Create and schedule social media content |

### Productivity & Workflow

| Skill | Description |
|-------|-------------|
| [file-organization](./productivity-and-workflow/file-organization) | Organize and structure files and directories |
| [meeting-scheduler](./productivity-and-workflow/meeting-scheduler) | Schedule meetings across calendars and time zones |
| [note-taking](./productivity-and-workflow/note-taking) | Take structured notes from meetings and documents |
| [project-management](./productivity-and-workflow/project-management) | Manage tasks, milestones, and team coordination |
| [task-automation](./productivity-and-workflow/task-automation) | Automate repetitive tasks and workflows |

### Research & Knowledge

| Skill | Description |
|-------|-------------|
| [deep-research](./research-and-knowledge/deep-research) | Conduct comprehensive multi-source research |
| [fact-checking](./research-and-knowledge/fact-checking) | Verify claims against authoritative sources |
| [knowledge-graph-creation](./research-and-knowledge/knowledge-graph-creation) | Build knowledge graphs from unstructured data |
| [literature-review](./research-and-knowledge/literature-review) | Review and synthesize academic literature |
| [summarization](./research-and-knowledge/summarization) | Summarize long documents and articles |

### Sales

| Skill | Description |
|-------|-------------|
| [competitive-battlecard-creation](./sales/competitive-battlecard-creation) | Build sales battlecards for competitive positioning |
| [crm-data-enrichment](./sales/crm-data-enrichment) | Enrich CRM records with firmographic and contact data |
| [lead-scoring](./sales/lead-scoring) | Score and prioritize leads based on fit and engagement signals |
| [proposal-generation](./sales/proposal-generation) | Create tailored sales proposals and RFP responses |
| [sales-email-sequences](./sales/sales-email-sequences) | Design multi-touch outbound email sequences |

### Security

| Skill | Description |
|-------|-------------|
| [dependency-scanning](./security/dependency-scanning) | Scan dependencies for known vulnerabilities |
| [dynamic-application-security-testing](./security/dynamic-application-security-testing) | Test running applications for security flaws |
| [security-audit](./security/security-audit) | Perform comprehensive security audits |
| [static-application-security-testing](./security/static-application-security-testing) | Analyze source code for security vulnerabilities |
| [threat-modeling](./security/threat-modeling) | Identify and prioritize security threats |

### Writing & Content

| Skill | Description |
|-------|-------------|
| [blog-post-writing](./writing-and-content/blog-post-writing) | Write engaging blog posts and articles |
| [copywriting](./writing-and-content/copywriting) | Write persuasive marketing and advertising copy |
| [proofreading](./writing-and-content/proofreading) | Proofread and edit text for grammar and clarity |
| [technical-writing](./writing-and-content/technical-writing) | Write technical documentation and user guides |
| [translation](./writing-and-content/translation) | Translate text between languages |

## Skill Format

Each skill follows the [Agent Skills open standard](https://agentskills.io/specification). A skill is a directory containing a `SKILL.md` file with YAML frontmatter and Markdown instructions:

```
skill-name/
├── SKILL.md          # Required: Instructions and metadata
├── agents/           # Optional: Product-specific UI metadata
├── scripts/          # Optional: Executable scripts
├── references/       # Optional: Reference documentation
└── assets/           # Optional: Templates and resources
```

The `SKILL.md` file structure:

```yaml
---
name: skill-name
description: What the skill does. Use when the user provides these inputs or requests this workflow.
---

# Skill Name

Instructions, workflows, and examples for the agent.
```

## Quality and Validation

Run the zero-dependency catalog validator locally:

```bash
python3 scripts/validate_skills.py
```

The same validation runs in CI. New and materially revised skills must also test one normal prompt, one edge or failure prompt, and every executable script. See [CONTRIBUTING.md](./CONTRIBUTING.md) for the complete quality and safety checklist.

## Contributing

We welcome contributions from the community. Whether you want to add a new skill, improve an existing one, or fix a bug, please see our [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

## License

This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for details.
