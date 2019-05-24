# androidTip
android知识点


根据图片的名字获取对应的资源ID

一、   getResources().getIdentifier(String name,String defType,String defPackage) 
···
public int  getResource(String imageName){
     int resId = getResources().getIdentifier(imgName, "drawable",getPackageName());
     //如果在drawable下没找到imgName,将会返回0
     return resId;
}
···
二、利用反射
···
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
···
