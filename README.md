# android知识点

```
def getVersionCode() {
    def versionFile = file('version.properties')
    if (versionFile.canRead()) {
        Properties versionProps = new Properties()
        versionProps.load(new FileInputStream(versionFile))
        def versionCode = versionProps['VERSION_CODE'].toInteger()
        def runTasks = gradle.startParameter.taskNames
        println("runTasks------$runTasks")
        //仅在assembleAppDebug任务是增加版本号
        if ('assembleAppDebug' in runTasks || ':app:assembleLightningDebug' in runTasks) {
            versionProps['VERSION_CODE'] = (++versionCode).toString()
            versionProps.store(versionFile.newWriter(), null)
        }
        return versionCode
    } else {
        throw new GradleException("Could not find version.properties!")
    }
}
```

## 调试手机webview
```
在Chrome浏览器输入 Chrome://inspect
```

# 根据图片的名字获取对应的资源ID

一、   getResources().getIdentifier(String name,String defType,String defPackage) 
```
public int  getResource(String imageName){
     int resId = getResources().getIdentifier(imgName, "drawable",getPackageName());
     //如果在drawable下没找到imgName,将会返回0
     return resId;
}
```
二、利用反射
```
public int  getResource(String imageName){
    Class drawable = R.drawable.class;
        Field field = null;
        int r_id;
        try {
            field = drawable.getField(imageName);
            r_id = field.getInt(field.getName());
        } catch (Exception e) {
            r_id = R.drawable.ic_head;
            Log.e("ERROR", "PICTURE NOT　FOUND！");
        }
        return r_id;
}
```

# 判断是debug 还是release

```
public static boolean isApkInDebug(Context context) {
   try {
       ApplicationInfo info = context.getApplicationInfo();
       return (info.flags & ApplicationInfo.FLAG_DEBUGGABLE) != 0;
   } catch (Exception e) {
       return false;
   }
}
```

# 禁止屏幕锁屏

## 方法一：
```
getWindow().setFlags(WindowManager.LayoutParams.FLAG_KEEP_SCREEN_ON, WindowManager.LayoutParams.FLAG_KEEP_SCREEN_ON);
setContentView(R.layout.main);  
```
## 方法二
```
@Override  
protected void onResume() {  
     super.onResume();  
     pManager = ((PowerManager) getSystemService(POWER_SERVICE));  
     mWakeLock = pManager.newWakeLock(PowerManager.SCREEN_BRIGHT_WAKE_LOCK  | PowerManager.ON_AFTER_RELEASE, TAG);  
     mWakeLock.acquire();  
}  

@Override  
protected void onPause() {  
     super.onPause();  

     if(null != mWakeLock){  
          mWakeLock.release();  
     }  
}  
```


# Android项目打包遇com.android.builder.internal.aapt.v2.Aapt2Exception: AAPT2 error

```
在app的build.gradle中添加以下配置：

aaptOptions.cruncherEnabled = false  
aaptOptions.useNewCruncher = false 

```

```
Android平台上录制视频时，如果是横屏录制（手机逆时针旋转90度），则录制的视频时不带角度的。
如果是竖屏录制（正常的拿手机的姿势），此时的录制的视频的旋转角度是90度。
如果再旋转90度，此时一般音量键和关屏键朝下，此时的视频的旋转角度是180。
以此类推。所以在手机上的视频一般会有4中角度的视频，播放时，要对视频资源进行旋转后在进行播放。

一般而言，带角度的视频和不带角度的视频，数据帧里面的宽和高都是一样的（如果分辨率一样）。
以 720P 的分辨率来说，不论是横屏还是竖屏，或者其他角度，录制的视频分辨率都是 1280X720，
而不是 720X1280 或者其他，所以是无法从宽和高来判断视频的旋转角度的。
要获取视频的旋转角度，只能从视频的元数据里面来获取.
```
