# Workflow Orchestration Skill

A [Claude Code](https://claude.ai/code) skill for disciplined, high-quality task execution with planning, verification, and self-improvement loops.

## Installation

### Option 1: Personal Installation (All Projects)

```bash
# Clone to your Claude skills directory
git clone https://github.com/YOUR_USERNAME/workflow-orchestration ~/.claude/skills/workflow-orchestration
```

### Option 2: Project Installation (Single Project)

```bash
# Add as a subdirectory in your project
git clone https://github.com/YOUR_USERNAME/workflow-orchestration .claude/skills/workflow-orchestration

# Or add as a git submodule
git submodule add https://github.com/YOUR_USERNAME/workflow-orchestration .claude/skills/workflow-orchestration
```

## Usage

### Direct Invocation

```
/workflow-orchestration
```

### Automatic Invocation

Claude will automatically apply this skill when:
- Starting non-trivial tasks (3+ steps or architectural decisions)
- Working on bugs, features, or refactoring
- Tasks require coordination between exploration, implementation, and verification

## What's Included

### Core Practices

| Practice | Description |
|----------|-------------|
| **Plan Mode Default** | Enter plan mode for any non-trivial task |
| **Subagent Strategy** | Offload research and exploration to keep context clean |
| **Self-Improvement Loop** | Capture lessons after corrections in `tasks/lessons.md` |
| **Verification Before Done** | Never mark complete without proving it works |
| **Demand Elegance** | Balance quality with pragmatism |
| **Autonomous Bug Fixing** | Just fix it—no hand-holding required |

### Task Management

The skill uses two tracking files:

- `tasks/todo.md` - Planning and progress tracking
- `tasks/lessons.md` - Captured learnings from corrections

### Core Principles

- **Simplicity First** - Make every change as simple as possible
- **No Laziness** - Find root causes, no temporary fixes
- **Minimal Impact** - Only touch what's necessary

## File Structure

```
workflow-orchestration/
├── SKILL.md          # Main skill definition
├── README.md         # This file
└── LICENSE           # MIT License
```

## License

MIT
