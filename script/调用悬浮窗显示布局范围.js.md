 # 调用悬浮窗显示布局范围.js
```
auto.waitFor();
var root = runtime.accessibilityBridge.getRootInActiveWindow();
var node = com.stardust.view.accessibility.NodeInfo.capture(root);
//或者LayoutHierarchyFloatyWindow
var window = new com.stardust.scriptdroid.ui.floating.layoutinspector.LayoutBoundsFloatyWindow(node);
ui.run(function(){
    com.stardust.enhancedfloaty.FloatyService.addWindow(window);
});```
