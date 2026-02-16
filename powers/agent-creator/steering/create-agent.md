# Creating Custom Agents

This guide walks you through creating custom agents in Kiro.

## What Are Custom Agents?

Custom agents are specialized sub-agents with their own system prompts and tool access. They handle specific, recurring tasks autonomously — code review, documentation, testing, and more.

## Agent Structure

Agents are stored in `.kiro/agents/`:

```
.kiro/
└── agents/
    └── your-agent-name.json
```

## Step 1: Pick a Codename

Every agent needs a personality. Ask the user to choose a fun codename for their agent. Suggest options like:

- **Jarvis** — General-purpose assistant (Iron Man)
- **Friday** — Monitoring and alerting (Iron Man successor)
- **Oracle** — Code analysis and review (The Matrix / DC Comics)
- **Scotty** — Build and infrastructure ("I'm givin' her all she's got!")
- **Hal** — Testing and QA (2001: A Space Odyssey)
- **Samwise** — Documentation and support (Lord of the Rings)
- **Alfred** — Cleanup and maintenance (Batman)
- **Athena** — Security and compliance (Greek mythology)
- **Merlin** — Refactoring and transformation (Arthurian legend)
- **Cortana** — Search and navigation (Halo)

The codename goes in `displayName`. The `name` field stays lowercase-with-hyphens (e.g., `code-reviewer`). Users can pick from the list, remix, or invent their own.

## Step 2: Plan Your Agent

Define before creating:
- **Purpose**: What specific task will this agent handle?
- **Tools**: Which tools does it need? (keep it minimal)
- **Workflow**: What's the step-by-step process?

## Step 3: Create Agent Configuration

Create a JSON file in `.kiro/agents/`:

```json
{
  "name": "agent-name",
  "displayName": "Agent Name",
  "description": "Clear description of what this agent does",
  "systemPrompt": "Detailed instructions for the agent's behavior and approach",
  "tools": ["readCode", "readFile", "getDiagnostics"],
  "examples": [
    {
      "prompt": "Example task",
      "explanation": "What the agent should do"
    }
  ]
}
```

### Configuration Fields

- `name` — Lowercase with hyphens (e.g., `code-reviewer`)
- `displayName` — Human-readable (e.g., "Code Reviewer")
- `description` — What the agent does and when to use it
- `systemPrompt` — Detailed behavior instructions
- `tools` — Array of tools the agent can access (keep minimal)
- `examples` — Sample prompts to guide agent behavior

## Step 4: Test the Agent

- Validate JSON syntax
- Invoke with: `"Use the [agent-name] agent to [task]"`
- Start with simple tasks, then expand scope

## Agent Examples

**Code Reviewer (Oracle):**
```json
{
  "name": "code-reviewer",
  "displayName": "Oracle",
  "description": "Reviews code for quality, security, and best practices",
  "systemPrompt": "Analyze code for bugs, security issues, performance problems, and style violations. Provide constructive feedback with specific suggestions.",
  "tools": ["readCode", "getDiagnostics", "grepSearch"],
  "examples": [
    {
      "prompt": "Review this file for issues",
      "explanation": "Analyze code and provide actionable feedback"
    }
  ]
}
```

**Documentation Writer (Samwise):**
```json
{
  "name": "doc-writer",
  "displayName": "Samwise",
  "description": "Creates and updates technical documentation",
  "systemPrompt": "Create clear documentation with purpose, usage, code examples, and proper formatting.",
  "tools": ["readCode", "readFile", "fsWrite", "strReplace"]
}
```

**Test Generator (Hal):**
```json
{
  "name": "test-generator",
  "displayName": "Hal",
  "description": "Generates comprehensive test suites",
  "systemPrompt": "Generate tests covering happy paths, edge cases, and error handling. Use appropriate assertions and follow testing best practices.",
  "tools": ["readCode", "fsWrite", "executeBash", "getDiagnostics"]
}
```

## Tool Categories

- **Read**: `readCode`, `readFile`, `readMultipleFiles`, `grepSearch`
- **Write**: `fsWrite`, `fsAppend`, `strReplace`, `editCode`
- **Analysis**: `getDiagnostics`, `readCode`
- **Execution**: `executeBash`, `controlBashProcess`
- **Search**: `grepSearch`, `fileSearch`, `remote_web_search`

## Best Practices

- Each agent should have a focused, single responsibility
- Grant only the tools necessary for the agent's tasks
- Provide specific, detailed instructions in the system prompt
- Include examples to guide behavior
- Start narrow and expand scope as needed
- Test with edge cases and unexpected inputs

## Troubleshooting

**Agent not loading?**
- Check JSON syntax in the configuration file
- Verify the file is in `.kiro/agents/`
- Ensure all required fields are present

**Agent not behaving as expected?**
- Refine the system prompt with more specific instructions
- Add more examples
- Check if the agent has the necessary tools

**Agent too slow?**
- Reduce tool access to only what's needed
- Make the system prompt more focused
- Break complex tasks into smaller steps
