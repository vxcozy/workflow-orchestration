# Tutorial: Your First Orchestrated Task

Learn the workflow orchestration approach by working through a real example.

## What You'll Learn

- How to plan before executing
- When to delegate to subagents
- How to verify your work
- How to capture lessons

## Prerequisites

- Claude Code or compatible AI agent installed
- The workflow-orchestration skill installed
- A project to work on

## Step 1: Receive a Task

Let's say you receive this task:

> "Add a dark mode toggle to the settings page"

Before jumping in, apply the **Plan Mode Default** practice.

## Step 2: Enter Plan Mode

Ask yourself: Does this task have 3+ steps or architectural decisions?

**Yes** - it involves:
1. Understanding current theme system
2. Adding toggle UI component
3. Implementing theme switching logic
4. Persisting user preference
5. Testing the feature

Create `tasks/todo.md`:

```markdown
# Task: Add dark mode toggle to settings page

## Plan
- [ ] Research existing theme/styling patterns in codebase
- [ ] Design approach for theme state management
- [ ] Implement toggle component on settings page
- [ ] Add theme switching logic
- [ ] Persist preference to localStorage/database
- [ ] Test light/dark switching
- [ ] Verification: Manual test + visual regression check

## Progress Notes

## Review
```

## Step 3: Delegate Research to Subagent

The first step is research. This is perfect for a subagent—it keeps your main context clean.

Delegate:
> "Search this codebase for existing theme, color, or styling patterns. Look for CSS variables, theme contexts, or color scheme utilities. Report back what you find."

Wait for results before proceeding.

## Step 4: Execute with Progress Tracking

As you work through each step, update `tasks/todo.md`:

```markdown
## Progress Notes
10:00 - Subagent found existing CSS variables in styles/theme.css
10:15 - Using CSS custom properties approach, no React context needed
10:30 - Toggle component added to SettingsPage.tsx
10:45 - Theme switching working via data-theme attribute
```

Mark items complete as you finish them.

## Step 5: Verify Before Done

Before marking the task complete, verify:

- [ ] Does the toggle actually switch themes?
- [ ] Does the preference persist on refresh?
- [ ] Are all UI elements properly themed?
- [ ] Would a staff engineer approve this code?

Run through each check. If something fails, fix it before proceeding.

## Step 6: Complete and Review

Update your todo with the review:

```markdown
## Review
Added dark mode toggle using CSS custom properties approach.
Toggle persists to localStorage. All existing components
properly inherit theme colors. No new dependencies added.
```

## Step 7: Capture Lessons (If Applicable)

Did anything unexpected happen? Did you make a mistake the user corrected?

If yes, add to `tasks/lessons.md`:

```markdown
## 2024-01-15 - Architecture

**Mistake**: Initially tried to use React context for theme, but codebase already had CSS variables
**Pattern**: Jumping to familiar solutions without checking existing patterns
**Rule**: Always search for existing patterns before introducing new architecture
**Applied**: Any feature that could use existing infrastructure
```

## Summary

You've now completed an orchestrated task:

1. **Planned** before executing
2. **Delegated** research to a subagent
3. **Tracked** progress in todo.md
4. **Verified** before marking complete
5. **Captured** lessons for future improvement

Repeat this process for every non-trivial task, and your execution quality will continuously improve.

## Next Steps

- Read the [How-To Guides](howto.md) for specific scenarios
- Check the [Reference](../references/REFERENCE.md) for decision criteria
- Review [Explanation](explanation.md) to understand why these practices work
