# libuvccamera

---
重新编译uvccamer.os库


# 使用
1、将uvccamera添加到你的工程根目录

2、`./settings.gradle` 添加 `include ':uvccamerasdk'`

3、`app/src/main/AndroidManifest.xml` 添加
```xml
<uses-permission android:name="android.permission.CAMERA" />
```

4、`app/build.gradle`
```gradle
android {
    compileSdkVersion 27
    buildToolsVersion "27.0.1"

    defaultConfig {
        applicationId "com.muzilee.demo"
        minSdkVersion 18
        targetSdkVersion 27
        versionCode 1
        versionName "1.0"
        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"

        ndk { abiFilters "armeabi" }
        externalNativeBuild {
            cmake {
                cppFlags ""
                abiFilters 'armeabi'
            }
        }
    }

    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
    }
}

dependencies {
    implementation fileTree(include: ['*.jar'], dir: 'libs')
    // ...
    implementation project(':uvccamerasdk')
    implementation 'com.bulong.rudeness:rudeness:latest.release@aar'
}

```

5、go to happy!!!
