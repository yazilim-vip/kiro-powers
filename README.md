# Kiro Powers Collection

A curated collection of Kiro Powers to enhance your development workflow.

## What are Kiro Powers?

Kiro Powers are packages that extend Kiro's capabilities by bundling documentation, workflow guides (steering files), and optionally MCP (Model Context Protocol) servers. They provide structured, on-demand access to specialized tools and knowledge domains.

## Available Powers

| Power | Description | Keywords |
|-------|-------------|----------|
| [agent-creator](powers/agent-creator/) | Create and manage custom agents with specialized capabilities for automation, code review, documentation, testing, and more | agents, custom agents, agent creator, code review, documentation, testing, automation |
| [git-committer](powers/git-committer/) | Helps create well-formatted conventional commits following best practices | git, commits, conventional commits, version control, commit messages |

## Installation

### Install from GitHub (Recommended)

Install individual powers directly from this repository:

```
# In Kiro, ask:
"Install the agent-creator power from https://github.com/YOUR_USERNAME/YOUR_REPO/tree/main/powers/agent-creator"
```

Or use the Kiro Powers UI:
1. Open Command Palette → "Configure Powers"
2. Click "Install from URL"
3. Enter: `https://github.com/YOUR_USERNAME/YOUR_REPO/tree/main/powers/agent-creator`

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
"Help me create a conventional commit"

# Or activate explicitly
"Activate the agent-creator power"
"Activate the git-committer power"

# Or use the # context menu
Type # and select the power
```

Powers load their documentation and tools on-demand, keeping your context focused.

## Power Structure

Each power in this repository follows this structure:

```
powers/
└── power-name/
    ├── POWER.md           # Required: Documentation with frontmatter
    └── .steering/         # Optional: Workflow guides
        └── guide.md
```

### POWER.md Structure

The only required file is `POWER.md` with YAML frontmatter containing metadata:

```markdown
---
name: power-name
displayName: Power Name
description: What this power does
keywords: [keyword1, keyword2]
version: 1.0.0
license: MIT
---

# Power Name

Power documentation and instructions...
```

**Required frontmatter fields:**
- `name`: Power identifier (lowercase with hyphens)
- `displayName`: Human-readable name
- `description`: Brief description of what the power does
- `keywords`: Array of keywords for activation
- `version`: Semantic version number
- `license`: License identifier (e.g., MIT)

The POWER.md content should include:
- Overview of capabilities
- Usage examples
- Best practices
- Troubleshooting tips

### Steering Files (Optional)

Additional workflow guides in the `.steering/` directory provide detailed instructions for specific use cases. These are regular markdown files without frontmatter.

## Creating New Powers

To create a new power:

1. Create a directory under `powers/` with a descriptive name (lowercase-with-hyphens)
2. Create `POWER.md` with proper YAML frontmatter (see structure above)
3. Write clear documentation with usage examples and best practices
4. Optionally add `.steering/` directory with workflow guides for complex use cases

Follow the structure of existing powers as examples. The official documentation is at [kiro.dev/docs/powers/create/](https://kiro.dev/docs/powers/create/).

## Resources

- [Kiro Powers Documentation](https://kiro.dev/docs/powers/)
- [Creating Powers Guide](https://kiro.dev/docs/powers/create/)
- [Conventional Commits Specification](https://www.conventionalcommits.org/)

## License

MIT - See individual power directories for specific licenses
