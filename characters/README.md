# Miko 精选朋友

App 的「认识新朋友」读取 [catalog.json](catalog.json)。这是独立于 APK 的公开内容源，不包含用户聊天、密钥或本机联系人数据。

目录版本为 `1`，`entries` 中每位朋友包含：

- `id`：稳定标识，发布后不要为同一位朋友更换。
- `name`、`intro`、`tags`：列表展示资料。
- `card`：本目录内完整 CCv3 JSON 的相对路径。
- `sha256`：角色文件原始 UTF-8 字节的 SHA-256。
- `avatar_data_url`（可选）：PNG/JPEG/WebP 的 data URL，可由角色卡中的 Miko 扩展提供。现有两位使用 App 既有头像。

角色卡保存于 `<id>/<sha256>.json`，先上传新文件，再更新目录。旧文件保留，让尚未刷新的客户端仍能读取所看到的版本。不要直接覆盖旧摘要文件。目录和单张卡都须小于 1 MiB，最多 100 位朋友；头像遵循角色卡现有大小限制。

在源码仓库更新 `docs/product-design/role-cards/catalog.json` 和对应的 `*-chara-card-v3.json` 后执行：

```sh
uv run python scripts/publish-friend-catalog.py --output /path/to/MikoRelease
```

审核发布仓库的 `characters/` 差异后提交并推送 `main`。该工具只准备角色目录，不上传 APK、不修改 `update.json`。未来可直接在本仓库管理作者卡，但仍需重新计算摘要并更新清单。

客户端断网时使用成功缓存；首次无缓存时使用内置精选朋友。角色更新、从目录移除或下架，都不会修改用户已经添加的独立联系人。已有好友的聊天、记忆、资料和表达配置继续保留。
