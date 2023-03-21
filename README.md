# libuvccamera

---
重新编译uvccamer.os库


# 使用
1、将uvccamera添加到你的工程根目录

2、`./settings.gradle` 添加 `include ':uvccamerasdk'`

3、`./build.gradle`
```gradle
allprojects {
    repositories {
        maven { url 'http://maven.aliyun.com/nexus/content/groups/public' }
        maven { url 'https://dl.google.com/dl/android/maven2/' }
        google()
        jcenter()
        maven {
            url "https://jitpack.io"
        }
    }
}
```

4、`app/src/main/AndroidManifest.xml` 添加
```xml
<uses-permission android:name="android.permission.CAMERA" />
```

5、`app/build.gradle`
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
}

```

5、go to happy!!!
