## Windows Quick Run Commands via Azure Run Command Blade

1. Get Free Disk Space

```powershell
Get-WmiObject win32_logicaldisk | Select-Object DeviceID, @{name="FreeSpace(GB)";expression={$_.FreeSpace / 1GB -as [int]}}, @{name="Size(GB)";expression={$_.Size / 1GB
 -as [int]}}
```
