# Kiro Powers Collection

A curated collection of Kiro Powers to enhance your development workflow.

## What are Kiro Powers?

Kiro Powers are packages that extend Kiro's capabilities by bundling documentation, workflow guides (steering files), and optionally MCP (Model Context Protocol) servers. They provide structured, on-demand access to specialized tools and knowledge domains.

## Available Powers

Browse the `powers/` directory to see all available powers. Each power includes:

- **POWER.md** - Complete documentation and usage guide
- **power.json** - Power configuration and metadata
- **Steering files** (optional) - Workflow guides for specific tasks
- **MCP servers** (optional) - Backend tools and integrations

## Installation

### Using Kiro UI

1. Open the Command Palette in Kiro
2. Search for "Configure Powers" or use the Powers panel
3. Browse and install powers from this repository

### Manual Installation

1. Clone this repository or download a specific power
2. Copy the power directory to your Kiro powers location:
   - User-level: `~/.kiro/powers/`
   - Workspace-level: `.kiro/powers/`

## Usage

After installing a power, activate it in Kiro:

```
Ask Kiro to activate the power by name, or use the # context menu
```

Powers load their documentation and tools on-demand, keeping your context focused.

## Contributing

Want to add a new power? See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Each power should follow this structure:

```
powers/
└── your-power-name/
    ├── power.json          # Required: Power metadata
    ├── POWER.md           # Required: Documentation
    ├── steering/          # Optional: Workflow guides
    │   └── guide.md
    └── mcp/              # Optional: MCP server configs
        └── server.json
```

## Example Powers

This repository includes:

- **agent-skills**: Create and manage custom agents with reusable skills following the Agent Skills specification

## License

MIT
