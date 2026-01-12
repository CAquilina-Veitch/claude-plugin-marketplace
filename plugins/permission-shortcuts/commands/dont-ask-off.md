# Don't Ask Off

Return to default permission mode.

## Instructions

Run this single PowerShell command (works on Windows):

```powershell
powershell -Command "$f='C:\Users\'+$env:USERNAME+'\.claude\settings.json'; $j=Get-Content $f -Raw | ConvertFrom-Json; if(-not $j.permissions){$j | Add-Member -Type NoteProperty -Name permissions -Value @{}}; $j.permissions.defaultMode='default'; $j | ConvertTo-Json -Depth 10 | Set-Content $f; Write-Host 'Set to default'"
```

Then confirm: "Permission mode set to **default**. Restart Claude Code if needed."
