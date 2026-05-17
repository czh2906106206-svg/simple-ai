# 简单生图 Android App 编译说明

## 你需要准备

1. **Android Studio**（免费）
   - 下载地址：https://developer.android.com/studio
   - 或者国内镜像：https://developer.android.google.cn/studio

2. **电脑要求**
   - Windows / Mac / Linux 都可以
   - 至少 8GB 内存
   - 10GB 以上硬盘空间

---

## 编译步骤（5 分钟）

### 第 1 步：解压项目

```bash
解压"简单生图-Android项目.zip"到任意文件夹
```

### 第 2 步：Android Studio 打开项目

1. 打开 Android Studio
2. 选择 **Open an Existing Project**
3. 选择解压后的 `android` 文件夹
4. 等待 Gradle 自动下载依赖（第一次需要几分钟，看网速）

### 第 3 步：编译 APK

1. 菜单栏点击 **Build** → **Build Bundle(s) / APK(s)** → **Build APK(s)**
2. 等待编译完成（2-5 分钟）
3. 编译成功后右下角会弹出提示，点击 **locate** 找到 APK 文件

APK 文件位置：
```
android/app/build/outputs/apk/debug/app-debug.apk
```

### 第 4 步：安装到手机

**方法一：USB 直连**
1. 手机开启开发者模式（设置 → 关于手机 → 连续点版本号 7 次）
2. 开启 USB 调试（开发者选项 → USB 调试）
3. 用 USB 连接电脑
4. Android Studio 点击运行按钮（绿色三角），直接装到手机

**方法二：传 APK 文件**
1. 把 `app-debug.apk` 发到手机（微信 / QQ / 数据线）
2. 手机点击安装
3. 如果提示"未知来源"，去设置 → 安全 → 允许未知来源安装

---

## 常见问题

### Q: Gradle 下载很慢 / 失败？
**A:** 在 `android/gradle/wrapper/gradle-wrapper.properties` 中，将 distributionUrl 改为腾讯镜像：
```properties
distributionUrl=https\://mirrors.cloud.tencent.com/gradle/gradle-8.11.1-all.zip
```

### Q: 编译报错 "SDK not found"？
**A:** Android Studio 首次打开会自动下载 SDK，点击提示中的链接安装即可。

### Q: 安装后打开白屏？
**A:** 确保手机能访问 `grsai.dakka.com.cn`，这是 API 服务器。如果网络不通，App 会显示生成失败。

---

## 项目结构

```
android/
  app/src/main/assets/public/  ← 网页资源（前端代码）
  app/src/main/java/           ← Java 原生代码（壳）
  app/src/main/res/            ← 图标、配置
  gradle/wrapper/              ← Gradle 配置
  build.gradle                 ← 构建设置
  settings.gradle              ← 项目设置
```

你的前端代码在 `public/` 文件夹里，以后更新只需要替换里面的文件。
