# Creating a Reusable Skill

This guide shows you how to create skills that follow the Agent Skills specification.

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
mkdir -p .kiro/agents/your-agent/skills/skill-name
```

Use lowercase letters, numbers, and hyphens only.

## Step 2: Create SKILL.md

Every skill must have a `SKILL.md` file with YAML frontmatter:

```markdown
---
name: skill-name
description: A clear description of what this skill does and when to use it
license: MIT
metadata:
  author: Your Name
  version: "1.0.0"
  tags: ["tag1", "tag2"]
---

# Skill Name

## Overview

Brief overview of the skill's purpose.

## When to Use

Describe scenarios where this skill is applicable.

## Instructions

Detailed step-by-step instructions.

## Examples

Concrete examples demonstrating the skill.

## Best Practices

Tips for effective use of this skill.
```

## Required Fields

- `name`: Lowercase letters, numbers, hyphens only (max 64 chars)
- `description`: What the skill does and when to use it (max 1024 chars)

## Optional Fields

- `license`: License name or SPDX identifier
- `compatibility`: Environment requirements
- `metadata`: Additional key-value pairs
  - `author`: Skill creator
  - `version`: Semantic version
  - `tags`: Categorization tags
- `allowed-tools`: Pre-approved tools (experimental)

## Step 3: Add Optional Resources

### Scripts Directory

For executable code:

```bash
mkdir -p skill-name/scripts
```

Add scripts that support the skill's functionality.

### References Directory

For detailed documentation:

```bash
mkdir -p skill-name/references
```

Use when SKILL.md exceeds 500 lines. Link from SKILL.md:

```markdown
See [detailed guide](references/detailed-guide.md) for more information.
```

### Assets Directory

For templates and static resources:

```bash
mkdir -p skill-name/assets
```

Include templates, configuration files, images, or data files.

## Step 4: Keep It Focused

Good skills are:
- Single-purpose
- Reusable across agents
- Well-documented
- Under 500 lines in SKILL.md

## Step 5: Validate

Use the Agent Skills CLI:

```bash
skills-ref validate ./skill-name
```

## Example: Requirements Analysis Skill

```markdown
---
name: requirements-analysis
description: Gather and document functional and non-functional requirements for software projects
license: MIT
metadata:
  author: Your Name
  version: "1.0.0"
  tags: ["planning", "requirements", "documentation"]
---

# Requirements Analysis

## Overview

This skill helps gather, organize, and document software requirements systematically.

## When to Use

- Starting a new project
- Clarifying project scope
- Documenting stakeholder needs
- Creating technical specifications

## Instructions

1. **Identify Stakeholders**
   - List all project stakeholders
   - Understand their roles and needs

2. **Gather Functional Requirements**
   - What should the system do?
   - User stories and use cases
   - Feature lists

3. **Gather Non-Functional Requirements**
   - Performance expectations
   - Security requirements
   - Scalability needs
   - Compliance requirements

4. **Document Requirements**
   - Use clear, testable language
   - Prioritize requirements (must-have, should-have, nice-to-have)
   - Include acceptance criteria

5. **Validate Requirements**
   - Review with stakeholders
   - Check for completeness
   - Ensure feasibility

## Examples

### User Story Format
```
As a [user type]
I want to [action]
So that [benefit]
```

### Acceptance Criteria
```
Given [context]
When [action]
Then [expected result]
```

## Best Practices

- Be specific and measurable
- Avoid technical jargon with non-technical stakeholders
- Document assumptions and constraints
- Keep requirements traceable
- Update as project evolves
```

## Tips

- Make skills reusable - consider if other agents could use them
- Keep SKILL.md concise - use references/ for lengthy content
- Include practical examples
- Test skills with different agents
- Version skills independently from agents
