# Creating Custom Agents in Kiro

This guide will help you create custom agents to automate specialized tasks in your workflow.

## What are Custom Agents?

Custom agents are specialized sub-agents with their own system prompts and tool access. They can be invoked to handle specific, recurring tasks autonomously while you continue other work.

## When to Create a Custom Agent

Create a custom agent when you have:

- Recurring task patterns that need specialized behavior
- Domain-specific workflows (code review, documentation, testing)
- Tasks requiring isolated context and focused tool access
- Work that benefits from a consistent, specialized approach

## Creating an Agent

### Using Kiro's Agent Creator

The easiest way is to ask Kiro directly:

```
"Create a custom agent for [task description]"
```

Kiro will use the `custom-agent-creator` sub-agent to help you define:
- Agent name and purpose
- System prompt and behavior
- Available tools
- Usage patterns

### Manual Agent Configuration

Agents are configured in `.kiro/agents/` directory:

```
.kiro/
└── agents/
    └── your-agent-name.json
```

#### Agent Configuration Schema

```json
{
  "name": "your-agent-name",
  "displayName": "Your Agent Name",
  "description": "What this agent does",
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

## Agent Examples

### Code Review Agent

```json
{
  "name": "code-reviewer",
  "displayName": "Code Reviewer",
  "description": "Reviews code for best practices, bugs, and improvements",
  "systemPrompt": "You are a code review specialist. Analyze code for:\n- Potential bugs and edge cases\n- Performance issues\n- Security vulnerabilities\n- Code style and readability\n- Best practices\nProvide constructive feedback with specific suggestions.",
  "tools": ["readCode", "readFile", "grepSearch", "getDiagnostics"]
}
```

### Documentation Agent

```json
{
  "name": "doc-writer",
  "displayName": "Documentation Writer",
  "description": "Creates and updates technical documentation",
  "systemPrompt": "You are a technical documentation specialist. Create clear, comprehensive documentation that:\n- Explains purpose and usage\n- Includes code examples\n- Covers edge cases\n- Uses proper formatting\n- Maintains consistent style",
  "tools": ["readCode", "readFile", "fsWrite", "strReplace"]
}
```

### Test Generator Agent

```json
{
  "name": "test-generator",
  "displayName": "Test Generator",
  "description": "Generates comprehensive test suites",
  "systemPrompt": "You are a test automation specialist. Generate tests that:\n- Cover happy paths and edge cases\n- Test error handling\n- Use appropriate assertions\n- Follow testing best practices\n- Include setup and teardown",
  "tools": ["readCode", "fsWrite", "executeBash", "getDiagnostics"]
}
```

## Using Your Custom Agent

Once created, invoke your agent:

```
"Use the [agent-name] agent to [task]"
```

Or Kiro will automatically suggest appropriate agents based on your task.

## Best Practices

1. **Clear Purpose** - Each agent should have a focused, well-defined role
2. **Detailed Prompts** - Provide specific instructions and expectations
3. **Right Tools** - Grant only the tools needed for the agent's tasks
4. **Test Thoroughly** - Verify agent behavior with various inputs
5. **Iterate** - Refine the system prompt based on results

## Tool Categories

Common tool groups for agents:

- **Read**: `readCode`, `readFile`, `readMultipleFiles`, `grepSearch`
- **Write**: `fsWrite`, `fsAppend`, `strReplace`, `editCode`
- **Analysis**: `getDiagnostics`, `readCode`
- **Execution**: `executeBash`, `controlBashProcess`
- **Search**: `grepSearch`, `fileSearch`, `remote_web_search`

## Tips

- Start with a narrow scope and expand as needed
- Use examples to guide agent behavior
- Test with edge cases and unexpected inputs
- Document the agent's capabilities and limitations
- Share useful agents with your team

## Troubleshooting

**Agent not behaving as expected?**
- Review and refine the system prompt
- Check if the agent has the necessary tools
- Add more specific examples
- Test with simpler tasks first

**Agent too slow?**
- Reduce tool access to only what's needed
- Make the system prompt more focused
- Break complex tasks into smaller steps



## Need Help?

Ask Kiro: "Help me create a custom agent for [your use case]"
