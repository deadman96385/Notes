This requires that you are AVB and BL unlocked on your Android Things powered device. The following commands will disable the userspace security restrictions allowing you to edit files on the system.

```adb root
adb disable-verity
adb reboot
adb root
adb remount
adb shell setenforce 0 
```

Verity will be disabled until you factory reset or run `adb enable-verity`. You will need to run remount, and setenforce 0 on each reboot or have a script in the ramdisk run them for you.
