 # 8.0打开关闭网络usb共享.js
```
app.startActivity({
    packageName: "com.android.settings",
    className: "com.android.settings.Settings$TetherSettingsActivity"
});
waitForActivity("com.android.settings.Settings$TetherSettingsActivity")
click("USB 共享网络");```
