---
name: agent-creator
displayName: Agent Creator
description: Create and manage custom agents with specialized capabilities for automation, code review, documentation, testing, and more
keywords: [agents, custom agents, agent creator, code review, documentation, testing, automation, skills, hooks, steering]
version: 1.1.0
license: MIT
---

# Agent Creator Power

Create and manage custom AI agents, skills, hooks, and steering files in your Kiro workflow.

## What is Agent Creator?

This power helps you build custom agents, reusable skills, event-driven hooks, and persistent steering files in Kiro. Each component serves a distinct purpose in shaping how the agent behaves and automates your workflow.

## Features

- Create custom Kiro agents with proper structure and configuration
- Build reusable skills following the open Agent Skills specification
- Set up event-driven hooks that automate tasks on file changes and other IDE events
- Define steering files that give Kiro persistent project knowledge
- Configure agent tools, system prompts, and inclusion modes

## Key Concepts

### Agents
Custom sub-agents stored in `.kiro/agents/` with their own system prompts and tool access. Good for recurring, specialized tasks like code review or test generation.

### Skills
Modular instruction packages based on the [agentskills.io](https://agentskills.io) standard. Skills live in `.kiro/skills/` (workspace) or `~/.kiro/skills/` (global) and load on-demand when relevant, keeping your context lean.

### Hooks
Event-driven automations stored in `.kiro/hooks/` that trigger on file saves, creates, deletes, or manual activation. Hooks connect IDE events to AI-powered actions using natural language prompts.

### Steering
Persistent project knowledge via markdown files in `.kiro/steering/`. Steering files ensure Kiro consistently follows your patterns, libraries, and standards without repeating yourself every chat.

## Agent Naming

Every agent deserves a proper codename. When creating an agent, you'll be asked to pick a fun personality name. Here are some ideas to get you started:

| Codename | Inspired By | Good For |
|---|---|---|
| Jarvis | Iron Man | General-purpose assistant agents |
| Friday | Iron Man (successor) | Monitoring and alerting agents |
| Cortana | Halo | Navigation and search agents |
| Oracle | The Matrix / DC Comics | Code analysis and review agents |
| Scotty | Star Trek | Build, deploy, and infrastructure agents |
| Hal | 2001: A Space Odyssey | Testing and quality assurance agents |
| Samwise | Lord of the Rings | Documentation and support agents |
| Alfred | Batman | Cleanup, formatting, and maintenance agents |
| Athena | Greek mythology | Security and compliance agents |
| Merlin | Arthurian legend | Refactoring and transformation agents |

Pick one, remix it, or invent your own. The codename goes in `displayName` — the `name` field stays lowercase-with-hyphens for the file.

## Usage

```
"Create a custom agent for code review"
"Create a skill for requirements analysis"
"Set up a hook to run tests when I save TypeScript files"
"Create a steering file for our API conventions"
```

## Quick Start

### Create an Agent

```json
// .kiro/agents/code-reviewer.json
{
  "name": "code-reviewer",
  "displayName": "Oracle",
  "description": "Reviews code for quality, security, and best practices",
  "systemPrompt": "Analyze code for bugs, security issues, and style violations.",
  "tools": ["readCode", "getDiagnostics", "grepSearch"]
}
```

### Create a Skill

```
.kiro/skills/
└── requirements-analysis/
    └── SKILL.md
```

### Create a Hook

Use the Kiro panel → Agent Hooks → "+" button, or describe what you want in natural language.

### Create a Steering File

Navigate to the Steering section in the Kiro panel and click "+", or create a markdown file in `.kiro/steering/`.

## Best Practices

1. **Focused Purpose**: Each agent, skill, hook, or steering file should have a single, clear responsibility
2. **Minimal Tools**: Grant agents only the tools they need
3. **On-Demand Loading**: Use skills for specialized knowledge that shouldn't always consume context
4. **Specific Patterns**: Use precise file patterns in hooks to avoid unnecessary triggers
5. **Inclusion Modes**: Choose the right steering inclusion mode (always, fileMatch, manual) for each file

## Troubleshooting

**Agent not loading?**
- Check JSON syntax and verify it's in `.kiro/agents/`
- Ensure all required fields are present

**Skill not discovered?**
- Verify SKILL.md has valid YAML frontmatter with `name` and `description`
- Check the skill is in `.kiro/skills/<skill-name>/SKILL.md`

**Hook not triggering?**
- Verify file patterns match your target files
- Check the hook is enabled in the Agent Hooks panel

**Steering not applied?**
- Check inclusion mode in frontmatter
- For conditional includes, verify `fileMatchPattern` matches your files
- Ensure the file is in `.kiro/steering/`
