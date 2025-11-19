# sharing-print-fix "0x0000011b"/“Cannot connect to printer”/“Operation failed with error 0x0000007c”
This contains a simple batch script to fix network printing issues caused by the RpcAuthnLevelPrivacyEnabled policy introduced in Windows updates (especially on Windows 10 &amp; 11).  Some printers or shared printers may fail to connect when this policy is enabled. This script disables the value and restores normal printing behavior



## 🔧 What This Script Does

The batch script:

1. Adds or modifies the registry key:
HKLM\SYSTEM\CurrentControlSet\Control\Print


2. Sets the following DWORD value:



RpcAuthnLevelPrivacyEnabled = 0


3. Prompts the user to restart the PC to apply the fix.

---

## 📜 Script Contents

```bat
@echo off
echo add registry
reg add "HKLM\SYSTEM\CurrentControlSet\Control\Print" /v RpcAuthnLevelPrivacyEnabled /t REG_DWORD /d 0 /f
echo Restart your Pc
pause
```
🚀 How to Use

Download file from this repository

Right-click the .bat file.

Select Run as Administrator.

Restart your PC after the script completes.

❓ Why This Fix Works

Some Windows updates enforce higher RPC authentication levels for printing services.
Older printer drivers or network-shared printers may not support this requirement, resulting in issues like:

Printer cannot connect

RPC errors

Shared printer not detected

Printing fails unexpectedly

By setting RpcAuthnLevelPrivacyEnabled = 0, Windows relaxes this policy and restores compatibility.

⚠️ Disclaimer

Editing the Windows registry may affect system behavior.
Only run this script if you're facing related printer/RPC authentication issues.
Use at your own risk.
