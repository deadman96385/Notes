# Notes on using WSA for Android Studio development

Here is an example batch script that does the following:
1. Launches Android studio
2. Launches the WSA subsystem via either your app directly or through the built in settings app
3. Uses the default android studio adb server to connect to the WSA instance for instant recognition in studio

![image](https://user-images.githubusercontent.com/2042793/218284168-8f69ff72-94a3-4bb5-b9f3-c0e852ea8d51.png)

Notes: 
  Replace the com.example.program with your already installed android package id or comment it out and uncomment the settings line. 
```batch
@echo off

:: Launch Android Studio
START /B "" "%ProgramFiles%\Android\Android Studio\bin\studio64.exe"

:: Finds the package name of your WSA package (Changes based on version)
PowerShell -nologo -NoProfile -command "Get-AppXPackage *WindowsSubsystemForAndroid* | Select-Object PackageFullName" > tempfile.txt
For /f "usebackqdelims=" %%A in (tempfile.txt) Do Set InstanceID=%%A

:: Launches already installed application, Note you need to update the package name
START /B "" "%ProgramFiles%\WindowsApps\%InstanceID%\WsaClient\WsaClient.exe" /launch wsa://com.example.program

:: Launches the Windows subsystem for android settings application using the preinstalled URL protocol handler
:: start wsa-settings:\\

:: Connect to the WSA device via local network using the Android Studio default adb for seamless connection
START /WAIT /B "" %LocalAppData%\Android\Sdk\platform-tools\adb.exe connect 127.0.0.1:58526

del tempfile.txt

```

