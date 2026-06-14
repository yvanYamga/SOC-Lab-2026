============================================================================

Download Sysmon 
Sysmon : https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon

============================================================================

###########################################################################

Folder content:
- Eula.txt
- sysmon.exe
- sysmon64.exe
- sysmon64a.exe
*
start installation for win64

.\sysmon64.exe -accepteula -i sysmonconfig-export.xml

###########################################################################

Debbug 
 
Error: Failed to open xml configuration: sysmonconfig-export

Download xml file

Invoke-WebRequest -Uri "https://raw.githubusercontent.com/SwiftOnSecurity/sysmon-config/master/sysmonconfig-export.xml" -OutFile "C:\sysmonconfig.xml"

###########################################################################

Verification sysmon running

Get-Process sysmon*

######
