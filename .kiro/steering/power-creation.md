---
inclusion: auto
fileMatchPattern: "powers/**/POWER.md"
---

# Kiro Power Creation Guidelines

When creating or modifying Kiro Powers, follow these strict formatting and structure guidelines.

## POWER.md Format

Every POWER.md file MUST start with YAML frontmatter and follow this structure:

### Required Frontmatter

```yaml
---
name: power-name
displayName: Power Display Name
description: Brief one-line description of what the power does
keywords: [keyword1, keyword2, keyword3, keyword4]
version: 1.0.0
license: MIT
---
```

### Frontmatter Fields

- `name`: Lowercase with hyphens (e.g., `react-mui-dev`, `git-committer`)
- `displayName`: Human-readable title (e.g., "React + Material-UI Development")
- `description`: Single sentence describing the power's purpose
- `keywords`: Array of relevant search terms (5-10 keywords)
- `version`: Semantic version (start with 1.0.0)
- `license`: MIT (standard for Kiro powers)

### Document Structure

After frontmatter, use this structure:

```markdown
# [Power Display Name]

Brief one-sentence tagline about what the power does.

## What is [Power Name]?

2-3 sentences explaining the power's purpose and what it helps users accomplish.

## Features

- Bullet list of key capabilities
- Focus on what users can do
- Keep it concise (5-8 items max)

## Usage

Show how users interact with the power:

```
"Example command or question"
"Another example"
```

Brief explanation of what happens when they use it.

## Quick Start

### Installation (if applicable)

```bash
npm install package-name
```

### Basic Setup

```language
// Minimal code example
```

## Common Patterns

### Pattern Name

```language
// Code example
```

Brief explanation.

### Another Pattern

```language
// Code example
```

## Best Practices

1. **Practice Name**: Brief explanation
2. **Another Practice**: Brief explanation
3. Keep to 5-7 key practices

## Troubleshooting

**Problem description?**
- Solution step 1
- Solution step 2

**Another problem?**
- Solution approach
```

## Style Guidelines

### Tone
- Direct and conversational
- Action-oriented language
- Avoid marketing fluff
- Be specific and practical

### Code Examples
- Keep examples minimal and focused
- Show real, working code
- Include comments only when necessary
- Use proper syntax highlighting

### Sections to Avoid
- Don't create "Overview" and "What This Power Does" separately (redundant)
- Don't list every possible feature exhaustively
- Don't include "Tips" and "Best Practices" as separate sections (combine)
- Avoid "Key Capabilities" if you have "Features"

### Length
- Keep POWER.md under 300 lines
- Each section should be scannable
- Use bullet points over paragraphs
- Code examples should be < 20 lines each

## File Structure

A complete power should have:

```
powers/
└── power-name/
    ├── POWER.md              # Main documentation (required)
    ├── mcp.json              # MCP server config (if applicable)
    └── .steering/            # Optional: Workflow guides
        ├── getting-started.md
        └── best-practices.md
```

## Steering Files

If your power includes steering files:
- Keep them focused on specific workflows
- Use descriptive names (getting-started.md, best-practices.md)
- Don't duplicate POWER.md content
- Provide deeper, actionable guidance

## Examples to Follow

Good examples in this repository:
- `powers/git-committer/POWER.md` - Clean structure, clear sections
- `powers/agent-creator/POWER.md` - Good use of examples

## Checklist

Before committing a new power, verify:

- [ ] YAML frontmatter is present and complete
- [ ] All required fields are filled
- [ ] `name` uses lowercase-with-hyphens format
- [ ] `keywords` array has 5-10 relevant terms
- [ ] Document starts with `# [Display Name]`
- [ ] "What is [Name]?" section explains purpose
- [ ] Features are listed as bullets
- [ ] Usage examples are provided
- [ ] Code examples use proper syntax highlighting
- [ ] No redundant sections
- [ ] Tone is direct and practical
- [ ] File is under 300 lines
- [ ] mcp.json is included if power uses MCP servers
