# Creating a Chart AI Agent

This guide walks you through creating a new Chart AI agent from scratch.

## Step 1: Plan Your Agent

Before creating, define:
- **Purpose**: What specific task will this agent handle?
- **Skills**: What reusable skills does it need?
- **Workflow**: What's the step-by-step process?

## Step 2: Create Agent Directory

Create the agent folder with proper naming:

```bash
mkdir -p .kiro/agents/your-agent-name
```

Example:
```bash
mkdir -p .kiro/agents/code-reviewer
```

## Step 3: Create Agent Configuration

Create `agent.json` or `your-agent-name.json`:

```json
{
  "name": "agent-name",
  "displayName": "Agent Name",
  "description": "Clear description of what this agent does",
  "systemPrompt": "Detailed instructions for the agent's behavior and approach",
  "tools": ["readCode", "readFile", "fsWrite"],
  "examples": [
    {
      "prompt": "Example task",
      "explanation": "What the agent should do"
    }
  ]
}
```

## Step 4: Create Skills Directory

```bash
mkdir -p .kiro/agents/your-agent-name/skills
```

## Step 5: Add Skills

For each skill, create a directory and SKILL.md:

```bash
mkdir -p .kiro/agents/your-agent-name/skills/skill-name
```

Create `SKILL.md`:

```markdown
---
name: skill-name
description: What this skill does and when to use it (max 1024 chars)
license: MIT
metadata:
  author: Your Name
  version: "1.0.0"
---

# Skill Name

## Purpose

Clear explanation of what this skill does.

## When to Use

Describe scenarios where this skill should be applied.

## Instructions

Step-by-step instructions for using this skill.

## Examples

Provide concrete examples of the skill in action.
```

## Step 6: Reference Skills in Agent Config

If using Agent Skills specification, update the agent's configuration to reference skills.

## Step 7: Test the Agent

Validate the configuration:
- Check JSON syntax
- Verify skill references
- Test agent workflow end-to-end

## Example: Code Reviewer Agent

```json
{
  "name": "code-reviewer",
  "displayName": "Code Reviewer",
  "description": "Reviews code for quality, security, and best practices",
  "systemPrompt": "Analyze code thoroughly for bugs, security issues, performance problems, and style violations. Provide constructive feedback with specific suggestions.",
  "tools": ["readCode", "getDiagnostics", "grepSearch"],
  "examples": [
    {
      "prompt": "Review this file for issues",
      "explanation": "Analyze code and provide feedback"
    }
  ]
}
```

## Tips

- Start with 1-2 core skills, add more as needed
- Keep skills focused and reusable
- Test each skill independently
- Document workflows clearly
- Use semantic versioning for updates
