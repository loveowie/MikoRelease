# Miko 发布仓库

这个仓库只存放 Miko Android 的公开更新资源，不包含应用源码、签名文件或模型密钥。

## 当前版本

- 版本：`1.2.1`
- `versionCode`：`4`
- Release：[v1.2.1](https://gitee.com/Faylinn/miko-release/releases/tag/v1.2.1)
- APK：[miko-1.2.1-20261013-update-release.apk](https://gitee.com/Faylinn/miko-release/releases/download/v1.2.1/miko-1.2.1-20261013-update-release.apk)

Miko 启动时会读取本仓库的 [`update.json`](./update.json)。发现更高版本时只提示用户，不会强制更新。用户确认后，应用下载 APK、校验 SHA-256，再交给 Android 系统安装。覆盖安装会保留聊天记录、角色数据和模型连接；APK 必须使用与已安装版本相同的 Release 签名。

## 发布新版本

1. 在主仓库递增 Android `versionCode` 和 `versionName`，用同一 Release 签名构建 APK。
2. 计算 APK 的 SHA-256。
3. 在本仓库创建同名 Gitee Release 并上传 APK。
4. 更新 `update.json` 的 `versionCode`、`versionName`、`apkUrl`、`sha256` 和 `releaseNotes`，提交到 `main`。
5. 用手机打开应用，启动时会自动检查；也可以在“关于 Miko”中手动检查。

`update.json` 和 Release 附件保持公开，主项目可以继续保持私有。
