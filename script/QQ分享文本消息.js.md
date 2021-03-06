 # QQ分享文本消息.js
```
var content = rawInput("请输入要发生的消息");
app.startActivity({
    action: "android.intent.action.SEND",
    type: "text/*",
    extras: {
        "android.intent.extra.TEXT": content
    },
    packageName: "com.tencent.mobileqq",
    className: "com.tencent.mobileqq.activity.JumpActivity"
});```
