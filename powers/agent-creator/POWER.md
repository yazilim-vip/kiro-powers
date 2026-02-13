---
name: agent-creator
displayName: Agent Creator
description: Create and manage custom agents with specialized capabilities for automation, code review, documentation, testing, and more
keywords: [agents, custom agents, agent creator, code review, documentation, testing, automation]
version: 1.0.0
license: MIT
---

# Agent Creator Power

Create and manage custom AI agents for specialized tasks in your Kiro workflow.

## Overview

This power helps you build, configure, and manage custom agents in Kiro. Each agent is specialized for specific tasks like code review, documentation generation, testing, and more.

## What You Can Do

- Create custom Kiro agents with proper structure
- Generate agent configurations with best practices
- Build specialized agents for code review, documentation, testing, and more
- Configure agent tools and system prompts
- Manage agent lifecycle and updates

## Agent Structure

Agents are stored in the `.kiro/agents/` directory:

```
.kiro/
└── agents/
    └── your-agent-name.json
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

### Use an Existing Agent

```
"Use the code-reviewer agent to review my changes"
```

### Update an Agent

```
"Update the code-reviewer agent to also check for security issues"
```

## Naming Conventions

- Agent files: `your-agent-name.json`
- Agent names: lowercase with hyphens (e.g., `code-reviewer`)
- Display names: Human-readable format (e.g., "Code Reviewer")

## Best Practices

1. **Focused Purpose**: Each agent should have a clear, specific role
2. **Clear Descriptions**: Explain what the agent does and when to use it
3. **Minimal Tools**: Grant only the tools necessary for the agent's tasks
4. **Detailed Prompts**: Provide specific instructions in the system prompt
5. **Test Thoroughly**: Verify agent behavior with various inputs
6. **Iterate**: Refine based on results and feedback

## Troubleshooting

**Agent not loading?**
- Check JSON syntax in agent configuration
- Verify agent is in `.kiro/agents/` directory
- Ensure all required fields are present

**Agent not behaving as expected?**
- Review and refine the system prompt
- Check if the agent has the necessary tools
- Add more specific examples
- Test with simpler tasks first

**Agent too slow?**
- Reduce tool access to only what's needed
- Make the system prompt more focused
- Break complex tasks into smaller steps
