# Don't Ask On

Enable "don't ask" mode - auto-deny tools unless pre-approved.

## Instructions

Run this single PowerShell command (works on Windows):

```powershell
powershell -Command "$f='C:\Users\'+$env:USERNAME+'\.claude\settings.json'; $j=Get-Content $f -Raw | ConvertFrom-Json; if(-not $j.permissions){$j | Add-Member -Type NoteProperty -Name permissions -Value @{}}; $j.permissions.defaultMode='dontAsk'; $j | ConvertTo-Json -Depth 10 | Set-Content $f; Write-Host 'Set to dontAsk'"
```

Then confirm: "Permission mode set to **dontAsk**. Restart Claude Code if needed."
