本文主要介绍如何快速地将腾讯云即时通信 IM SDK 集成到您的项目中，只要按照如下步骤进行配置，就可以完成 SDK 的集成工作。
## 开发环境要求
- JDK 1.6。
- Android 4.0（SDK API 14）及以上系统。

## 集成 SDK（aar）
您可以选择使用 Gradle 自动加载的方式，或者手动下载 aar 再将其导入到您当前的工程项目中。

### 方法一：自动加载（aar）
IM SDK 已经发布到 jcenter 库，您可以通过配置 gradle 自动下载更新。
只需要用 Android Studio 打开需要集成 SDK 的工程（本文以 [TIM SDK Demo](https://github.com/tencentyun/TIMSDK/tree/master/Android) 为例），然后通过如下三个步骤修改 app/build.gradle 文件，就可以完成 SDK 集成：

- **第一步：添加 SDK 依赖**

 找到 tuikit lib 工程的 build.gradle，在 dependencies 中添加 IM SDK 的依赖。
```
dependencies {
		api 'com.tencent.imsdk:imsdk:版本号'
}
```
>“版本号”应替换为 SDK 的实际版本号，建议使用 [最新版本]( https://github.com/tencentyun/TIMSDK/tree/master/Android/tuikit/libs)。
>以版本号是`4.0.10`为例：
>```
dependencies {
		api 'com.tencent.imsdk:imsdk:4.0.10'
}
```
>
 ![](https://main.qcloudimg.com/raw/e28438bb2be46cc188b217d26b920108.png)
- **第二步：指定 App 使用架构**
在 defaultConfig 中，指定 App 使用的 CPU 架构（从 IM SDK 4.3.118 版本开始支持 armeabi-v7a，arm64-v8a，x86，x86_64）：
```
   defaultConfig {
        ndk {
            abiFilters "armeabi-v7a"
        }
    }
```

- **第三步：同步 SDK**
单击【Sync Now】按钮，如果您的网络连接 jcenter 没有问题，SDK 就会自动下载集成到工程里。
![](https://main.qcloudimg.com/raw/a75e143229c36e509811261942c29e88.png)


### 方法二：手动下载（aar）
如果您的网络连接 jcenter 有问题，也可以手动下载 SDK 集成到工程里：
- **第一步：下载 IM SDK**
在 Github 上可以下载到最新版本的 [IM SDK](https://github.com/tencentyun/TIMSDK/tree/master/Android/tuikit/libs)。

- **第二步：拷贝 IM SDK 到工程目录**
将下载到的 aar 文件拷贝到 tuikit lib工程的 **/libs** 目录下：
![](https://main.qcloudimg.com/raw/6c68a70c15ce85d51ac6678234fcfe1b.png)

- **第三步：指定本地仓库路径**
在工程根目录下的 build.gradle 中，添加 **flatDir**，指定本地仓库路径：
![](https://main.qcloudimg.com/raw/61b30f5e1c9cca868c1a0220231ffcde.png)

- **第四步：添加 IM SDK 依赖**
由于 tuikit 是以 lib 工程导入的，需要在 app/build.gradle 和 tuikit/build.gradle 中，添加引用 aar 包的代码。
 ![](https://main.qcloudimg.com/raw/53d530fd5ce0b66c88e678250b3d9386.png)
 ![](https://main.qcloudimg.com/raw/5175545f0e583fba7b7099ee94c721fa.png)
- **第五步：指定 App 使用架构**
在 app/build.gradle的defaultConfig 中，指定 App 使用的 CPU 架构（从 IM SDK 4.3.118 版本开始支持 armeabi-v7a，arm64-v8a，x86，x86_64）：
```
defaultConfig {
            ndk {
                abiFilters "armeabi-v7a"
            }
    }
```

- **第六步：同步 SDK**
单击 Sync Now 按钮，完成 IM SDK 的集成工作。


## 集成 SDK（jar & so）
如果您不想集成 aar 库，也可以通过导入 jar 和 so 库的方式集成 IM SDK：

- **第一步：下载解压 IM SDK**
在 Github 上可以 [下载](https://github.com/tencentyun/TIMSDK/tree/master/Android/tuikit/libs) 到最新版本的 aar 文件，解压：
![](https://main.qcloudimg.com/raw/da04237dcb53c1953667dfc9d43d6d7e.png)
解压后的目录里面主要包含 jar 文件和 so 文件夹，把其中的 **classes.jar** 重命名成 **imsdk.jar** ，文件清单如下：
![](https://main.qcloudimg.com/raw/8ec9ecd08e9451b907a50bbc96c99607.png)

- **第二步：拷贝 SDK 文件到工程目录**
将重命名后的 jar 文件和 armeabi-v7a 文件夹拷贝到 tuikit/libs 目录下：
![](https://main.qcloudimg.com/raw/83c582b1c8ccfe989e4f0694f06c03f1.png)

- **第三步：引用 jar 库**
由于 tuikit 是以 lib 工程导入的，需要在 app/build.gradle 和 tuikit/build.gradle 中，添加引用 jar 库的代码。
 - 在 app/build.gradle 中添加引用jar 库的代码：
![](https://main.qcloudimg.com/raw/83e5ce182acc734dd6d5674a18cb12be.png)
 - 在 tuikit/build.gradle 中添加引用jar 库的代码：
![](https://main.qcloudimg.com/raw/637afa9cebeb0b3b7506c414fef1becb.png)


- **第四步：引用 so 库**
在 tuikit/build.gradle 中，添加引用 so 库的代码：
![](https://main.qcloudimg.com/raw/e48d628afa3f97e663f8e6c810badb01.png)

- **第五步：指定 App 使用架构**
在 app/build.gradle 的 defaultConfig 中，指定 App 使用的 CPU 架构（从 IM SDK 4.3.118 版本开始支持 armeabi-v7a，arm64-v8a，x86，x86_64）：
```
   defaultConfig {
        ndk {
            abiFilters "armeabi-v7a"
        }
    }
```

- **第六步：同步 SDK**
单击【Sync Now】，完成 IM SDK 的集成工作。

## 配置 App 权限
在 AndroidManifest.xml 中配置 App 的权限，IM SDK 需要以下权限：

```

	<uses-permission android:name="android.permission.INTERNET" />
	<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
	<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
```

## 设置混淆规则
在 proguard-rules.pro 文件，将 IM SDK 相关类加入不混淆名单：

```
-keep class com.tencent.** { *; }
```
