# Commit Conventions

We follow the [Conventional Commits](https://www.conventionalcommits.org) standard.

## Format

```text
<type>(<scope>): <short description>

[optional body]

[optional footer]
```

Example footer:

```text
Closes #123
```

## Types

| Type | When to use |
|---|---|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `style` | Formatting, no logic change |
| `refactor` | Code restructure, no behavior change |
| `test` | Adding or updating tests |
| `chore` | Tooling, dependencies, build |
| `perf` | Performance improvement |
| `ci` | CI/CD configuration |
| `revert` | Reverting a previous commit |

## Scope

The scope is the area of the codebase affected:
`auth`, `contacts`, `deals`, `api`, `db`, `ui`, `infra`, `deps`, etc.

## Examples

```bash
feat(auth): add Google OAuth2 login
fix(api): correct pagination offset calculation
chore(deps): update axios to 1.6.0
docs(contributing): add branch naming section
test(auth): add unit tests for JWT expiry edge case
refactor(contacts): extract validation logic to service layer
```

## Rules

- Subject line: max 72 characters
- Use imperative mood: "add" not "added" or "adds"
- No period at the end of subject
- Body: explain WHY, not what (the diff shows what)
