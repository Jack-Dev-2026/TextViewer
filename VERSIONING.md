# TextViewer 版本命名与发版规范 (Versioning & Release Rules)

为了确保 TextViewer 的持续迭代具备极高的规范性，明确每次更新的重要程度，并降低用户的升级成本，我们参考了业界重型软件（如 VS Code）的命名逻辑，并结合极客精神，制定了 **五段式版本号机制**。

本文档适用于所有开发者、贡献者以及终端用户。

---

## 1. 五段式版本号结构定义

标准版本号格式为：`v.[逻辑大版本].[主题大版本].[中版本].[热修复号].[快照号]`
例如：`v1.4.0.0.1`

### 1.1 核心字段详细解析

**① 第一段：逻辑大版本 (Logical Major)**
*   **标识**：`v1`
*   **定义**：软件的基础架构与逻辑世代。
*   **规则**：极其稳定，一般不会轻易变动。只有当软件发生颠覆性的底层语言重构（比如从跨语言改为纯原生）、或者彻底推翻了现有的操作逻辑时，才会变成 `v2`。
**② 第二段：主题大版本 (Thematic Major)**
*   **标识**：`v1.4`
*   **定义**：代表一个**“更新主题”**的周期。
*   **规则**：当软件积累了大量新特性，或者决定开启一个全新的阶段性更新目标（例如：“v2.x 主题是性能重构”、“v3.x 主题是插件生态”）时递增。每当这个数字变动，意味着软件迎来了一次大换血。

**③ 第三段：中版本 (Minor)**
*   **标识**：`v1.4.1`
*   **定义**：常规的新功能发布。
*   **规则**：每当软件加入了实质性的新功能（如：支持了语法高亮、加入了多标签页、实装了 10 国语言），这个数字就会递增。它代表软件“变强了”。

**④ 第四段：热修复号 (Emergency Hotfix)**
*   **标识**：`v1.4.0.1` 中的 `1`
*   **定义**：专用于紧急修补致命 Bug。
*   **规则**：当线上稳定版本出现了严重影响使用的缺陷（如：无法保存文件、频繁闪退），我们会跳过中版本的更新，直接在这个位置 +1，发布紧急补丁。此位置**可加可不加**，如果是常规的稳定版，这里为 `0`。

**⑤ 第五段：快照号 (Beta Snapshot)**
*   **标识**：`v1.4.1.0.1` 中的最后一个 `1`
*   **定义**： Snapshot 快照版，代表在某个特定版本上的内测迭代。
*   **规则**：比如 `v1.4.1.0.1` 代表这是 1.4.1 版本的**第一个快照**。如果测试期间发现了 Bug 并修复，我们不会发正式版，而是发布 `v1.4.1.0.2`（第二个快照）。只有快照测试稳定后，才会发布不带第五段快照号的正式版 `v1.4.1`。

---

## 2. 历史经典版本复盘

*   `v1.3.0.0.1`：首个正式重构常驻服务、加入 10 国语言的快照测试版。
*   `v1.3.0.1`：**经典热修复案例**。当时 v1.3.0 重构导致了“无法保存”的致命退化，团队在数小时内定位并发布此紧急补丁。
*   `v1.4.0`：史诗级更新正式版。支持拖拽、右键打开，内置极速自动更新。

---

## 3. 发版与用户升级策略 (Release Workflow)

1.  **构建产物**：所有发布包均由 `PyInstaller` 打包，且必须内嵌精简版 `java_runtime` 环境，确保用户“下载即解压，双击即运行”。
2.  **自动更新机制**：自 v1.4.0 起，软件内置国内镜像加速下载模块。只要发布了新版本，用户即可在软件内一键秒速更新。
3.  **破坏性变更警告**：如果某版本涉及不兼容变更，开发者必须在 Release 日志首行使用 `🚨 BREAKING CHANGES` 醒目标注。

---
*本规范自 v1.4.1.0.1 版本起正式生效。TextViewer 开发团队保留对版本命名规则的最终解释权。*
*最后更新日期：2026年11月15日*



# TextViewer Versioning & Release Rules

To ensure highly standardized and transparent iteration of TextViewer, clearly communicate the importance of each update, and minimize the upgrade cost for users, we have adopted a **Five-Segment Versioning Scheme** inspired by industry-standard software (e.g., VS Code).

This document applies to all developers, contributors, and end-users.

---

## 1. Five-Segment Version Structure

The standard version format is:
`v.[Logical Major].[Thematic Major].[Minor].[Hotfix].[Snapshot]`
Example: `v1.4.1.0.1`

### 1.1 Detailed Field Definitions

**① Logical Major**
*   **Identifier**: `v1`
*   **Definition**: The foundational architecture and logical generation of the software.
*   **Rule**: Highly stable and rarely changes. It only increments (e.g., to `v2`) when the software undergoes a disruptive backend language refactoring (e.g., shifting from a cross-language architecture to native) or a complete overhaul of existing operational logic.

**② Thematic Major**
*   **Identifier**: `v1.4`
*   **Definition**: Represents an "Update Theme" cycle.
*   **Rule**: Increments when the software accumulates numerous new features or initiates a new phase of updates (e.g., "v2.x Theme: Performance Refactoring", "v3.x Theme: Plugin Ecosystem"). Each change in this number signifies a major overhaul.

**③ Minor**
*   **Identifier**: `v1.4.1`
*   **Definition**: Regular feature releases.
*   **Rule**: Increments when substantial new features are added (e.g., syntax highlighting, multi-tab support, 10-language localization). It represents that the software has "become stronger".

**④ Hotfix**
*   **Identifier**: The `1` in `v1.4.0.1`
*   **Definition**: Dedicated to urgent patching of critical bugs.
*   **Rule**: When a stable release has a usage-impacting defect (e.g., failure to save, frequent crashes), this number increments instead of the Minor version. This is optional; if it's a regular stable release, this field is `0`.

**⑤ Snapshot**
*   **Identifier**: The last `1` in `v1.4.1.0.1`
*   **Definition**: Represents internal iteration on a specific version, similar to a snapshot release.
*   **Rule**: For example, `v1.4.1.0.1` means this is the **first snapshot** of version 1.4.1. If bugs are found and fixed during testing, we will release `v1.4.1.0.2` (the second snapshot) rather than the official version. Only after snapshot testing is stable will we release the official version `v1.4.1` without the snapshot segment.

---

## 2. Historical Version Review

*   `v1.3.0.0.1`: The first snapshot testing version that refactored the persistent service and added 10-language support.
*   `v1.3.0.1`: **Classic Hotfix Case**. A critical regression ("unable to save") occurred after v1.3.0's refactoring; the team identified and released this emergency patch within hours.
*   `v1.4.0`: Epic official update. Supports drag-and-drop, right-click opening, and built-in ultra-fast auto-updates.

---

## 3. Release & Upgrade Strategy

1.  **Build Artifacts**: All release packages are built using `PyInstaller` and must embed the lite `java_runtime` environment to ensure "download, unzip, and double-click to run".
2.  **Auto-Update Mechanism**: Starting from v1.4.0, the software includes a built-in domestic mirror acceleration module for downloads. Users can update instantly within the app once a new version is published.
3.  **Breaking Changes Warning**: If a version involves incompatible changes, developers must prominently mark it with `🚨 BREAKING CHANGES` in the first line of the Release notes.

---
*This specification takes effect from v1.4.0 onwards. The TextViewer Development Team reserves the right of final interpretation for these versioning rules.*
*Last Updated: November 15, 2026*
