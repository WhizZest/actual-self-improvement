# Self-Improvement Skill

Capture, review, promote, and extract durable lessons so future sessions avoid repeating the same mistakes.

## Overview

This skill provides a systematic approach to learning from debugging, user corrections, missing capabilities, and repeated workflow friction. It helps agents and teams build durable knowledge that prevents repeat mistakes across sessions.

## Key Features

- **Structured Learning Capture**: Log learnings, errors, and feature requests with consistent metadata
- **Deduplication**: Search existing entries before creating new ones to avoid duplicates
- **Promotion Workflow**: Promote proven lessons into project memory files (CLAUDE.md, AGENTS.md, etc.)
- **Skill Extraction**: Extract reusable skills from recurring patterns
- **Helper Scripts**: Python and bash utilities for managing learnings

## When to Use

Use this skill for reusable learning, not for routine issues. A good entry typically:
- Corrects a wrong assumption
- Reveals a project-specific convention
- Required real debugging or investigation
- Is likely to recur
- Should change future workflow, memory, or tooling

**Do not log**: obvious typos, expected validation failures, or errors solved immediately with no transferable lesson.

## Quick Start

1. Initialize learnings in your workspace:
   ```bash
   python3 scripts/learnings.py init --root /absolute/path/to/workspace
   ```

2. Review existing learnings before risky work:
   ```bash
   python3 scripts/learnings.py status --root /absolute/path/to/workspace
   ```

3. Log a new learning:
   ```bash
   python3 scripts/learnings.py log-learning \
     --root /absolute/path/to/workspace \
     --category correction \
     --priority high \
     --area backend \
     --summary "Project uses pnpm workspaces, not npm" \
     --details "Attempted npm install. Lockfile and workspace config showed pnpm." \
     --suggested-action "Check for pnpm-lock.yaml before assuming npm."
   ```

## Entry Types

| Type | Use Case |
|------|----------|
| **Learning** | Corrections, knowledge gaps, best practices, durable conventions |
| **Error** | Non-obvious failures, exceptions, tool/API issues worth remembering |
| **Feature Request** | Missing capabilities or recurring friction points |

## Path Model

- **Skill Root**: Contains bundled resources (scripts/, references/, assets/)
- **Workspace Root**: Where project learnings live (.learnings/, CLAUDE.md, AGENTS.md, etc.)

Never write learnings into the installed skill directory. Always target the workspace root.

## Documentation

- `SKILL.md` - Complete skill documentation and workflow
- `references/entry-formats.md` - Full field schemas and templates
- `references/examples.md` - Concrete examples of good entries
- `references/promotion-and-extraction.md` - Promotion rules and skill extraction criteria

## Requirements

- Python 3.6+ for helper scripts
- Bash for hook helpers (optional)

## Source

This skill was originally sourced from:  
https://clawhub.ai/tristanmanchester/actual-self-improvement

## License

Refer to the original source for licensing information.
