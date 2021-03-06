 # 判断屏幕方向是横屏还是竖屏.js
```
var a = (context.resources.configuration.orientation);
if (a === 1) {
    toastLog("这是竖屏!!");
} else {
    toastLog("这是横屏!!");
}```
