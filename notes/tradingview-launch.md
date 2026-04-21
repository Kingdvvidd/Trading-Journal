# TradingView Launch Command (Windows MSIX Install)

The `tv_launch` MCP tool and the default batch script fail on MSIX (Windows Store) installs because the `WindowsApps` directory is protected.

## Working Launch Command

```powershell
powershell.exe -Command "Stop-Process -Name TradingView -Force -ErrorAction SilentlyContinue; Start-Sleep 2; Start-Process 'C:\Program Files\WindowsApps\TradingView.Desktop_3.0.0.7652_x64__n534cwy3pjxzj\TradingView.exe' -ArgumentList '--remote-debugging-port=9222'"
```

## Verify CDP is Live

```bash
curl -s http://localhost:9222/json/version
```

## Notes

- Port `9222` is the default Chrome DevTools Protocol (CDP) port used by the TradingView MCP server.
- Run the PowerShell command in a terminal with standard user permissions (no admin required).
- TradingView install path: `C:\Program Files\WindowsApps\TradingView.Desktop_3.0.0.7652_x64__n534cwy3pjxzj\TradingView.exe`

