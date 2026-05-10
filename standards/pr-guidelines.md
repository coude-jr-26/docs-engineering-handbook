# Pull Request Guidelines

## Before Opening a PR

- [ ] Your branch is up to date with `develop`
- [ ] All tests pass locally (`npm test`)
- [ ] No linter errors (`npm run lint`)
- [ ] No console.log or debug statements
- [ ] No hardcoded secrets or credentials

## Branch Naming
```text
{type}/{issue-number}-{kebab-case-description}
Examples:
feature/123-add-contact-search
fix/456-correct-pagination
chore/789-update-eslint-config
```

## PR Size

Keep PRs small and focused. A PR that touches 20+ files is hard to review.
If your feature is large, break it into multiple sequential PRs.

- **Small:** < 200 lines changed ✅
- **Medium:** 200–500 lines ⚠️ (include extra context in description)
- **Large:** > 500 lines ❌ (break it up, or justify in description)

## Review Process

1. Open as **Draft** while working — CI runs immediately
2. Convert to **Ready for Review** when done
3. Tag relevant reviewers (CODEOWNERS does this automatically)
4. Respond to all review comments — don't just resolve them silently
5. After addressing feedback, re-request review
6. Do **not** merge your own PR (except Tech Leads in emergencies)

## Giving Reviews

- Be specific: point to the exact line and explain why
- Be kind: review the code, not the person
- Use prefixes: `nit:` for minor suggestions, `blocking:` for required changes
- Approve only when you'd be comfortable owning that code

## Merge Strategy

- `feature/* → develop`: **Squash and merge** (clean history)
- `develop → main`: **Merge commit** (preserve release boundary)
- `hotfix/* → main`: **Squash and merge** (then backport to develop)
