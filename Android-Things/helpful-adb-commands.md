Brings up the default launcher selector screen (If a launcher you try opens and then closes it is not supported by Android Things. You will need one that does not have Widget support. Like KISS Launcher)

```adb shell am start -a android.intent.action.MAIN -c android.intent.category.HOME```

Lists installed app package names

```adb shell pm list packages```

Change the -p to whichever package name you want to launch it emulates clicking the apps icon in launcher so some system apps don't support it.

```adb shell monkey -p PACKAGE_NAME -c android.intent.category.LAUNCHER 1```

Will launch the android things settings page

```adb shell monkey -p com.android.iotlauncher -c android.intent.category.HOME 1```

This will launch the google setupwizard/launcher

```adb shell monkey -p com.google.assistant.core -c android.intent.category.LAUNCHER 1```

Seems to soft reboot the android things system, but not actually reboot the device proper

```adb shell monkey -p com.google.android.apps.quartz -c android.intent.category.LAUNCHER 1```

Launches camera app

```adb shell am start -n com.android.camera2/com.android.camera.CameraActivity```

Force stop an app

```adb shell am force-stop PACKAGE_NAME```

Install apk via adb with all permissions in the manifest granted

```adb install -g APK_FILE```

Install apk via adb, reinstall app while keeping data

```adb install -r APK_FILE```

Allow an app to disable battery optimizations and run in the background

```adb shell dumpsys deviceidle whitelist +io.homeassistant.companion.android.minimal```

Allows draw over other apps without settings

```adb shell pm grant com.fb.fluid android.permission.SYSTEM_ALERT_WINDOW```

Enable accessibility options for an app's service

```adb shell settings put secure enabled_accessibility_services com.fb.fluid/.MainAccessibilityService```

Check currently enabled accessibilites

```adb shell settings get secure enabled_accessibility_services```

Grant accessibility settings for an app you don't know the service name of

https://forum.xda-developers.com/t/app-firetv-accessibility-permissions-manager-for-firetv-devices.4144057/

or

Look through this commands output for the activity

```adb shell pm dump PACKAGE_NAME```

Launches Magisk

```adb shell monkey -p com.topjohnwu.magisk -c android.intent.category.LAUNCHER 1```
