# Conventional Commits Guide

When creating git commits, follow the Conventional Commits v1.0.0 specification.

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

## Common Scopes

Use these scopes based on what changed:

- `powers`: Changes to power definitions
- `agents`: Changes to agent configurations
- `docs`: Documentation files
- `steering`: Steering files
- `config`: Configuration changes
- `api`: API changes
- `ui`: User interface changes
- `core`: Core functionality

## Description Rules

- Use imperative mood: "add" not "added" or "adds"
- Start with lowercase
- No period at the end
- Keep under 72 characters
- Be specific and clear

## Examples

```
feat(powers): add git-committer power
fix(api): handle null response correctly
docs(readme): update installation instructions
refactor(core): simplify authentication logic
test(api): add integration tests for auth flow
chore: update dependencies
```

## Breaking Changes

Add `!` after type/scope or include `BREAKING CHANGE:` in footer:

```
feat(api)!: change authentication method

BREAKING CHANGE: API now requires OAuth2 tokens.
Update all clients to use new authentication flow.
```

## Workflow for Creating Commits

1. **Analyze Changes**: Review what files changed
   ```bash
   git status
   git diff --staged
   ```

2. **Determine Type**: Choose the appropriate commit type based on the primary change

3. **Identify Scope**: Use the scope that matches the changed area

4. **Write Description**: Clear, concise summary in imperative mood

5. **Add Body** (if needed): Explain what and why, not how

6. **Add Footers** (if applicable): Reference issues, note breaking changes

## Complete Example

```
feat(powers): add git-committer power

Create a new power for helping with conventional commits.
Includes documentation, steering files, and formatting guidance.

Follows Conventional Commits v1.0.0 specification.

Closes #123
```

## Reference

Full specification: https://www.conventionalcommits.org/en/v1.0.0/
