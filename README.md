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

从 [Releases](https://github.com/LXFNice/guojiang-compass/releases) 下载 `GuoJiangCompass.apk` 安装。

> **2.0 起包名由 `com.study.research.test` 改为 `com.guojiang.compass`**，与旧版 1.x 无法覆盖升级，请先卸载旧版再安装。
> 首次使用请允许「位置信息」权限（否则主界面看不到经纬度）；下载更新后系统会要求授予「安装未知应用」权限。

## 如何发布新版本

1. 在 [Releases](https://github.com/LXFNice/guojiang-compass/releases) 里新建一个 release（或替换已有 release 中的 `GuoJiangCompass.apk` 资产），资产名保持 `GuoJiangCompass.apk`，并确保它是**最新发布**（latest）
2. 修改根目录 `update.json`：`version` 每次 **+1**，`message` 写本次更新日志
3. 提交到 `main` 分支即可生效（App 读取的是 jsdelivr 的 `@main`，分支缓存约 12 小时）

> **下载地址固定为** `https://github.com/LXFNice/guojiang-compass/releases/latest/download/GuoJiangCompass.apk`（GitHub 的 latest 重定向），所以换版本时**不需要改 `update.json` 里的 `url`**。
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
| [Releases](https://github.com/LXFNice/guojiang-compass/releases) | 安装包 `GuoJiangCompass.apk` |

## 免责声明

原应用的知识产权归原开发者所有。本项目仅包含逆向学习过程中的分析记录与重建产物，不用于分发牟利。如您是权利人且不希望本项目存在，请联系删除。
