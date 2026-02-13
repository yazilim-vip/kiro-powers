# Git Committer Power

A power to help you create well-formatted conventional commits following best practices.

## What is Git Committer?

Git Committer helps you write consistent, meaningful commit messages that follow the Conventional Commits specification. It provides guidance on commit types, scopes, and formatting to maintain a clean git history.

## Features

- Conventional Commits v1.0.0 specification support
- Project-specific scope recommendations
- Commit message formatting guidance
- Breaking change handling
- Multi-line commit support with body and footers

## Usage

Simply ask Kiro to help with commits:

```
"Help me commit these changes"
"Create a commit message for my changes"
"Commit and push with conventional format"
```

Kiro will analyze your changes and suggest an appropriate commit message following conventional commits format.

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

## Examples

```bash
feat(powers): add git-committer power
fix(agents): correct agent configuration schema
docs(readme): update installation instructions
chore: update dependencies
```

## Breaking Changes

For breaking changes, add `!` after type/scope:

```bash
feat(api)!: change authentication method

BREAKING CHANGE: API now requires OAuth2 tokens.
Update all clients to use new authentication flow.
```

## Best Practices

1. Use imperative mood: "add" not "added"
2. Start description with lowercase
3. Keep description under 72 characters
4. Be specific and clear
5. Use body to explain what and why, not how

## Reference

Full specification: https://www.conventionalcommits.org/en/v1.0.0/
