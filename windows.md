## Windows Quick Run Commands via Azure Run Command Blade

#### Get Free Disk Space

```powershell
Get-WmiObject win32_logicaldisk | Select-Object DeviceID, @{name="Total Size(GB)";expression={$_.Size / 1GB -as [int]}}, @{name="FreeSpace(GB)";expression={$_.FreeSpace / 1GB -as [int]}}
```
