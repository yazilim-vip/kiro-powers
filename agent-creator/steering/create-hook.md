# Creating Agent Hooks

This guide covers creating event-driven hooks in Kiro that automate tasks when specific IDE events occur.

## What Are Hooks?

Hooks are automated triggers that execute predefined agent actions when events occur in your IDE — file saves, creates, deletes, or manual activation. They eliminate manual requests for routine tasks and ensure consistency.

## How Hooks Work

1. **Event Detection** — The system monitors for specific IDE events
2. **Prompt Execution** — A predefined prompt is sent to the agent
3. **Automated Action** — The agent processes the prompt and acts

## Hook Triggers

- **On File Save** (`fileEdited`) — Run linting, update docs, run tests for changed files
- **On File Create** (`fileCreated`) — Generate boilerplate, add license headers, create test files
- **On File Delete** (`fileDeleted`) — Clean up references, update imports
- **Manual Trigger** (`userTriggered`) — On-demand code reviews, security scans, audits
- **On Prompt Submit** (`promptSubmit`) — Run commands when a message is sent to the agent
- **On Agent Stop** (`agentStop`) — Run commands when agent execution completes
- **Pre Tool Use** (`preToolUse`) — Intercept before a tool executes (access control, validation)
- **Post Tool Use** (`postToolUse`) — React after a tool executes (review, logging)

## Hook Configuration

Hooks are stored as JSON files in `.kiro/hooks/` with this schema:

```json
{
  "name": "Hook Name",
  "version": "1.0.0",
  "description": "What this hook does",
  "when": {
    "type": "fileEdited",
    "patterns": ["*.ts", "*.tsx"]
  },
  "then": {
    "type": "askAgent",
    "prompt": "Instructions for what the agent should do"
  }
}
```

## Schema Fields

### `when` (trigger)

- `type` — One of: `fileEdited`, `fileCreated`, `fileDeleted`, `userTriggered`, `promptSubmit`, `agentStop`, `preToolUse`, `postToolUse`
- `patterns` — Array of glob patterns (required for file events)
- `toolTypes` — Array of tool categories or regex patterns (required for `preToolUse`/`postToolUse`). Valid categories: `read`, `write`, `shell`, `web`, `spec`, `*`. Use regex like `.*sql.*` to match MCP tool names.

### `then` (action)

- `type` — `askAgent` or `runCommand`
- `prompt` — Required for `askAgent`
- `command` — Required for `runCommand`

### Valid Combinations

| Action | Compatible Triggers |
|---|---|
| `askAgent` | `fileEdited`, `fileCreated`, `fileDeleted`, `userTriggered`, `promptSubmit`, `agentStop`, `preToolUse`, `postToolUse` |
| `runCommand` | `promptSubmit`, `agentStop`, `preToolUse`, `postToolUse` (NOT file events) |

## Creating Hooks

### Via Kiro Panel

1. Click the Kiro icon → Agent Hooks
2. Click "+" and type a natural language description
3. Review and adjust title, description, event type, file patterns, and prompt
4. Save — the hook appears in the panel and as a config file in `.kiro/hooks/`

### Via Command Palette

`Cmd + Shift + P` → "Kiro: Open Kiro Hook UI"

## Hook Examples

**Test Sync on Save:**
```json
{
  "name": "Test Sync",
  "version": "1.0.0",
  "when": {
    "type": "fileEdited",
    "patterns": ["src/**/*.ts"]
  },
  "then": {
    "type": "askAgent",
    "prompt": "Review the changes and update corresponding test files to maintain coverage."
  }
}
```

**Security Scanner:**
```json
{
  "name": "Security Scan",
  "version": "1.0.0",
  "when": {
    "type": "fileEdited",
    "patterns": ["**/*"]
  },
  "then": {
    "type": "askAgent",
    "prompt": "Scan this file for API keys, hardcoded credentials, SQL injection, and XSS vulnerabilities. Suggest fixes for any issues found."
  }
}
```

**Write Operation Review (preToolUse):**
```json
{
  "name": "Review Writes",
  "version": "1.0.0",
  "when": {
    "type": "preToolUse",
    "toolTypes": ["write"]
  },
  "then": {
    "type": "askAgent",
    "prompt": "Verify this write operation follows our coding standards."
  }
}
```

**Lint on Save (runCommand):**
```json
{
  "name": "Lint on Save",
  "version": "1.0.0",
  "when": {
    "type": "fileEdited",
    "patterns": ["*.ts", "*.tsx"]
  },
  "then": {
    "type": "askAgent",
    "prompt": "Run `npm run lint` and fix any errors in the edited file"
  }
}
```

**Manual Code Audit:**
```json
{
  "name": "Code Quality Audit",
  "version": "1.0.0",
  "when": {
    "type": "userTriggered"
  },
  "then": {
    "type": "askAgent",
    "prompt": "Perform a comprehensive code quality analysis: check for code smells, complexity, duplication, naming conventions, and error handling patterns."
  }
}
```

## Managing Hooks

- **Enable/Disable**: Click the eye icon next to any hook, or use the toggle in the hook view
- **Edit**: Select a hook and modify triggers, patterns, or instructions. Updates apply immediately.
- **Delete**: Select the hook → Delete Hook at the bottom (cannot be undone)
- **Run Manual Hooks**: Click the play button (▷) next to the hook name

## Best Practices

- **Be specific** — Clear, unambiguous instructions focused on one task per hook
- **Use precise patterns** — Target specific file types/directories to avoid unnecessary triggers
- **Test first** — Try hooks on sample files before enabling project-wide
- **Monitor performance** — Hooks consume AI interactions; design them to be efficient
- **Version control** — Commit hooks in `.kiro/hooks/` so the whole team benefits
- **Start simple** — Begin with basic hooks and add complexity as needed

## Troubleshooting

**Hook not triggering?**
- Verify file patterns match your target files
- Check the hook is enabled in the Agent Hooks panel
- Ensure the trigger event type is correct

**Slow execution?**
- Make instructions more specific and focused
- Use narrower file patterns
- Consider manual triggers for expensive operations

**Inconsistent results?**
- Add more context about project structure in the prompt
- Refine conditions and patterns
- Check hook execution logs in the Agent Hooks panel
