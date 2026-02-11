# Contributing to Awesome AI Agent Skills

Thank you for your interest in contributing to this collection. We welcome new skills, improvements to existing ones, and bug fixes from the community.

## How to Add a New Skill

1. **Fork the repository** and clone it to your local machine.

2. **Choose the right category.** Browse the existing categories in the repository and select the one that best fits your skill. If no existing category fits, you may propose a new one.

3. **Create the skill directory.** Inside the appropriate category folder, create a new directory for your skill. The directory name must use `kebab-case` (lowercase letters, numbers, and hyphens only).

4. **Create the `SKILL.md` file.** Every skill must include a `SKILL.md` file with the following structure:

```yaml
---
name: your-skill-name
description: A clear description of what the skill does and when to use it.
license: MIT
---

# Your Skill Name

Detailed instructions, workflows, and examples for the agent.
```

5. **Add optional resources.** If your skill requires scripts, reference documentation, or templates, add them in the appropriate subdirectories (`scripts/`, `references/`, `assets/`).

6. **Submit a pull request.** Push your changes to your fork and open a pull request against the `main` branch.

## Skill Quality Guidelines

We prioritize quality over quantity. Please ensure your skill meets the following criteria:

- **Clear and actionable instructions.** The agent should be able to follow the instructions without ambiguity.
- **Practical examples.** Include at least one example of how the skill is used.
- **Proper YAML frontmatter.** The `name` and `description` fields are required.
- **Tested and validated.** If possible, test your skill with an AI agent before submitting.

## Code of Conduct

Be respectful and constructive in all interactions. We are building this together.
