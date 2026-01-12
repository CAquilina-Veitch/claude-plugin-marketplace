# Don't Ask Off

Return to default permission mode - prompts for new tools as normal.

## Instructions

1. Read the user's Claude settings file at `~/.claude/settings.json`
2. Parse the JSON content
3. Ensure `permissions` object exists, create it if not
4. Set `permissions.defaultMode` to `"default"`
5. Write the updated JSON back to the file (preserve formatting with 2-space indent)
6. Confirm to the user: "Permission mode set to **default**. You will be prompted for new tool permissions as normal. Restart Claude Code if needed."

If the file doesn't exist, create it with:
```json
{
  "permissions": {
    "defaultMode": "default"
  }
}
```
