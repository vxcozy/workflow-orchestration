# Lessons Format

Template and examples for capturing learnings in `tasks/lessons.md`.

## Template

```markdown
# Lessons Learned

## [Date] - [Category]

**Mistake**: What went wrong
**Pattern**: The underlying cause or anti-pattern
**Rule**: Concrete rule to prevent recurrence
**Applied**: Where this rule applies (specific files, patterns, situations)
```

## Categories

Use these categories to organize lessons:

- **Architecture** - System design decisions
- **Testing** - Test coverage, edge cases
- **Performance** - Speed, memory, efficiency
- **Security** - Vulnerabilities, auth issues
- **API** - Interface design, contracts
- **Tooling** - Build, deploy, CI/CD
- **Communication** - Misunderstandings, unclear specs

## Example Lessons

```markdown
# Lessons Learned

## 2024-01-10 - Testing

**Mistake**: Deployed code that broke production because mocks hid the real API behavior
**Pattern**: Over-mocking in tests created false confidence
**Rule**: Always include at least one integration test that hits real services
**Applied**: All API endpoints, external service integrations

---

## 2024-01-12 - Architecture

**Mistake**: Added a feature flag that was never cleaned up, causing confusion 6 months later
**Pattern**: Technical debt accumulation through "temporary" solutions
**Rule**: Every feature flag must have a removal date in the TODO and a cleanup task
**Applied**: All feature flags, A/B tests, temporary workarounds

---

## 2024-01-15 - Performance

**Mistake**: N+1 query pattern caused 500ms page load
**Pattern**: Lazy loading in loops without considering query count
**Rule**: Before any loop that touches the database, check if batch loading is possible
**Applied**: All ORM queries in loops, GraphQL resolvers

---

## 2024-01-18 - Communication

**Mistake**: Built the wrong feature because requirements were ambiguous
**Pattern**: Assumed instead of asking for clarification
**Rule**: If a requirement has multiple interpretations, ask before implementing
**Applied**: All feature specs, bug reports with unclear reproduction steps
```

## Best Practices

1. **Write immediately** - Capture lessons right after the correction, not later
2. **Be specific** - Vague lessons don't prevent mistakes
3. **Include context** - Future you needs to understand why this matters
4. **Make rules actionable** - "Be more careful" is not a rule
5. **Review regularly** - Scan lessons at session start for relevant projects
