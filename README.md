# android知识点

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
