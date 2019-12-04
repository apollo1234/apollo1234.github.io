## 确定 App(Activity) 的启动者

```shell
% adb logcat | grep -E "ActivityManager: START" --color=always
I ActivityManager: START u0 {act=android.intent.action.MAIN
cat=[android.intent.category.HOME] flg=0x10000000 hwFlg=0x10
cmp=com.huawei.android.launcher/.unihome.UniHomeLauncher (has extras)} from uid 10070
```
from uid 10070 确定是这个应用启动的

```
% adb shell ps | grep 10070
% adb shell ps | grep launcher
u0_a70        2207   620 4979992 156312 0                   0 S com.huawei.android.launcher
% adb shell id u0_a70
```

#### u0_a70
- u0 默认的手机第一个用户（可以通过设置里面的多用户新增和切换
- a app
- 70 第70个应用

#### 参考
[在 Android 中如何确定 App(Activity) 的启动者
](https://droidyue.com/blog/2019/12/01/android-uid-process-name/)

---

