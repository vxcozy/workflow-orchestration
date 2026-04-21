---
name: workflow-orchestration
description: "Structured multi-step task execution with plan-first workflow, progress tracking in tasks/todo.md, lessons capture in tasks/lessons.md, subagent delegation for parallel work, and verification gates before task completion. Use when the user requests a step-by-step plan, asks to track progress, needs multi-step implementation (3+ steps), wants verification checkpoints, or says 'plan this', 'break this down', or 'track this task'. Do not activate for single-step fixes, quick questions, or simple one-line changes."
license: MIT
user-invocable: true
triggers:
  - plan this task
  - break this down into steps
  - track my progress
  - step by step implementation
  - multi-step task
  - structured workflow
  - verify before completing
metadata:
  author: vxcozy
  version: "1.0.0"
---

# Workflow Orchestration

Structured multi-step task execution with planning, verification, and continuous improvement.

## Quick Reference

| Practice | When to Apply |
|----------|---------------|
| Plan Mode | Any task with 3+ steps or architectural decisions |
| Subagents | Research, exploration, parallel analysis |
| Lessons | After ANY user correction |
| Verification | Before marking any task complete |
| Elegance Check | Non-trivial changes only |

## 1. Plan Mode Default

- Enter plan mode for ANY task with 3+ steps or architectural decisions
- If the approach breaks down mid-task, STOP and re-plan immediately
- Use plan mode for verification steps, not just building
- Write detailed specs upfront to reduce ambiguity

## 2. Subagent Strategy

- Delegate research, exploration, and parallel analysis to subagents
- For complex problems, run multiple subagents in parallel
- One task per subagent with clear instructions and expected output format
- Template: `Agent({ description: "Search auth patterns", prompt: "Find all authentication middleware in src/ and list file paths with a one-line summary of each" })`

## 3. Self-Improvement Loop

After ANY correction from the user:

1. Update `tasks/lessons.md` with the mistake, root cause, and prevention rule
2. Write rules that prevent the same mistake in future sessions
3. Review lessons at session start to avoid repeating errors

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
- Run tests, check logs, demonstrate the fix or feature working
- If verification fails → return to the plan step and revise the approach before retrying

## 5. Elegance Gate

For changes touching 5+ files or when the solution feels forced: pause and evaluate simpler alternatives before proceeding.

## 6. Autonomous Bug Fixing

Reproduce → identify root cause → implement fix → verify resolved.

## Task Management Protocol

1. **Plan First**: Write plan to `tasks/todo.md` with checkable items
2. **Verify Plan**: Confirm approach with user before starting
3. **Track Progress**: Mark items complete as you go
4. **Explain Changes**: Provide a high-level summary at each step
5. **Verify Results**: Run tests and confirm behavior before marking done
6. **Handle Failures**: If verification fails → re-plan (step 1), don't push through
7. **Document Results**: Add a review summary to `tasks/todo.md`
8. **Capture Lessons**: Update `tasks/lessons.md` after any corrections

**Inline example** (full templates in [references/task-templates.md](references/task-templates.md)):

```markdown
# Task: Fix memory leak in WebSocket handler
## Plan
- [ ] Reproduce the issue locally
- [ ] Identify leak source with profiler
- [ ] Implement fix
- [ ] Verification: Memory stable over 1000 connections
```

