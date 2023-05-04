# RFID

> 致梦RFID库

------------

[![](https://jitpack.io/v/ceneax/QRScan.svg)](https://jitpack.io/#ceneax/QRScan)

------------

### 说明



### 引入依赖

##### 第一步：
项目根目录的 **build.gradle** 文件中加入以下代码：



##### 第二步：
在项目模块中的 **build.gradle** 文件中加入以下代码：

```Groovy
dependencies {
    ...
    implementation 'com.github.ceneax:RFID:需要引入的版本号'
}
```

### 开始使用

为了方便使用，该库内置了一个符合大众场景使用的扫描Activity，无需自己画界面，开箱即用。支持识别多个条码、二维码，支持选择相册图片进行解析。

无需进行任何初始化操作，无需提前申请拍照权限，该Activity会自动尝试申请权限。直接启动 **QRScanActivity**




```xml
<uses-sdk tools:overrideLibrary="realid.rfidlib"/>
```

然后在Activity中初始化扫描类 **（记得先申请拍照权限）** ：

```Kotlin
private lateinit var mRfidMain: RfidMain

override fun onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    setContentView(binding.root)

    // 初始化扫描器
    mRfidMain = RfidMain.RfidBuilder(this)
        .setBtnInventory(binding.btnInventory)
        .setIsAutoInventory(false)
        .setIsBeep(true)
        .setRFIDCallback{
            binding.tvMsg.text = it.size.toString()
        }
        .setReplaceString("A")
        .build()
}
```

# RFID
