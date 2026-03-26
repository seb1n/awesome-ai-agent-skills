# Awesome AI Agent Skills

**The Open-Source Library of AI Agent Skills.**

**Not a directory of links — a ready-to-use collection of 90+ complete, universal skills for any agent.**

[![Skills Count](https://img.shields.io/badge/Skills-90+-blue?style=flat-square)](https://github.com/seb1n/awesome-ai-agent-skills)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=flat-square)](./LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](./CONTRIBUTING.md)

---

## About This Library

While other collections link to external repositories, **Awesome AI Agent Skills** provides a self-contained, ready-to-use library of complete skills. Every skill in this repository is a full `SKILL.md` file with detailed instructions, workflows, and implementation guidance.

Our focus is on **universal, platform-agnostic skills** that make any AI agent better at general, real-world tasks like code review, security auditing, data analysis, technical writing, legal compliance, financial modeling, sales, and customer success. This is not a list of vendor-specific tools, but a foundational library for building capable, autonomous agents.

Each skill follows the open [SKILL.md standard](https://agentskills.io/specification), making them compatible with leading AI coding assistants and agent platforms, including Claude Code, OpenAI Codex, Gemini CLI, Cursor, GitHub Copilot, Windsurf, and more.

## Why a Library, Not a Directory?

-   **Ready to Use:** No need to hunt down external repos. Just clone and use.
-   **Standardized Quality:** Every skill follows the same high-quality, community-vetted format.
-   **Community Owned:** This is a library built *by* the community, *for* the community. All content is here, open to improvement by everyone.

## How to Use

Each skill is a self-contained directory with a `SKILL.md` file. To use a skill, copy its directory into the appropriate skills path for your AI agent platform:

| Platform | Project Path | Global Path |
|----------|-------------|-------------|
| Claude Code | `.claude/skills/` | `~/.claude/skills/` |
| OpenAI Codex | `.codex/skills/` | `~/.codex/skills/` |
| Gemini CLI | `.gemini/skills/` | `~/.gemini/skills/` |
| Cursor | `.cursor/skills/` | `~/.cursor/skills/` |
| GitHub Copilot | `.github/skills/` | `~/.copilot/skills/` |
| Windsurf | `.windsurf/skills/` | `~/.codeium/windsurf/skills/` |

## Skills Index

### AI/ML Operations

| Skill | Description |
|-------|-------------|
| [data-labeling](./ai-ml-operations/data-labeling) | Create labeled datasets for machine learning model training |
| [hyperparameter-tuning](./ai-ml-operations/hyperparameter-tuning) | Optimize model hyperparameters for better performance |
| [ml-pipeline-creation](./ai-ml-operations/ml-pipeline-creation) | Build end-to-end machine learning pipelines |
| [model-deployment](./ai-ml-operations/model-deployment) | Deploy trained models to production environments |
| [model-training](./ai-ml-operations/model-training) | Train machine learning models on given datasets |

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
| [license-analysis](./legal-and-compliance/license-analysis) | Analyze open-source license compatibility and obligations |
| [privacy-policy-drafting](./legal-and-compliance/privacy-policy-drafting) | Generate GDPR/CCPA-compliant privacy policies |
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
├── scripts/          # Optional: Executable scripts
├── references/       # Optional: Reference documentation
└── assets/           # Optional: Templates and resources
```

The `SKILL.md` file structure:

```yaml
---
name: skill-name
description: What the skill does and when to use it.
license: MIT
---

# Skill Name

Instructions, workflows, and examples for the agent.
```

## Related Skill Frameworks

| Framework | Description |
|-----------|-------------|
| [AuraKit](https://github.com/smorky850612/Aurakit) | All-in-one Claude Code skill: 33 modes, 6-layer security, 23 hooks, 8 languages, 75% token savings. Cross-platform (Codex, Cursor, Manus, Windsurf). Install: `npx @smorky85/aurakit` |

## Contributing

We welcome contributions from the community. Whether you want to add a new skill, improve an existing one, or fix a bug, please see our [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

## License

This project is licensed under the MIT License. See the [LICENSE](./LICENSE) file for details.
