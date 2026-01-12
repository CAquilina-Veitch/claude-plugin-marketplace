# Create Plugin Skill

Use this skill when the user wants to create a new Claude Code plugin.

## When to Use

Invoke this skill when the user:
- Wants to create a new Claude Code plugin
- Asks to scaffold a plugin structure
- Needs help setting up a plugin with commands, agents, skills, hooks, or MCP servers

## Plugin Structure

When creating a plugin, always use this directory structure:

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json              # Required: Plugin manifest
├── commands/                     # Optional: Slash commands (*.md files)
├── agents/                       # Optional: Subagents (*.md files)
├── skills/                       # Optional: Skills (subdirs with SKILL.md)
│   └── skill-name/
│       └── SKILL.md
├── hooks.json                    # Optional: Event hooks
├── .mcp.json                     # Optional: MCP server configs
└── .lsp.json                     # Optional: LSP server configs
```

## Plugin Manifest (plugin.json)

The `.claude-plugin/plugin.json` manifest is required:

```json
{
  "name": "plugin-name",
  "version": "1.0.0",
  "description": "What the plugin does",
  "author": {
    "name": "Author Name"
  },
  "license": "MIT",
  "keywords": ["relevant", "tags"]
}
```

## Component Templates

### Command Template (commands/command-name.md)

```markdown
# Command Name

Description of what this command does.

## Usage

How to use the command and what arguments it accepts.

$ARGUMENTS will contain any text passed after the command.

## Instructions

Step-by-step instructions for Claude to follow when this command is invoked.
```

### Agent Template (agents/agent-name.md)

```markdown
---
name: agent-name
description: Short description for when Claude should use this agent
tools:
  - Bash
  - Read
  - Write
  - Edit
  - Glob
  - Grep
---

# Agent Name

Detailed instructions for how this agent should behave and what tasks it handles.
```

### Skill Template (skills/skill-name/SKILL.md)

```markdown
# Skill Name

Description of when and how to use this skill.

## When to Use

Conditions that should trigger this skill.

## Instructions

What Claude should do when this skill is invoked.
```

### Hooks Template (hooks.json)

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Bash",
        "type": "command",
        "command": "echo 'Running Bash command'"
      }
    ],
    "PostToolUse": [],
    "UserPromptSubmit": []
  }
}
```

Available hook events:
- `PreToolUse` / `PostToolUse` - Before/after tool execution
- `UserPromptSubmit` - When user sends a message
- `Stop` / `SubagentStop` - When agent completes
- `PreCompact` - Before context compaction
- `SessionStart` / `SessionEnd` - Session lifecycle
- `Notification` - System notifications

### MCP Server Template (.mcp.json)

```json
{
  "mcpServers": {
    "server-name": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-name"],
      "env": {}
    }
  }
}
```

## Instructions

When creating a plugin:

1. **Ask the user** what components they need (commands, agents, skills, hooks, MCP servers)
2. **Create the directory structure** at the specified location
3. **Generate plugin.json** with appropriate name, description, and keywords
4. **Create requested components** using the templates above
5. **Explain how to install** the plugin:
   - For local testing: `/plugin install ./path/to/plugin`
   - For marketplace: Add to marketplace.json and use `/plugin install name@marketplace`

## Validation

After creating a plugin, remind the user they can validate it with:
```
/plugin validate ./path/to/plugin
```
