# Creating Agent Skills

This guide covers creating reusable Agent Skills in Kiro following the open [agentskills.io](https://agentskills.io) standard.

## What Are Skills?

Skills are modular instruction packages that teach the agent new capabilities. They load on-demand — only consuming context when relevant — keeping your context window lean.

### Skills vs Steering vs Powers

- **Steering** — Always-on guidance (coding standards, project conventions)
- **Skills** — On-demand capabilities the agent learns when needed
- **Powers** — Superset that can also include MCP servers and rules

A Terraform skill won't consume context when you're writing React components. A security review skill stays dormant during routine refactoring.

## Skill Locations

- **Workspace**: `.kiro/skills/<skill-name>/SKILL.md` — project-specific
- **Global**: `~/.kiro/skills/<skill-name>/SKILL.md` — available across all workspaces

Workspace skills take precedence when names collide, so teams can override global defaults.

## Skill Discovery

At startup, Kiro only loads the `name` and `description` from each skill's frontmatter. The full instructions load into context only when the agent determines the skill is relevant or you explicitly request it.

## Skill Structure

```
skill-name/
├── SKILL.md           # Required: Main skill instructions
├── scripts/           # Optional: Executable scripts
├── references/        # Optional: Additional documentation
└── assets/            # Optional: Templates, images, data files
```

## Step 1: Create Skill Directory

```bash
mkdir -p .kiro/skills/skill-name
```

Use lowercase letters, numbers, and hyphens only.

## Step 2: Create SKILL.md

Every skill must have a `SKILL.md` with YAML frontmatter:

```markdown
---
name: skill-name
description: What this skill does and when to use it (max 1024 chars)
license: MIT
metadata:
  author: Your Name
  version: "1.0.0"
  tags: ["tag1", "tag2"]
---

# Skill Name

## Overview

Brief explanation of the skill's purpose.

## When to Use

Scenarios where this skill should be applied.

## Instructions

Step-by-step instructions for using this skill.

## Examples

Concrete examples demonstrating the skill in action.
```

### Required Frontmatter Fields

- `name` — Lowercase letters, numbers, hyphens only (max 64 chars)
- `description` — What the skill does and when to use it (max 1024 chars)

### Optional Frontmatter Fields

- `license` — License name or SPDX identifier
- `compatibility` — Environment requirements
- `metadata` — Additional key-value pairs (author, version, tags)

## Step 3: Add Optional Resources

**Scripts** (`scripts/`): Executable code supporting the skill's functionality.

**References** (`references/`): Detailed documentation when SKILL.md exceeds 500 lines. Link from SKILL.md:
```markdown
See [detailed guide](references/detailed-guide.md) for more information.
```

**Assets** (`assets/`): Templates, configuration files, images, or data files.

## Skill Example

```markdown
---
name: requirements-analysis
description: Gather and document functional and non-functional requirements for software projects
license: MIT
metadata:
  author: Team
  version: "1.0.0"
  tags: ["planning", "requirements", "documentation"]
---

# Requirements Analysis

## Overview

Systematically gather, organize, and document software requirements.

## When to Use

- Starting a new project or feature
- Clarifying project scope
- Creating technical specifications

## Instructions

1. Identify stakeholders and their needs
2. Gather functional requirements (user stories, use cases)
3. Gather non-functional requirements (performance, security, scalability)
4. Document with clear, testable language and acceptance criteria
5. Validate with stakeholders

## Examples

### User Story Format
As a [user type], I want to [action], so that [benefit].

### Acceptance Criteria
Given [context], when [action], then [expected result].
```

## Best Practices

- Keep skills single-purpose and reusable across agents
- Keep SKILL.md under 500 lines; use `references/` for lengthy content
- Include practical examples
- Version skills independently
- Test each skill with different agents
- Make skills portable — consider if other agents or projects could use them
