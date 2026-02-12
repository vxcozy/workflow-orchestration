# Task Templates

Ready-to-use templates for task management files.

## tasks/todo.md

```markdown
# Task: [Title]

## Plan
- [ ] Step 1: [Description]
- [ ] Step 2: [Description]
- [ ] Step 3: [Description]
- [ ] Verification: [How to prove it works]

## Progress Notes
<!-- Add timestamped notes as you work -->

## Review
<!-- Summary when complete: what changed, what was learned -->
```

## Example: Feature Implementation

```markdown
# Task: Add user authentication

## Plan
- [ ] Research existing auth patterns in codebase
- [ ] Design session management approach
- [ ] Implement login endpoint
- [ ] Implement logout endpoint
- [ ] Add session middleware
- [ ] Write tests
- [ ] Verification: Manual test + all tests pass

## Progress Notes
2024-01-15 10:00 - Found existing JWT utilities in lib/auth.ts
2024-01-15 11:30 - Login endpoint complete, tested with curl

## Review
Added JWT-based auth with 24h expiry. Reused existing token utilities.
Tests cover happy path and invalid credentials.
```

## Example: Bug Fix

```markdown
# Task: Fix memory leak in WebSocket handler

## Plan
- [ ] Reproduce the issue locally
- [ ] Identify leak source with profiler
- [ ] Implement fix
- [ ] Verification: Memory stable over 1000 connections

## Progress Notes
2024-01-15 14:00 - Reproduced: memory grows 10MB/min under load
2024-01-15 14:30 - Found: event listeners not cleaned up on disconnect

## Review
Root cause: Missing removeEventListener in cleanup. Added proper cleanup
in disconnect handler. Memory now stable at ~50MB under same load.
```
