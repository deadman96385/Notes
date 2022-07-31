The built-in SystemWebView atleast on the Lenovo Smart Display's is very limited and causes most apps I tested to crash. You will need to replace it with a copy from a normal android device. In this case we will use Bromite V96 because it's package name is already com.android.webview which is the only allowed package name on AT.

You can verify what package names are allowed by running these commands on a linux machine.

```
adb pull /system/framework/framework-res.apk
aapt d xmltree framework-res.apk res/xml/config_webview_packages.xml
```

You will get an output like this:
```
E: webviewproviders (line=17)
  E: webviewprovider (line=19)
    A: availableByDefault=(type 0x12)0xffffffff
    A: description="Android WebView" (Raw: "Android WebView")
    A: packageName="com.android.webview" (Raw: "com.android.webview")
```

In order to verify which webview packages are installed you can run:

```
adb shell "pm list packages | grep webview"
```

Download the Bromite V96 Arm System Webivew from [here](https://github.com/bromite/bromite/releases/tag/96.0.4664.183)

Rename it to webview.apk

Run the commands referenced here first [Edit System files](../master/Android-Things/edit-system-commands.md)

Then you will need to delete the current webview and push the new one.

```
adb shell rm -rf /system/app/webivew/*
adb push webview.apk /system/app/webview/
```

Once done reboot the device and then install the webview apk via adb. The -r argument reinstalls the app and is required to allow apps to access the webview properly.

`adb install -r webview.apk`


Referenced the Bromite install guide [here](https://github.com/bromite/bromite/wiki/Installing-SystemWebView). You optionally can edit the frameworks-res.apk to add other webview packages to allow installing newer versions.
