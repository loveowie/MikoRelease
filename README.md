# Miko Android 发布与下载

[下载最新版](https://github.com/loveowie/MikoRelease/releases/latest) · [源码仓库](https://github.com/loveowie/Miko)

本仓库提供 Android 安装包、应用更新清单和精选角色目录。发布页只提供当前最新版 APK，安装包通过 GitHub Releases 下载，版本、SHA-256 与更新说明以 [update.json](https://raw.githubusercontent.com/loveowie/MikoRelease/main/update.json) 为准。

迁移前安装的 App 需要手动下载并覆盖安装 **1.3.3 或更新版本**，之后启动和设置中的“检查更新”均使用本仓库。使用相同签名覆盖安装可保留聊天、角色和模型配置；不要卸载原应用。

应用只提示可用更新，不强制更新。用户确认后下载 APK、校验 SHA-256，再交给 Android 系统确认安装。

## 发布

在 [源码仓库](https://github.com/loveowie/Miko) 使用 `scripts/publish-android-release.sh --publish`，需要 GitHub CLI 登录与原 Release 签名。脚本递增版本、构建 APK，先创建 Release 并上传附件，再更新本仓库 `main` 的清单。新 APK 不写入 Git。

精选角色可以独立发布，流程见 [characters/README.md](characters/README.md)。公开文件不包含用户聊天、联系人、签名密钥或模型凭据。
