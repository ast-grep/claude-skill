# Claude Skills Marketplace

A collection of Claude Code plugins that extend Claude's capabilities with specialized skills.

## Available Plugins

### ast-grep

Structural code search using Abstract Syntax Tree (AST) patterns. Search codebases based on code structure rather than text matching.

**Features:**
- Structure-aware search that understands code syntax
- Metavariables (`$VAR`, `$$$ARGS`) to match any expression or statement
- Relational queries to find code inside specific contexts
- Composite logic (AND, OR, NOT) for complex matching

**Example queries:**
- "Find all async functions that don't have error handling"
- "Locate all React components that use a specific hook"
- "Find functions with more than 3 parameters"

## Installation

### Add the Marketplace

```
/plugin marketplace add github:dylan/claude-skills-marketplace
```

### Install a Plugin

```
/plugin install ast-grep@claude-skills-marketplace
```

Or browse available plugins:

```
/plugin
```

## Prerequisites

For the ast-grep plugin, you need ast-grep installed:

```bash
# macOS
brew install ast-grep

# npm
npm install -g @ast-grep/cli

# cargo
cargo install ast-grep
```

## Repository Structure

```
.claude-plugin/
└── marketplace.json          # Marketplace configuration
plugins/
└── ast-grep/
    ├── .claude-plugin/
    │   └── plugin.json       # Plugin manifest
    └── skills/
        └── ast-grep/
            ├── SKILL.md      # Skill instructions
            └── references/
                └── rule_reference.md
```

## Creating a New Plugin

1. Create a directory under `plugins/`
2. Add `.claude-plugin/plugin.json` with required `name` field
3. Add components (skills, commands, agents, hooks) in appropriate directories
4. Register the plugin in `.claude-plugin/marketplace.json`

### Plugin Manifest Example

```json
{
  "name": "my-plugin",
  "version": "1.0.0",
  "description": "What the plugin does",
  "author": "your-name"
}
```

## Resources

- [ast-grep Documentation](https://ast-grep.github.io/)
- [ast-grep Playground](https://ast-grep.github.io/playground.html)
- [Claude Code Plugins Guide](https://code.claude.com/docs/en/plugins.md)

## License

MIT
