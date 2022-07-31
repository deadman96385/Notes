You will need to install the Home assistant Minimal version because the normal version has dependecies on Google play services for firebase notifications for non-local notifications. You also will need to replace the webview with one from normal android using this [guide](../Android-Things/replace-webview.md)

Download the minimal version of apk from the Github release page for the android companion app [here](https://github.com/home-assistant/android/releases)

Install the app via adb with the -g argument to allow all permissions by default for the app due to us not having a way to control them later.

```adb install -g home-assistant-minimal.apk```

Optionally you can allow the Home Assistant app to run in the background (I am not sure if this is required on Android Things, but it doesn't hurt to do it)

```adb shell dumpsys deviceidle whitelist +io.homeassistant.companion.android.minimal```

You can now launch the app via a launcher or this adb command

```adb shell am start -n io.homeassistant.companion.android.minimal/io.homeassistant.companion.android.launch.LaunchActivity```

To enter text for the login field either install a keyboard app or you can run the following adb command:

```adb shell input text TEXT_GOES_HERE```
