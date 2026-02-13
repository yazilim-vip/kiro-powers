# Agent Skills Power

Create and manage custom AI agents with reusable skills following the [Agent Skills specification](https://agentskills.io/).

## Overview

This power helps you build, configure, and manage custom agents in Kiro. Each agent is specialized for specific tasks and leverages modular, reusable skills that follow industry standards.

## What You Can Do

- Create custom Kiro agents with proper structure
- Add reusable skills to agents following Agent Skills specification
- Generate agent configurations with best practices
- Organize skills into modular, reusable components
- Build agents for code review, documentation, testing, and more

## Agent Architecture

### Agent Structure

```
.kiro/
└── agents/
    └── your-agent-name.json
```

Or with embedded skills:

```
.kiro/
└── agents/
    └── your-agent/
        ├── agent.json
        └── skills/
            ├── skill-name/
            │   ├── SKILL.md
            │   ├── scripts/
            │   ├── references/
            │   └── assets/
            └── another-skill/
                └── SKILL.md
```

### Agent Configuration Format

```json
{
  "name": "agent-name",
  "displayName": "Agent Name",
  "description": "What the agent does",
  "systemPrompt": "Detailed instructions for the agent's behavior and approach",
  "tools": ["tool1", "tool2"],
  "examples": [
    {
      "prompt": "Example task",
      "explanation": "What the agent should do"
    }
  ]
}
```

### Skill Format (SKILL.md)

```markdown
---
name: skill-name
description: What this skill does and when to use it
license: MIT
metadata:
  author: Chart AI Team
  version: "1.0.0"
---

# Skill Name

Detailed skill instructions and content...
```

## Example Agents

### Code Review Agent

Analyzes code for quality, security, and best practices.

**Tools:**
- `readCode`: Read and analyze code structure
- `getDiagnostics`: Check for errors and warnings
- `grepSearch`: Search for patterns

**Workflow:** Read code → Analyze → Provide feedback

### Documentation Agent

Creates and maintains technical documentation.

**Tools:**
- `readCode`: Understand code structure
- `fsWrite`: Create documentation files
- `strReplace`: Update existing docs

**Workflow:** Analyze code → Generate docs → Add examples

### Test Generator Agent

Generates comprehensive test suites.

**Tools:**
- `readCode`: Understand code to test
- `fsWrite`: Create test files
- `executeBash`: Run tests

**Workflow:** Analyze code → Generate tests → Verify

## Usage Examples

### Create a New Agent

```
"Create a custom agent called 'code-reviewer' that analyzes code quality"
```

### Add a Skill to an Agent

```
"Add a 'security-audit' skill to my code-reviewer agent"
```

### Generate Agent with Skills

```
"Create a documentation agent with API documentation and example generation skills"
```

## Naming Conventions

- Agent files: `your-agent-name.json` or `your-agent/agent.json`
- Agent names: lowercase with hyphens (e.g., `code-reviewer`)
- Skill directories: lowercase with hyphens (e.g., `requirements-analysis`)
- Skill names in YAML: lowercase letters, numbers, hyphens only (max 64 chars)

## Skill Requirements

**Required Fields:**
- `name`: Skill identifier (lowercase, hyphens, max 64 chars)
- `description`: What the skill does (max 1024 chars)

**Optional Fields:**
- `license`: License name or reference
- `compatibility`: Environment requirements
- `metadata`: Additional key-value pairs (author, version, etc.)
- `allowed-tools`: Pre-approved tools (experimental)

**Optional Directories:**
- `scripts/`: Executable scripts
- `references/`: Additional documentation
- `assets/`: Templates, images, data files

## Best Practices

1. **Focused Skills**: Keep skills single-purpose and reusable
2. **Clear Descriptions**: Explain what the skill does and when to use it
3. **Proper Versioning**: Follow semantic versioning (MAJOR.MINOR.PATCH)
4. **Skill Size**: Keep SKILL.md under 500 lines (use references/ for detailed docs)
5. **Validation**: Test agent configurations before deployment
6. **Tool Access**: Grant only necessary tools to agents

## Standards

This power follows:
- [Agent Skills](https://agentskills.io/) specification
- [AGENTS.md](https://agents.md/) convention
- JSON for structured configuration
- Markdown with YAML frontmatter for skills

## Validation

Validate your skills using the Agent Skills CLI:

```bash
skills-ref validate ./skill-name
```

## Troubleshooting

**Agent not loading?**
- Check JSON syntax in agent config
- Verify skill references match actual skill directories
- Ensure SKILL.md has valid YAML frontmatter

**Skill not working?**
- Validate required fields (name, description)
- Check name format (lowercase, hyphens only)
- Verify description length (max 1024 chars)

**Global agent not accessible?**
- Check agent is in `.kiro/agents/` directory
- Verify agent configuration file exists
- Ensure JSON syntax is valid

## Resources

- [Agent Skills Specification](https://agentskills.io/specification)
- [AGENTS.md Convention](https://agents.md/)
