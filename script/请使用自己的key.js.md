 # 请使用自己的key.js
```
auto();

function 新消息() {
    {

}
var msgcounts = id("listView1").findOne();
var a = msgcounts.child(msgcounts.childCount() - 1);
var b = a.child(a.childCount() - 1).text();
var b1 = a.child(a.childCount() - 1).bounds();
if (b1.centerX() < 530) {
log(b);
return b;
}
}
function 得到回复(message) {
var url = "http://www.tuling123.com/openapi/api";
var r = http.postJson(url, {
key: "这里填你的key",
info: message,
});
return r.body.json().text;
}

function 发送回复() {
var msgcounts = id("listView1").findOne();
var a = msgcounts.child(msgcounts.childCount() - 1);
var b = a.child(a.childCount() - 1).text();
var b1 = a.child(a.childCount() - 1).bounds();
waitForActivity("com.tencent.mobileqq.activity.SplashActivity", [period = 200])
if (id("listView1").exists() && id("input").exists()) {
if (b1.centerX() < 530) {
setText("[马化腾]" + 得到回复(新消息()));
click("发送");
}
}
}
while (1) {
发送回复();
sleep(500);
}```
