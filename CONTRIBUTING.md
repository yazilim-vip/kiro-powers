# Contributing to Kiro Powers Collection

Thank you for your interest in contributing! This guide will help you add new powers to the collection.

## Power Structure

Each power must follow this directory structure:

```
powers/
└── your-power-name/
    ├── power.json          # Required: Power metadata
    ├── POWER.md           # Required: Documentation
    ├── .steering/         # Optional: Workflow guides
    │   └── guide.md
    └── mcpServers/        # Optional: MCP server configs (note: not "mcp")
        └── server-name/
            └── config.json
```

## Required Files

### power.json

The power configuration file with metadata:

```json
{
  "name": "your-power-name",
  "displayName": "Your Power Name",
  "version": "1.0.0",
  "description": "Brief description of what your power does (max 200 chars)",
  "keywords": ["keyword1", "keyword2", "keyword3"],
  "license": "MIT",
  "mcpServers": {}
}
```

**Required fields:**
- `name`: Lowercase with hyphens, matches directory name
- `displayName`: Human-readable name
- `version`: Semantic versioning (MAJOR.MINOR.PATCH)
- `description`: Clear, concise description
- `keywords`: Array of searchable terms (triggers power activation)
- `license`: License identifier (MIT, Apache-2.0, etc.)
- `mcpServers`: Object containing MCP server configurations (empty if none)

### POWER.md

The main documentation file that Kiro loads when the power is activated.

**Recommended structure:**

```markdown
# Power Name

Brief introduction (1-2 sentences)

## Overview

What the power does and why it's useful

## What You Can Do

- Feature 1
- Feature 2
- Feature 3

## Usage Examples

### Example 1: Common Task

\```
"Ask Kiro to do something with this power"
\```

### Example 2: Advanced Task

\```
"More complex usage example"
\```

## Configuration

Any setup or configuration required

## Best Practices

Tips for effective use

## Troubleshooting

Common issues and solutions

## Resources

- [External documentation](https://example.com)
```

**Guidelines:**
- Keep it focused and actionable
- Include concrete examples
- Use clear, conversational language
- Add code snippets where helpful
- Link to external resources

## Optional Components

### Steering Files

Add workflow guides in the `.steering/` directory for specific tasks:

```
.steering/
├── getting-started.md
├── advanced-workflows.md
└── troubleshooting.md
```

Steering files provide step-by-step instructions for specific workflows. They're loaded on-demand when users need detailed guidance.

### MCP Servers

If your power includes MCP integrations, configure them in `power.json`:

```json
{
  "mcpServers": {
    "server-name": {
      "command": "uvx",
      "args": ["package-name@latest"],
      "env": {
        "ENV_VAR": "value"
      }
    }
  }
}
```

## Testing Your Power

Before submitting:

1. **Install locally:**
   ```bash
   cp -r powers/your-power-name ~/.kiro/powers/
   ```

2. **Test activation:**
   - Open Kiro
   - Mention a keyword from your power
   - Verify Kiro activates the power
   - Check that POWER.md loads correctly

3. **Test functionality:**
   - Try all examples in your documentation
   - Verify MCP servers connect (if applicable)
   - Test steering files load properly

4. **Validate structure:**
   - Ensure power.json is valid JSON
   - Check all required fields are present
   - Verify file paths are correct

## Submission Process

1. **Fork this repository**

2. **Create a feature branch:**
   ```bash
   git checkout -b add-your-power-name
   ```

3. **Add your power:**
   ```bash
   mkdir -p powers/your-power-name
   # Add power.json, POWER.md, etc.
   ```

4. **Update registry:**
   Add your power to `powers/registry.json`:
   ```json
   {
     "name": "your-power-name",
     "path": "your-power-name",
     "displayName": "Your Power Name",
     "description": "Brief description",
     "keywords": ["keyword1", "keyword2"]
   }
   ```

5. **Update README:**
   Add your power to the table in README.md

6. **Commit with conventional commits:**
   ```bash
   git add .
   git commit -m "feat(powers): add your-power-name power"
   ```

7. **Push and create PR:**
   ```bash
   git push origin add-your-power-name
   ```
   Then open a pull request on GitHub

## Guidelines

### Naming
- Use lowercase with hyphens: `my-power-name`
- Be descriptive but concise
- Avoid generic names like "helper" or "utils"

### Keywords
- Choose 3-8 relevant keywords
- Include domain-specific terms
- Think about what users would type
- Keywords trigger automatic power activation

### Documentation
- Write for developers
- Be clear and concise
- Include working examples
- Test all code snippets
- Link to external resources

### Code Quality
- Follow existing patterns
- Keep it simple
- Comment complex logic
- Handle errors gracefully

### Licensing
- Specify a clear license
- Ensure compatibility with MIT
- Credit external resources
- Respect third-party licenses

## Review Process

Pull requests will be reviewed for:
- Correct structure and required files
- Quality of documentation
- Working examples
- Appropriate keywords
- License compatibility

## Questions?

- Open an issue for questions
- Check existing powers for examples
- Review [Kiro Powers documentation](https://kiro.dev/docs/powers/)

## Resources

- [Kiro Powers Documentation](https://kiro.dev/docs/powers/)
- [Creating Powers Guide](https://kiro.dev/docs/powers/create/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)
