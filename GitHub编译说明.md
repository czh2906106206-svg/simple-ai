# 简单生图 - GitHub 自动编译 APK（零成本，无需 Android Studio）

## 原理
把代码推送到 GitHub，GitHub 的免费服务器自动帮你编译成 APK，然后下载安装。

---

## 操作步骤（5 分钟）

### 第 1 步：注册 GitHub（如果还没有）
- https://github.com
- 用邮箱注册，免费

### 第 2 步：创建仓库
1. 登录 GitHub
2. 点击右上角 + → **New repository**
3. 仓库名填 `simple-ai-app`
4. 选择 **Public**（公开）或 **Private**（私有）都可以
5. 点击 **Create repository**

### 第 3 步：上传代码

**方式 A：网页上传（最简单）**
1. 打开你刚创建的仓库页面
2. 点击 **uploading an existing file**
3. 把 `简单生图-GitHub编译.zip` 里的所有文件拖拽上传
4. 点 **Commit changes**

**方式 B：命令行**
```bash
git clone https://github.com/你的用户名/simple-ai-app.git
cd simple-ai-app
# 把 zip 解压后的文件复制进来
git add .
git commit -m "init"
git push origin main
```

### 第 4 步：触发编译
1. 打开仓库页面
2. 点击顶部 **Actions** 标签
3. 点击左侧 **Build Android APK**
4. 点击右侧 **Run workflow** → **Run workflow**
5. 等待 3-5 分钟（第一次会慢一点）

### 第 5 步：下载 APK
1. 编译完成后，进入 **Actions** 页面
2. 点击最新的一次运行记录
3. 页面最下方 **Artifacts** 区域
4. 点击 **simple-ai-apk** 下载

下载的 zip 解压后就是 `app-debug.apk`，传到手机安装即可。

---

## 以后更新代码

改完代码 → 重新 push 到 GitHub → Actions 自动重新编译 → 下载新 APK

---

## 常见问题

**Q: GitHub Actions 收费吗？**
A: 免费。公共仓库无限使用，私有仓库每月 2000 分钟（够编译几百次）。

**Q: 编译失败怎么办？**
A: 点击 Actions → 失败的记录 → 查看日志，找到红色报错信息发给我。

**Q: 可以改成 release 版本吗？**
A: 可以。在 GitHub 页面点击 **Releases** → **Create a new release**，上传 APK 文件，别人可以直接下载。
