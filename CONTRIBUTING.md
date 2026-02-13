# Contributing to Kiro Powers

Thanks for your interest in contributing! This guide will help you create and submit new powers.

## Creating a New Power

### 1. Use the Power Builder

The easiest way to create a new power is using Kiro's built-in power-builder:

1. Activate the power-builder power in Kiro
2. Follow the guided workflow to scaffold your power
3. Test thoroughly before submitting

### 2. Manual Creation

If creating manually, follow this structure:

```
powers/
└── your-power-name/
    ├── power.json
    ├── POWER.md
    ├── steering/
    └── mcp/
```

#### power.json

```json
{
  "name": "your-power-name",
  "displayName": "Your Power Name",
  "version": "1.0.0",
  "description": "Brief description of what your power does",
  "keywords": ["keyword1", "keyword2"],
  "mcpServers": {}
}
```

#### POWER.md

Document your power thoroughly:
- Overview and purpose
- Installation requirements
- Usage examples
- Available tools (if MCP servers included)
- Common workflows

## Submission Guidelines

1. Fork this repository
2. Create a new branch: `git checkout -b add-power-name`
3. Add your power to the `powers/` directory
4. Test your power locally
5. Submit a pull request with:
   - Clear description of what the power does
   - Any dependencies or requirements
   - Example usage

## Quality Standards

- Clear, concise documentation
- Tested functionality
- Proper error handling
- Meaningful keywords for discoverability
- Follow existing power conventions

## Questions?

Open an issue or reach out to the maintainers.
