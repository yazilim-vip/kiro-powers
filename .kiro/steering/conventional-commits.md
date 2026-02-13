---
inclusion: auto
---

# Conventional Commits for This Repository

When creating git commits for this repository, follow the Conventional Commits v1.0.0 specification.

## Commit Message Format

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

## Commit Types

- `feat`: New feature or capability
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style/formatting (no functional changes)
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Add or update tests
- `build`: Build system or dependency changes
- `ci`: CI/CD configuration changes
- `chore`: Maintenance tasks
- `revert`: Revert a previous commit

## Scopes for This Repository

Use these scopes based on what changed:

- `powers`: Changes to power definitions in `powers/` directory
- `agents`: Changes to agent configurations in `.kiro/agents/`
- `docs`: Documentation files (README, CONTRIBUTING, etc.)
- `steering`: Steering files in `.kiro/steering/`
- `examples`: Example code or configurations

## Description Rules

- Use imperative mood: "add" not "added" or "adds"
- Start with lowercase
- No period at the end
- Keep under 72 characters
- Be specific and clear

## Examples for This Repository

```
feat(powers): add agent-skills power
fix(powers): correct power.json schema validation
docs(readme): update installation instructions
docs(contributing): add power creation guidelines
chore: update .gitignore
feat(steering): add conventional commits guide
```

## Breaking Changes

Add `!` after type/scope or include `BREAKING CHANGE:` in footer:

```
feat(powers)!: change power.json schema

BREAKING CHANGE: power.json now requires 'version' field.
Update all power configs to include version.
```

## Workflow for Creating Commits

1. **Analyze Changes**: Review what files changed
   ```bash
   git status
   git diff --staged
   ```

2. **Determine Type**: Choose the appropriate commit type based on the primary change

3. **Identify Scope**: Use the scope that matches the changed area (powers, agents, docs, etc.)

4. **Write Description**: Clear, concise summary in imperative mood

5. **Add Body** (if needed): Explain what and why, not how

6. **Add Footers** (if applicable): Reference issues, note breaking changes

## Complete Example

```
feat(powers): add agent-skills power

Create a new power for building custom agents with reusable skills.
Includes documentation, steering files, and examples.

Follows Agent Skills specification and Kiro power structure.

Closes #123
```

## Reference

Full specification: https://www.conventionalcommits.org/en/v1.0.0/
