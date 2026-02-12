# How-To Guides

Task-focused guides for common scenarios.

## How to Fix a Bug Autonomously

**Situation**: User reports a bug and expects you to fix it without hand-holding.

1. **Gather information**
   - Read the error message/stack trace
   - Find the failing test or reproduction steps
   - Identify the affected file(s)

2. **Reproduce locally**
   - Run the failing test
   - Or follow reproduction steps
   - Confirm you see the same error

3. **Identify root cause**
   - Trace the error to its source
   - Check recent changes to the area
   - Look for similar past bugs

4. **Implement fix**
   - Make the minimal change that fixes the issue
   - Don't refactor unrelated code
   - Add a test if one doesn't exist

5. **Verify**
   - Run the test suite
   - Manually verify if applicable
   - Check that no new issues introduced

**Don't ask the user**: "Where should I look?" or "How do I run tests?"
**Do ask the user**: "There are two valid approaches—which do you prefer?"

---

## How to Handle a Stalled Task

**Situation**: You're stuck, something isn't working, progress has stopped.

1. **Stop immediately** - Don't keep trying the same approach

2. **Document what happened**
   ```markdown
   ## Progress Notes
   11:00 - Attempted X, got error Y
   11:15 - Tried Z, same error
   11:30 - BLOCKED: Need to re-plan
   ```

3. **Re-enter plan mode**
   - What assumptions were wrong?
   - What new information do you have?
   - What alternative approaches exist?

4. **Create new plan**
   - Present options to user if multiple valid paths
   - Or pivot to new approach if clearly better

5. **Resume execution**

**Anti-pattern**: Trying the same thing repeatedly, hoping for different results.

---

## How to Decide if Something Needs a Subagent

**Situation**: You need to do research or exploration.

**Use a subagent when:**

- Searching codebase for patterns (keeps tokens out of main context)
- Exploring unfamiliar area (focused investigation)
- Running parallel analyses (multiple independent queries)
- Result might be large (subagent can summarize)

**Keep in main context when:**

- You need the result immediately for next step
- The query is simple (one grep, one file read)
- You're in the middle of implementation flow

**Subagent prompt template:**
```
Search the codebase for [specific thing].
Report:
1. Files found
2. Relevant patterns
3. Recommendation for [current task]
Keep response under 500 words.
```

---

## How to Write an Effective Lesson

**Situation**: User corrected your work, and you need to capture the learning.

**Bad lesson:**
```markdown
**Mistake**: Made an error
**Pattern**: Wasn't careful
**Rule**: Be more careful
**Applied**: Everywhere
```

**Good lesson:**
```markdown
**Mistake**: Used `==` instead of `===` in JavaScript comparison, causing type coercion bug
**Pattern**: Defaulting to loose equality from habits in other languages
**Rule**: Always use `===` in JavaScript unless type coercion is explicitly intended
**Applied**: All JavaScript/TypeScript comparisons
```

**Checklist for good lessons:**
- [ ] Mistake is specific and reproducible
- [ ] Pattern explains *why* you made the mistake
- [ ] Rule is concrete and actionable
- [ ] Applied section tells you when to check this rule

---

## How to Know When a Task is Actually Done

**Situation**: You think you're done but want to be sure.

**Verification checklist:**

1. **Does it work?**
   - Run the code/tests
   - Manually verify if UI change
   - Check edge cases mentioned in requirements

2. **Is it correct?**
   - Re-read the original request
   - Does your implementation match?
   - Any requirements you missed?

3. **Is it complete?**
   - All acceptance criteria met?
   - Tests added for new functionality?
   - Documentation updated if needed?

4. **Is it good?**
   - Would you be proud of this code?
   - Would a senior engineer approve?
   - Any obvious improvements you skipped?

**Only after all four**: Mark the task complete.

---

## How to Balance Elegance vs. Shipping

**Situation**: Your solution works but feels hacky. Should you refactor?

**Refactor when:**
- The hack will cause problems in the near future
- You're touching this code anyway
- The elegant solution is only slightly more work
- The code is in a critical path

**Ship the hack when:**
- It's a one-off script or temporary fix
- The elegant solution requires major refactoring
- Time pressure is real and acknowledged
- You document the tech debt

**The question to ask:**
> "If I ship this hack, what's the realistic cost to fix it later vs. fixing it now?"

If the cost is similar, ship now. If fixing later is much harder, fix now.

---

## How to Start a New Session Effectively

**Situation**: Beginning work on a project you've worked on before.

1. **Review lessons**
   ```
   Read tasks/lessons.md
   ```
   Scan for patterns relevant to today's work.

2. **Check todo status**
   ```
   Read tasks/todo.md
   ```
   Any incomplete tasks from last session?

3. **Orient yourself**
   - What was the last thing completed?
   - Any blockers noted?
   - What's the current priority?

4. **Begin with plan mode** (if new task)
   - Don't assume you remember everything
   - Re-verify your understanding before coding
