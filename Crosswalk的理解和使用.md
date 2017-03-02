# Crosswalk的理解和使用

## 个人理解

Crosswalk是作为Web端应用移植到移动端的一种解决方案。较于Android原生WebView有更流畅的体验，并且可以和Cordova结合，使用拓展的API调用设备原生的功能。

### 官方解释

Crosswalk是一款为HTML应用提供运行时环境的开源项目，同时它也扩展了一些Web平台的新特性。
Web平台已经拥有很多优势，例如从简单的云服务集成到灵活的用户界面元素。当前随其对移动性能和设备API持续增长的关注，Web平台也越来越具有吸引力。
然而对于很多开发者而言，由于基础功能仍然缺失，导致时至今日采用Web平台依旧困难重重。
**使用Crosswalk项目，可以改变这种情况**
通过使用Crosswalk项目，应用开发人员可以：

* 使用所有现代浏览器可提供的特性：HTML5,CSS3,JavaScript。
* 访问主流和新兴的Web标准。
* 使用主流浏览器无法获取的实验性API。
* 通过部署自己的运行时环境来控制应用的升级周期。
* 通过为应用添加自定义扩展，来使用并未通过Crosswalk或公共Web标准暴露的系统平台功能。

## 使用

Crosswalk支持Android/iOS/Windows/Linux平台下创建应用。下面是Android平台的开发步骤。

### 系统配置

1. 安装工具
	* Java JDK
	* Apache Ant
	* Android SDK
	* NPM
	* Crosswalk App Tools

	`npm install -g crosswalk-app-tools`
	
2. 验证环境
	`crosswalk-app check android`
	
	如果lzma没有安装，会报如下的ERROR，您可以忽略这个错误。
	`ERROR: Checking for lzma... null`
	
### 编译应用
1. 创建Web工程
	* 使用已有的Web工程
	* 使用crosswalk命令创建
	* 手动创建简单的web工程
	
	工程中index.html作为程序的入口，manifest.json包含了应用的元数据。
2. 编译应用

 `crosswalk-pkg <含有manifest文件的目录>`
 
### 安装应用

`adb install -r com.abc.myapp-0.1-debug.x86.apk`

### 远程调试

安装应用后运行，在主机打开Chrome浏览器输入"chrome://inspect"将会显示已经挂载的设备。点击“inspect”打开应用，就可以使用Chrome dev tools进行调试。

### 安卓扩展程序

使用Java编写的Crosswalk安装扩展程序，主要包括两部分：

1. 一个Crosswalk插件程序
2. 一个Html5应用程序

(未完待续)

### 嵌入模式

当您的应用中有大量的Java代码，但是又想要使用Web技术来写UI界面时，我们才推荐您使用Embedding API。
[地址](https://download.01.org/crosswalk/releases/crosswalk/android/maven2/org/xwalk/xwalk_core_library/23.53.589.4/)下载后导入到项目。
(未完待续)

## 其他

### Cordova

随着Cordova Android 4.0.0引入了对插入式webview的支持，现在你可以方便地在你的Cordova应用上使用Crosswalk的webview。通过使用Crosswalk的webview插件，开发者可以享用远程调试的功能，前沿的HTML5特性，例如WebGL, WebAudio和WebRTC，以及在包括Android 4.0 Ice Cream Sandwich(ICS)在内的Android设备上性能的显著提升。

### 共享模式和下载模式

默认情况下，Crosswalk运行时是被嵌入到你的应用内，并且包含在APK中。相反，“共享模式”和“下载模式”在编译应用时不需要运行时，但是在后面运行的时候必须下载相关的运行时环境。

* 共享模式

“共享模式”允许多个Crosswalk应用共享一个运行时环境。

* 下载模式

独享Crosswalk运行时，可以控制运行时的生命周期。



 






