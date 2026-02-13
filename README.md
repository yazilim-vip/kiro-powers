# Kiro Powers Collection

A curated collection of Kiro Powers to enhance your development workflow.

## What are Kiro Powers?

Kiro Powers are packages that extend Kiro's capabilities by bundling documentation, workflow guides (steering files), and optionally MCP (Model Context Protocol) servers. They provide structured, on-demand access to specialized tools and knowledge domains.

## Available Powers

| Power | Description | Keywords |
|-------|-------------|----------|
| [agent-skills](powers/agent-skills/) | Create and manage custom agents with reusable skills following the Agent Skills specification | agents, skills, custom agents, code review, documentation, testing, automation |

## Installation

### Install from GitHub (Recommended)

Install individual powers directly from this repository:

```
# In Kiro, ask:
"Install the agent-skills power from https://github.com/YOUR_USERNAME/YOUR_REPO/tree/main/powers/agent-skills"
```

Or use the Kiro Powers UI:
1. Open Command Palette → "Configure Powers"
2. Click "Install from URL"
3. Enter: `https://github.com/YOUR_USERNAME/YOUR_REPO/tree/main/powers/agent-skills`

### Install All Powers

Clone this repository to install all powers at once:

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git

# Copy powers to your Kiro directory
cp -r YOUR_REPO/powers/* ~/.kiro/powers/
```

### Manual Installation

1. Download or clone this repository
2. Copy individual power directories to:
   - User-level: `~/.kiro/powers/`
   - Workspace-level: `.kiro/powers/`

## Usage

After installing a power, activate it in Kiro:

```
# Activate by mentioning keywords
"I need help with custom agents"

# Or activate explicitly
"Activate the agent-skills power"

# Or use the # context menu
Type # and select the power
```

Powers load their documentation and tools on-demand, keeping your context focused.

## Power Structure

Each power in this repository follows this structure:

```
powers/
└── power-name/
    ├── power.json          # Required: Power metadata
    ├── POWER.md           # Required: Documentation
    ├── steering/          # Optional: Workflow guides
    │   └── guide.md
    └── mcpServers/        # Optional: MCP server configs
        └── server-name/
            └── config.json
```

## Contributing

Want to add a new power? See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on:
- Power structure and requirements
- Documentation standards
- Testing and validation
- Submission process

## Resources

- [Kiro Powers Documentation](https://kiro.dev/docs/powers/)
- [Creating Powers Guide](https://kiro.dev/docs/powers/create/)
- [Agent Skills Specification](https://agentskills.io/)
- [AGENTS.md Convention](https://agents.md/)

## License

MIT - See individual power directories for specific licenses
