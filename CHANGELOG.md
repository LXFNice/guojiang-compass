# 更新日志

## v2.0（2026-10-11）

> **包名 `com.study.research.test` → `com.guojiang.compass`**，与 GitHub 仓库名对应。
> 包名变了，旧版 1.x **无法覆盖升级**，请先卸载旧版再安装本版本。

### 修复

- 修复「检查更新 → 马上更新」下载完成后闪退：`UpdateVersionService` 的通知、以及 `UpdateUtils` 建通知用的 PendingIntent 都缺 `FLAG_IMMUTABLE`（targetSdk 31 起强制要求），已补为 `FLAG_IMMUTABLE | FLAG_UPDATE_CURRENT`
- 修复更新通知点击无法回到应用：原代码硬编码了不存在的 `com.earn.money.MainActivity`，已改为真实主界面
- 修复进度通知与完成通知 id 不一致，导致进度通知无法被撤销的问题
- 修复主界面不显示经纬度：补充 `ACCESS_FINE_LOCATION` / `ACCESS_COARSE_LOCATION` 权限声明
- 修复下载完成后无法调起系统安装器：补 `REQUEST_INSTALL_PACKAGES` 权限与 FileProvider（authority 跟随包名动态拼接）

### 新增

- 下载过程中，通知栏与更新弹窗都实时显示下载百分比
- 下载进度通知统一使用同一 id，完成后自动清理

### 变更

- 包名 `com.study.research.test` → `com.guojiang.compass`
- 版本号 1.0 → **2.0**（versionCode 1 → 2）
- 检查更新的清单地址由 jsdelivr `@vlatest` 标签改为 **`@main` 分支**；安装包下载地址改为 `releases/latest/download/` 永久链接，以后发版不必再改地址

### 升级提示

本版本与旧版签名一致，但包名不同，属于**独立应用**：

1. 先卸载 `com.study.research.test`（旧版）
2. 再安装 `com.guojiang.compass`（本版本）
3. 安装后请允许「位置信息」权限；下载更新后需允许「安装未知应用」

---

## v1.0（2026-10-10）

- 首个研究版本（包名 `com.study.research.test`）
