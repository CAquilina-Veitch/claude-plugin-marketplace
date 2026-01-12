# Don't Ask On

Enable "don't ask" mode - auto-deny tools unless pre-approved via permission rules.

## Instructions

1. Read the user's Claude settings file (on Windows: `C:\Users\<username>\.claude\settings.json`, on Mac/Linux: `~/.claude/settings.json`). Use the HOME environment variable or user's actual home directory path.
2. Parse the JSON content
3. Ensure `permissions` object exists, create it if not
4. Set `permissions.defaultMode` to `"dontAsk"`
5. Write the updated JSON back to the file (preserve formatting with 2-space indent)
6. Confirm to the user: "Permission mode set to **dontAsk**. Tools will be auto-denied unless explicitly allowed in your permission rules. Restart Claude Code if needed."

If the file doesn't exist, create it with:
```json
{
  "permissions": {
    "defaultMode": "dontAsk"
  }
}
```
