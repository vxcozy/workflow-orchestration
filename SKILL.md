---
name: workflow-orchestration
description: |
  Disciplined task execution with planning, verification, and self-improvement loops.
  Use when starting non-trivial tasks (3+ steps), fixing bugs, building features,
  refactoring code, or when rigorous execution with quality gates is needed.
  Includes subagent delegation, lessons tracking, and staff-engineer-level verification.
license: MIT
metadata:
  author: vxcozy
  version: "1.0.0"
---

# Workflow Orchestration

Apply these practices for disciplined, high-quality task execution.

## Quick Reference

| Practice | When to Apply |
|----------|---------------|
| Plan Mode | Any task with 3+ steps or architectural decisions |
| Subagents | Research, exploration, parallel analysis |
| Lessons | After ANY user correction |
| Verification | Before marking any task complete |
| Elegance Check | Non-trivial changes only |

## 1. Plan Mode Default

- Enter plan mode for ANY non-trivial task (3+ steps or architectural decisions)
- If something goes sideways, STOP and re-plan immediately
- Use plan mode for verification steps, not just building
- Write detailed specs upfront to reduce ambiguity

## 2. Subagent Strategy

Keep the main context window clean:

- Offload research, exploration, and parallel analysis to subagents
- For complex problems, throw more compute at it via subagents
- One task per subagent for focused execution

**Template:**

```
Agent({
  description: "Search auth patterns",
  prompt: "Find all authentication middleware in src/ and list file paths with a one-line summary of each."
})
```

## 3. Self-Improvement Loop

After ANY correction from the user:

1. Update `tasks/lessons.md` with the pattern
2. Write rules that prevent the same mistake
3. Review lessons at session start

**Inline example** (full template in [references/lessons-format.md](references/lessons-format.md)):

```markdown
## 2024-01-10 - Testing
**Mistake**: Mocks hid real API behavior; production broke
**Pattern**: Over-mocking created false confidence
**Rule**: Include at least one integration test hitting real services
**Applied**: All API endpoints, external service integrations
```

## 4. Verification Before Done

- Never mark a task complete without proving it works
- Diff behavior between main and your changes when relevant
- Ask yourself: "Would a staff engineer approve this?"
- Run tests, check logs, demonstrate corrections
- If verification fails → return to the plan step and revise before retrying

## 5. Demand Elegance (Balanced)

- For non-trivial changes: pause and ask "is there a more elegant way?"
- If a fix feels hacky: "Knowing everything I know now, implement the elegant solution"
- Skip this for simple, obvious fixes—don't over-engineer

## 6. Autonomous Bug Fixing

- When given a bug report: Just fix it. Don't ask for hand-holding
- Point at logs, errors, failing tests—then resolve them
- Zero context switching required from the user

## Task Management Protocol

1. **Plan First**: Write plan to `tasks/todo.md` with checkable items
2. **Verify Plan**: Check in before starting implementation
3. **Track Progress**: Mark items complete as you go
4. **Explain Changes**: High-level summary at each step
5. **Verify Results**: Run tests and confirm behavior before marking done
6. **Handle Failures**: If verification fails → re-plan (step 1), don't push through
7. **Document Results**: Add review to `tasks/todo.md`
8. **Capture Lessons**: Update `tasks/lessons.md` after corrections

**Inline example** (full templates in [references/task-templates.md](references/task-templates.md)):

```markdown
# Task: Fix memory leak in WebSocket handler
## Plan
- [ ] Reproduce the issue locally
- [ ] Identify leak source with profiler
- [ ] Implement fix
- [ ] Verification: Memory stable over 1000 connections
```

## Core Principles

- **Simplicity First**: Make every change as simple as possible
- **No Laziness**: Find root causes. No temporary fixes. Senior developer standards
- **Minimal Impact**: Only touch what's necessary. Avoid introducing bugs
