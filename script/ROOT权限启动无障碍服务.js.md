 # ROOT权限启动无障碍服务.js
```
var pref = android.preference.PreferenceManager.getDefaultSharedPreferences(context);
pref.edit().putBoolean("key_enable_accessibility_service_by_root", true).commit();```
