# Cody Plugin Marketplace

A personal Claude Code plugin marketplace.

## Installation

Add this marketplace to Claude Code:

```bash
# From local path
/plugin marketplace add D:\Repositories\cody-plugin-marketplace

# Or if hosted on GitHub
/plugin marketplace add github:username/cody-plugin-marketplace
```

## Installing Plugins

Once the marketplace is added, install plugins with:

```bash
/plugin install plugin-creator@cody-plugin-marketplace
```

## Available Plugins

| Plugin | Description |
|--------|-------------|
| `plugin-creator` | A skill that helps scaffold and create new Claude Code plugins |

## Adding New Plugins

1. Create your plugin in `plugins/your-plugin-name/`:

```
plugins/your-plugin-name/
├── .claude-plugin/
│   └── plugin.json
├── commands/        # Optional
├── agents/          # Optional
├── skills/          # Optional
├── hooks.json       # Optional
└── .mcp.json        # Optional
```

2. Add it to `.claude-plugin/marketplace.json`:

```json
{
  "plugins": [
    {
      "name": "your-plugin-name",
      "source": "./plugins/your-plugin-name",
      "description": "What it does",
      "version": "1.0.0"
    }
  ]
}
```

3. Validate your plugin:

```bash
/plugin validate ./plugins/your-plugin-name
```

## Plugin Structure Reference

See the `plugin-creator` skill for templates and detailed structure documentation.

## Commands

```bash
/plugin marketplace list              # List added marketplaces
/plugin marketplace remove <name>     # Remove a marketplace
/plugin install <name>@<marketplace>  # Install a plugin
/plugin uninstall <name>@<marketplace># Remove a plugin
/plugin validate <path>               # Validate plugin structure
```
