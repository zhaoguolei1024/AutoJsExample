 # WebViewClient的使用方法.js
```
"ui";

ui.layout(
    <frame>
    <webview id="web" />
    </frame>
    )

var client = android.webkit.WebViewClient;

var t = new JavaAdapter(client, {
    onPageFinished: function(view, url) {
        toast("哈哈")
    }
})



ui.web.setWebViewClient(t);

ui.web.loadUrl("https://baidu.com")

toastLog(typeof(t));```
