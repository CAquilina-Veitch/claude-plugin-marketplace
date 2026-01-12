# Auth All

Bypass all permission prompts by setting `defaultMode` to `bypassPermissions`.

## Instructions

1. Read the user's Claude settings file at `~/.claude/settings.json`
2. Parse the JSON content
3. Ensure `permissions` object exists, create it if not
4. Set `permissions.defaultMode` to `"bypassPermissions"`
5. Write the updated JSON back to the file (preserve formatting with 2-space indent)
6. Confirm to the user: "Permission mode set to **bypassPermissions**. All permission prompts will be skipped. Restart Claude Code if needed."

If the file doesn't exist, create it with:
```json
{
  "permissions": {
    "defaultMode": "bypassPermissions"
  }
}
```
