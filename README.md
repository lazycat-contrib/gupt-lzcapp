# GUPT - LazyCat App

[GUPT](https://github.com/besoeasy/gupt)（自托管端到端加密即时通讯）的懒猫微服（LazyCat）打包。

## 模式

- **镜像模式（mirror）**：`ghcr.io/besoeasy/gupt` 镜像经 `ghcr.1ms.run` 加速器拉取，`require_digest_match: true` 校验镜像内容与上游一致。
- **自动跟随上游**：每日检查上游 semver tag（`channel: stable`），发现新版本自动更新版本号与镜像、构建 LPK、发布商店。
- **喵喵商店发布**：仅私有商店（MiaoMiao private store），不发布官方商店。

## 说明

- **纯前端应用**：Caddy 静态服务 + 端到端加密，消息数据全部保存在浏览器本地，无服务器数据卷。
- tag 家族为无 `v` 前缀的 semver（`5.1.5`）。

## 结构

| 文件 | 说明 |
| --- | --- |
| `package.yml` | 包元数据（`community.lazycat.app.gupt`） |
| `lzc-manifest.yml` | 服务与路由配置 |
| `lzc-build.yml` | 构建配置 |
| `icon.png` | 图标（上游 PWA 图标） |
| `.github/lazycat-action.yml` | [lazycat-github-action](https://github.com/ca-x/lazycat-github-action) 配置 |
| `.github/workflows/lazycat.yml` | 构建 + 发布工作流 |

## 所需 Secrets

| Secret | 说明 |
| --- | --- |
| `APPSTORE_URL` / `APPSTORE_TOKEN` | 喵喵商店 API 地址与发布令牌 |
| `APP_ID` | 可选 |
| `PRIVATE_STORE_GROUP_CODES` | 可选，私有分组码 |
