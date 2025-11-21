# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Claude Code plugin marketplace - a collection of plugins that extend Claude's capabilities with specialized skills, commands, and agents.

## Repository Structure

```
.claude-plugin/
└── marketplace.json              # Marketplace registry (lists all plugins)
plugins/
└── <plugin-name>/
    ├── .claude-plugin/
    │   └── plugin.json           # Plugin manifest (required: name field)
    ├── skills/                   # Skills extend Claude's autonomous capabilities
    │   └── <skill-name>/
    │       ├── SKILL.md          # Skill instructions with YAML frontmatter
    │       └── references/       # Supporting documentation
    ├── commands/                 # Custom slash commands (markdown files)
    ├── agents/                   # Specialized subagents (markdown files)
    └── hooks/                    # Event-driven automation (JSON files)
```

## Current Plugins

### ast-grep
Structural code search using AST patterns. Located at `plugins/ast-grep/`.

Key files:
- `plugins/ast-grep/skills/ast-grep/SKILL.md` - Main skill instructions
- `plugins/ast-grep/skills/ast-grep/references/rule_reference.md` - Rule syntax reference

## Adding a New Plugin

1. Create `plugins/<name>/.claude-plugin/plugin.json`:
   ```json
   {"name": "<name>", "version": "1.0.0", "description": "..."}
   ```

2. Add components in appropriate directories (skills/, commands/, agents/, hooks/)

3. Register in `.claude-plugin/marketplace.json`:
   ```json
   {"name": "<name>", "source": "./plugins/<name>", ...}
   ```

## Key Plugin Concepts

- **Skills**: SKILL.md files with YAML frontmatter (`name`, `description`) teach Claude new capabilities
- **Commands**: Markdown files that define custom `/command` operations
- **Agents**: Specialized subagents Claude can invoke for specific tasks
- **Hooks**: JSON configs that respond to events (PostToolUse, SessionStart, etc.)

## Critical Pattern for ast-grep Rules

Always use `stopBy: end` for relational rules:
```yaml
has:
  pattern: await $EXPR
  stopBy: end
```
