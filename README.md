# CodeSnippets
## Python
format number into hexadecimal representation with padding zero to have a nice output:
```python
print ("ID: 0x{:0>2x}".format((123))) # '0' padding with zeros, '>' right align, 'x' hexadecimal
```
see also: https://realpython.com/python-formatted-output/

some file handling:
```python
fPath = r'file.txt'
with open(fPath,'r') as f:
    fContent = f.readlines()
```

reverse a string:
```python
"Hello World!"[::-1]
```
### other
let start powershell in the right python environment:
```
conda init powershell
```
## Powershell
startMe.bat:

starts the powershell and directly jumps into a defined directory
```cmd
powershell.exe -noexit -command "cd d:\temp"
```

shorten the command prompt via profile settings

(e.g. C:\Users\username\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```cmd
function prompt {'PS ' + $(Get-Location | Split-Path -Leaf) + ">"}
```


```cmd
# adapt/modify the directories for National Instruments applications/drivers for additional exmaples and documentation
# the default path: "C:\Users\Public\Documents\National Instruments"

# draft

$newPath = "C:\Program Files (x86)\National Instruments\Shared\Documents\"

# not sure, if it has to be created in advance:
New-Item -ItemType Directory -Path $newPath

# parameters/pathes before/now:
Get-ItemProperty -Path "Registry::HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\National Instruments\Common\Installer" -Name NIPUBDOCSDIR
Get-ItemProperty -Path "Registry::HKEY_LOCAL_MACHINE\SOFTWARE\National Instruments\Common\Installer" -Name NIPUBDOCSDIR


# set new pathes:
Set-ItemProperty -Path "Registry::HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\National Instruments\Common\Installer" -Name NIPUBDOCSDIR -Value $newpath
Set-ItemProperty -Path "Registry::HKEY_LOCAL_MACHINE\SOFTWARE\National Instruments\Common\Installer" -Name NIPUBDOCSDIR -Value $newpath

# check:
Get-ItemProperty -Path "Registry::HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\National Instruments\Common\Installer" -Name NIPUBDOCSDIR
Get-ItemProperty -Path "Registry::HKEY_LOCAL_MACHINE\SOFTWARE\National Instruments\Common\Installer" -Name NIPUBDOCSDIR
```
```cmd
# -----------------------------------------
function Get-LargestFile {
	 param (
	 [Parameter(Mandatory=$true)]
	 [string]$Path
	 )
	
	 $largestFile = Get-ChildItem -Path $Path -File | Sort-Object -Property Length -Descending | Select-Object -First 1
	
	 return $largestFile
}
# use:
$largestFile = Get-LargestFile -Path "C:\Pfad\zum\Verzeichnis"
```




## ESP
```c
#include <Arduino.h>
#if defined(ESP8266)
  /* ESP8266 Dependencies */
  #include <ESP8266WiFi.h>
  #include <ESPAsyncTCP.h>
  #include <ESPAsyncWebServer.h>
#elif defined(ESP32)
  /* ESP32 Dependencies */
  #include <WiFi.h>
  #include <AsyncTCP.h>
  #include <ESPAsyncWebServer.h>
#endif
```

