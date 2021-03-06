 # 获取app安装时间.js
```
importClass(android.content.pm.PackageManager)
installed = context.getPackageManager().getPackageInfo(context.getPackag‌​eName(), 0).firstInstallTime
log(installed)
```
