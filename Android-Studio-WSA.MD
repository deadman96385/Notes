# Notes on using WSA for Android Studio development

Here is an example batch script that does the following:
1. Launches Android studio
2. Launches the WSA subsystem either your app directly or optionally the built in settings app
3. Uses the default android studio adb server to connect to the WSA instance for instant recognition in studio

![image](https://user-images.githubusercontent.com/2042793/218284168-8f69ff72-94a3-4bb5-b9f3-c0e852ea8d51.png)

Notes: 
1. Replace the com.example.program with your already installed android package id. 
2. Update the WSA install folder location most likely (Run this command `shell:AppsFolder` to see the hidden windows apps folder to get it easily)
```
@echo off

:: Launch Android Studio
START /B "" "%ProgramFiles%\Android\Android Studio\bin\studio64.exe"

:: Launch an already installed application
START /B "" "%ProgramFiles%\WindowsApps\MicrosoftCorporationII.WindowsSubsystemForAndroid_2301.40000.4.0_x64__8wekyb3d8bbwe\WsaClient\WsaClient.exe" /launch wsa://com.example.program

:: Launch the Windows subsystem for Android settings application (Uncomment)
:: START /B "" %ProgramFiles%\WindowsApps\MicrosoftCorporationII.WindowsSubsystemForAndroid_2301.40000.4.0_x64__8wekyb3d8bbwe\WsaSettings.exe

:: Connect to the WSA device via local network using the Android Studio default adb for seamless connection
START /WAIT /B "" %LocalAppData%\Android\Sdk\platform-tools\adb.exe connect 127.0.0.1:58526
```

