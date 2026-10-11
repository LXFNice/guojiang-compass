# 果酱指南针

> 逆向学习与研究用途的 Android 罗盘应用研究版

## 项目说明

本项目是对「终极指南针」(`com.honghui.compass`) 进行脱壳、逆向分析后重建的**学习与研究版本**，用于 Android 逆向工程、Smali 与资源结构的学习交流。

- **非官方版本**，与原始开发者无任何关联
- 仅供个人学习、研究、技术交流使用
- 请勿用于任何商业用途

## 基本信息

| 项目 | 值 |
| --- | --- |
| 应用名 | 果酱指南针 |
| 包名 | `com.guojiang.compass` |
| 当前版本 | 2.0（versionCode 2） |
| minSdk / targetSdk | 21 / 31 |
| 签名方案 | V1 / V2 / V3 |

## 功能

- 指南针 / 地理罗盘 / 水平仪
- 罗盘校准
- 主界面显示经纬度与磁场强度
- 自动检查更新（读取本仓库 `main` 分支的 `update.json`），下载过程显示百分比并可一键安装

## 安装

从 [Releases](https://github.com/LXFNice/guojiang-compass/releases/latest) 下载 `GuoJiangCompass.apk` 安装（认准标着 **Latest** 的那个，其余是历史版本）。

> **2.0 起包名由 `com.study.research.test` 改为 `com.guojiang.compass`**，与旧版 1.x 无法覆盖升级，请先卸载旧版再安装。
> 首次使用请允许「位置信息」权限（否则主界面看不到经纬度）；下载更新后系统会要求授予「安装未知应用」权限。

## 如何发布新版本

> **原则：旧的留着，新的往后加。** 每个版本单独建一个 release，历史版本都保留在页面上，谁想装哪个版本都能找到；只有 README / CHANGELOG 这类文档才直接改。

1. 在 [Releases](https://github.com/LXFNice/guojiang-compass/releases) 点 **Draft a new release**
   - **Choose a tag** 填新版本号（如 `v2.1`），Target 选 `main`
   - **Release title** 写「果酱指南针 2.1」
   - 上传资产，文件名固定用 `GuoJiangCompass.apk`
   - 正文写本次更新内容（可直接抄 CHANGELOG 对应段落）
2. 点 **Publish release**，确认它显示为 **Latest**（GitHub 默认把最新发布的当作 latest；**不要**勾 Pre-release，否则 latest 不会指向它）
3. 同步文档：`update.json` 的 `version` **+1**、`message` 写本次更新日志；`CHANGELOG.md` 加一段
4. 提交到 `main`，然后**清一次 jsdelivr 缓存**（否则最长要等约 12 小时才生效），浏览器直接打开：
   ```
   https://purge.jsdelivr.net/gh/LXFNice/guojiang-compass@main/update.json
   ```
   返回 `"status": "finished"` 就是清成功。

> **下载地址固定为** `https://github.com/LXFNice/guojiang-compass/releases/latest/download/GuoJiangCompass.apk`——它自动指向「最新 release」里的同名资产，所以**发新版本完全不用改 `update.json` 里的 `url`**，也不需要动任何旧 release。
> 判断逻辑：App 拿 `update.json` 的 `version` 与本机 **versionCode** 比较，`version > versionCode` 时提示更新。
> 历史说明：1.x 客户端读取的是 `@vlatest` 标签；2.0 起改读 `@main`，`vlatest` 标签已弃用。

## 目录结构

| 位置 | 说明 |
| --- | --- |
| `update.json` | 版本清单（供 App 检查更新读取） |
| `CHANGELOG.md` | 更新日志 |
| `docs/usage.md` | 使用说明 |
| `docs/agreement.md` | 服务协议 |
| `docs/privacy.md` | 隐私政策 |
| [Releases](https://github.com/LXFNice/guojiang-compass/releases) | 安装包 `GuoJiangCompass.apk`（每个版本一个 release，历史版本保留） |

## 免责声明

原应用的知识产权归原开发者所有。本项目仅包含逆向学习过程中的分析记录与重建产物，不用于分发牟利。如您是权利人且不希望本项目存在，请联系删除。
