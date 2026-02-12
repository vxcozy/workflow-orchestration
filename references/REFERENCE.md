# Workflow Orchestration Reference

Complete reference for all practices, rules, and decision criteria.

## Practice Reference

### Plan Mode

**When to enter plan mode:**
- Task has 3+ distinct steps
- Architectural decisions required
- Multiple files will be modified
- Unfamiliar codebase area
- User explicitly requests planning

**When to skip plan mode:**
- Single-line fixes
- Typo corrections
- Adding a log statement
- Task has clear, unambiguous instructions

**Plan mode checklist:**
- [ ] Problem clearly stated
- [ ] Approach outlined with steps
- [ ] Success criteria defined
- [ ] Potential risks identified
- [ ] User has approved plan

### Subagent Delegation

**Delegate to subagents:**
- Codebase exploration and search
- Documentation research
- Parallel analysis of multiple files
- Independent verification tasks
- Any research that might pollute main context

**Keep in main context:**
- Final implementation decisions
- User communication
- State that needs to persist
- Sequential dependent operations

**Subagent rules:**
- One task per subagent
- Clear, specific instructions
- Define expected output format
- Set scope boundaries

### Self-Improvement Loop

**Trigger conditions:**
- User corrects your work
- Tests reveal missed edge case
- Review feedback received
- Same mistake made twice

**Lesson quality checklist:**
- [ ] Mistake is specific, not vague
- [ ] Pattern identifies root cause
- [ ] Rule is actionable and testable
- [ ] Applied section is concrete

### Verification Standards

**Verification methods by task type:**

| Task Type | Minimum Verification |
|-----------|---------------------|
| Bug fix | Reproduce → Fix → Verify fixed |
| Feature | Tests pass + manual demo |
| Refactor | Behavior unchanged + tests pass |
| Performance | Before/after metrics |
| Security | Specific vulnerability addressed |

**Staff engineer approval criteria:**
- Code is readable and maintainable
- Edge cases handled
- No obvious security issues
- Tests are meaningful, not just coverage
- Changes are minimal and focused

### Elegance Assessment

**Check for elegance when:**
- Solution feels hacky or forced
- You're fighting the framework
- Similar code exists elsewhere
- Change touches 5+ files

**Skip elegance check when:**
- Fix is obviously correct
- Time-critical bug fix
- Change is under 10 lines
- Pattern already established in codebase

**Elegance questions:**
1. Is there a simpler approach?
2. Am I duplicating existing functionality?
3. Would I be embarrassed to show this code?
4. Does this follow existing patterns?

### Autonomous Bug Fixing

**Information to gather first:**
- Error messages and stack traces
- Steps to reproduce
- Expected vs actual behavior
- Recent changes to affected area

**Fix without asking when:**
- Error message is clear
- Root cause is identifiable
- Fix is contained to affected area
- Tests can verify the fix

**Ask before fixing when:**
- Multiple valid approaches exist
- Fix requires architectural change
- Business logic interpretation needed
- Change affects user-facing behavior

## Decision Trees

### Should I Enter Plan Mode?

```
Task received
    │
    ├─ Is it a single-line fix? → No plan needed
    │
    ├─ Are there 3+ steps? → Enter plan mode
    │
    ├─ Does it involve architecture? → Enter plan mode
    │
    ├─ Am I uncertain about approach? → Enter plan mode
    │
    └─ Otherwise → Proceed directly
```

### Should I Use a Subagent?

```
Need to do research/exploration
    │
    ├─ Will it add >1000 tokens to context? → Use subagent
    │
    ├─ Is it independent of current work? → Use subagent
    │
    ├─ Could it run in parallel? → Use subagent
    │
    └─ Otherwise → Do it in main context
```

### Is This Task Complete?

```
Implementation done
    │
    ├─ Did I prove it works? → If no, verify first
    │
    ├─ Do tests pass? → If no, fix tests
    │
    ├─ Would staff engineer approve? → If no, improve
    │
    └─ All yes → Mark complete
```
