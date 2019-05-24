# 1、back键退出APP不销毁activity
重写onkeydown()
```
 if(keyCode == KeyEvent.KEYCODE_BACK){
    moveTaskToBack(true);
    return true;
 }
``` 
# 2、沉浸式状态栏

需要适配v19、v21

创建values-v19文件夹
新建style
```
 <style name="TranslucentTheme" parent="Theme.AppCompat.Light.NoActionBar">
        <item name="android:windowTranslucentStatus">true</item>
        <item name="android:windowTranslucentNavigation">false</item>
    </style>
   ``` 
创建values-v25文件夹
新建style

```
<style name="TranslucentTheme" parent="Theme.AppCompat.Light.NoActionBar">
        <item name="android:windowTranslucentStatus">false</item>
        <item name="android:windowTranslucentNavigation">false</item>
        <!--Android 5.x开始需要把颜色设置透明，否则导航栏会呈现系统默认的浅灰色-->
        <item name="android:statusBarColor">@android:color/transparent</item>
</style>
```
然后在activity的oncreate（）中设置flag，要同时使用
getWindow().getDecorView().setSystemUiVisibility(View.SYSTEM_UI_FLAG_LAYOUT_STABLE |
                View.SYSTEM_UI_FLAG_LAYOUT_FULLSCREEN);
