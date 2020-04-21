# 开发准备
华为HMS的kit开发前准备工作都差不多，无非就是添加maven依赖，引入SDK。

## 在项目级gradle里添加华为maven仓
增量添加如下maven地址：
```java
buildscript {
    repositories {        
        maven {url 'http://developer.huawei.com/repo/'}
    }    }allprojects {
    repositories {       
        maven { url 'http://developer.huawei.com/repo/'}
    }}
```

## 在应用级的build.gradle里面加上SDK依赖
把人脸识别的SDK和基础SDK引入：
```java
dependencies{ 
  // 引入基础SDK 
  implementation 'com.huawei.hms:ml-computer-vision:1.0.2.300' 
  // 引入人脸检测能力包 
  implementation 'com.huawei.hms:ml-computer-vision-face-recognition-model:1.0.2.300'   
 }
```

## 在AndroidManifest.xml文件里面增量添加模型自动下载
这个主要是用来模型更新的，后面算法有了优化，可以自动下载到手机里面更新
```java
<manifest    
   <application  
       <meta-data                     
           android:name="com.huawei.hms.ml.DEPENDENCY"          
           android:value= "face"/>        	        
   </application></manifest> 
```

## 在AndroidManifest.xml文件里面申请相机和存储权限
```java
<!--相机权限--><uses-permission android:name="android.permission.CAMERA" /><!--使用存储权限--><uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```
