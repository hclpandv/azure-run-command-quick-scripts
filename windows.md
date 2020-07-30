## Windows Quick Run Commands via Azure Run Command Blade

### Get FQDN

```powershell
([System.Net.Dns]::GetHostByName(($env:computerName))).hostname
```

#### Get Free Disk Space

```powershell
Get-WmiObject win32_logicaldisk | Select-Object DeviceID, @{name="Total Size(GB)";expression={$_.Size / 1GB -as [int]}}, @{name="FreeSpace(GB)";expression={$_.FreeSpace / 1GB -as [int]}}
```

### Get Free memory

```powershell
Get-WmiObject Win32_OperatingSystem | select @{n="Total Memory(MB)";e={$_.TotalVisibleMemorySize / 1Mb}}, @{n='Free Memory(MB)';e={$_.FreePhysicalMemory / 1MB}}
```

#### Figure out who rebooted the server

```powershell
Get-EventLog -LogName System  | Where-Object {$_.Message -like "*restart*" } | select timewritten, Message | ft -Wrap
```
