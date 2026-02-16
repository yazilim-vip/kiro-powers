# Creating Steering Files

This guide covers creating steering files that give Kiro persistent knowledge about your project.

## What Is Steering?

Steering provides persistent project knowledge through markdown files in `.kiro/steering/`. Instead of explaining conventions in every chat, steering files ensure Kiro consistently follows your established patterns, libraries, and standards.

## Key Benefits

- **Consistent Code Generation** — Every component, API endpoint, or test follows your team's patterns
- **Reduced Repetition** — No need to explain project standards in each conversation
- **Team Alignment** — All developers work with the same standards
- **Scalable Knowledge** — Documentation that grows with your codebase

## Default Steering Files

Kiro automatically creates three foundational files included in every interaction:

- **product.md** — Product purpose, target users, key features, business goals
- **tech.md** — Frameworks, libraries, dev tools, technical constraints
- **structure.md** — File organization, naming conventions, import patterns, architecture

## Creating Custom Steering Files

1. Navigate to the Steering section in the Kiro panel
2. Click "+" to create a new `.md` file
3. Choose a descriptive filename (e.g., `api-standards.md`)
4. Write guidance in standard markdown
5. Optionally use the Refine button to let Kiro format it

Custom steering files are stored in `.kiro/steering/` and are immediately available.

## Inclusion Modes

Configure via YAML frontmatter at the top of the file:

### Always Included (default)

```yaml
---
inclusion: always
---
```

Loaded into every Kiro interaction. Use for core standards that should influence all code generation.

Use cases: Tech stack, coding conventions, security policies, architectural principles.

### Conditional Include

```yaml
---
inclusion: fileMatch
fileMatchPattern: 'components/**/*.tsx'
---
```

Loaded only when working with files matching the pattern. Keeps context relevant and reduces noise.

Common patterns:
- `*.tsx` — React components and JSX files
- `app/api/**/*` — API routes and backend logic
- `**/*.test.*` — Test files and testing utilities
- `src/components/**/*` — Component-specific guidelines
- `*.md` — Documentation files

### Manual Include

```yaml
---
inclusion: manual
---
```

Available on-demand by typing `#steering-file-name` in chat. Gives precise control over when specialized context is needed.

Use cases: Specialized workflows, troubleshooting guides, migration procedures, context-heavy documentation.

## File References

Link to live project files to keep steering current:

```markdown
#[[file:api/openapi.yaml]]
#[[file:components/ui/button.tsx]]
#[[file:.env.example]]
```

## Steering Locations

- **Workspace**: `.kiro/steering/` — project-specific, shared with team via version control
- **Global**: `~/.kiro/steering/` — personal conventions across all workspaces

## Common Steering Strategies

- `api-standards.md` — REST conventions, error formats, auth flows, versioning
- `testing-standards.md` — Unit test patterns, mocking approaches, coverage expectations
- `code-conventions.md` — Naming patterns, file organization, import ordering, architecture
- `security-policies.md` — Auth requirements, validation rules, sanitization standards
- `deployment-workflow.md` — Build procedures, environment config, rollback strategies

## Best Practices

- **One domain per file** — API design, testing, or deployment procedures
- **Clear names** — `api-standards.md`, `testing-unit-patterns.md`, `components-form-validation.md`
- **Include context** — Explain why decisions were made, not just what the standards are
- **Provide examples** — Code snippets and before/after comparisons to demonstrate standards
- **Security first** — Never include API keys, passwords, or sensitive data
- **Maintain regularly** — Update as your project evolves, remove outdated conventions
- **Right inclusion mode** — Use `always` sparingly; prefer `fileMatch` or `manual` for specialized guidance

## Troubleshooting

**Steering not applied?**
- Check inclusion mode in frontmatter
- For conditional includes, verify `fileMatchPattern` matches your files
- Ensure the file is in `.kiro/steering/`

**Too much context noise?**
- Switch from `always` to `fileMatch` or `manual` inclusion
- Split large files into focused, domain-specific files

**Team not seeing updates?**
- Commit steering files to version control
- Verify teammates have pulled the latest changes
