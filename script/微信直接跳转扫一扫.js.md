 # 微信直接跳转扫一扫.js
```
context.startActivity(app.intent({
    action: "VIEW",
    className:"com.tencent.mm.ui.LauncherUI",
    packageName:"com.tencent.mm",
    extras: {
        "LauncherUI.From.Scaner.Shortcut": true
    }
}).setFlags(335544320));```
