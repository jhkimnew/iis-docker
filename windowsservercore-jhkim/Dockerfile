# escape=`
FROM jhkimaks.azurecr.io/iis_test_client:iis_client_any

RUN powershell.exe -command "Get-ItemProperty 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion'"

RUN powershell -Command `
    Add-WindowsFeature Web-Server; `
    Invoke-WebRequest -UseBasicParsing -Uri "https://dotnetbinaries.blob.core.windows.net/servicemonitor/2.0.1.10/ServiceMonitor.exe" -OutFile "C:\ServiceMonitor.exe"

EXPOSE 80

ENTRYPOINT ["C:\\ServiceMonitor.exe", "w3svc"]
#ENTRYPOINT dir c:\
#ENTRYPOINT ["cmd.exe", "/c", "xcopy c:\\containerTest2 c:\\temp /s"]