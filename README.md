# Workflow Orchestration

A skill for disciplined AI agent task execution with planning, verification, and self-improvement loops.

## Overview

Workflow orchestration provides a systematic approach to complex task execution:

| Practice | Purpose |
|----------|---------|
| **Plan Mode** | Think before acting on non-trivial tasks |
| **Subagent Delegation** | Keep main context clean |
| **Self-Improvement** | Learn from corrections |
| **Verification** | Prove work is complete |
| **Balanced Elegance** | Quality without over-engineering |
| **Autonomous Fixing** | Reduce user burden |

## Installation

### Via skills CLI (Recommended)

```bash
npx skills add vxcozy/workflow-orchestration
```

### Manual Installation

**Personal (all projects):**
```bash
git clone https://github.com/vxcozy/workflow-orchestration ~/.claude/skills/workflow-orchestration
```

**Project-specific:**
```bash
git clone https://github.com/vxcozy/workflow-orchestration .claude/skills/workflow-orchestration
```

## Usage

### Direct Invocation

```
/workflow-orchestration
```

### Automatic

The skill activates automatically for:
- Non-trivial tasks (3+ steps)
- Bug fixes and feature work
- Refactoring and architectural changes

## Documentation

This skill uses [Diataxis](https://diataxis.fr)-style documentation:

| Type | Purpose | Link |
|------|---------|------|
| **Tutorial** | Learn by doing | [docs/tutorial.md](docs/tutorial.md) |
| **How-To** | Solve specific problems | [docs/howto.md](docs/howto.md) |
| **Reference** | Technical details | [references/REFERENCE.md](references/REFERENCE.md) |
| **Explanation** | Understand concepts | [docs/explanation.md](docs/explanation.md) |

### Additional References

- [Task Templates](references/task-templates.md) - Ready-to-use todo.md formats
- [Lessons Format](references/lessons-format.md) - How to capture learnings

## File Structure

```
workflow-orchestration/
├── SKILL.md                    # Main skill (loaded by agents)
├── docs/
│   ├── tutorial.md             # Learning-oriented guide
│   ├── howto.md                # Task-oriented guides
│   └── explanation.md          # Understanding-oriented
├── references/
│   ├── REFERENCE.md            # Complete reference
│   ├── task-templates.md       # Todo file templates
│   └── lessons-format.md       # Lessons file format
├── README.md
└── LICENSE
```

## Quick Start

1. Install the skill
2. Start a non-trivial task
3. Create `tasks/todo.md` with your plan
4. Execute with progress tracking
5. Verify before marking complete
6. Capture lessons after corrections

## Core Principles

- **Simplicity First** - Minimal changes, minimal code
- **No Laziness** - Find root causes, no temporary fixes
- **Minimal Impact** - Only touch what's necessary

## Compatibility

Works with any [Agent Skills](https://agentskills.io)-compatible agent:
- Claude Code
- Cursor
- GitHub Copilot
- Gemini CLI
- And [many more](https://agentskills.io)

## License

MIT
