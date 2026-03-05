---
name: figma-vue3-bootstrap
description: 从 Figma URL 到可合并 PR 的 Vue3 页面交付工作流。用于以下场景：需要在仓库内根据 Figma 设计实现页面或组件；项目尚无前端骨架时需用 Vite 初始化 Vue3+JavaScript；需要接入 ESLint 与 Element Plus；需要通过 Figma MCP 拉取 design context/tokens/screenshot；需要完成组件拆分、实现、lint/build、本地对稿、git commit/push、gh 创建 PR，并在 PR 评论中 @codex review，且全程遵守仓库 AGENTS.md 约束。
---

# Figma Vue3 Bootstrap

## Overview

把“Figma URL -> Vue3 页面落地 -> PR 提交流程”固化为可重复执行的流水线。
优先保证可交付性：先跑通骨架和质量门禁，再逐步贴合设计细节。

## Quick Start

1. 进入目标仓库，先读取仓库内 `AGENTS.md`。
2. 确认输入：Figma URL、目标页面范围、分支命名。
3. 按需初始化或复用现有 Vue3 工程。
4. 用 Figma MCP 拉设计上下文后再编码，不盲写 UI。
5. 通过 `npm run lint` 与 `npm run build` 后再发 PR。
6. 在 PR 中显式评论 `@codex review`。

## Workflow

### 1) Intake And Guardrails

1. 解析 Figma URL，提取 `fileKey` 与 `nodeId`。
2. 检查仓库结构与现有前端目录，识别是否已有 Vue3 工程。
3. 打开并遵守仓库 `AGENTS.md`：命名、脚本、提交流程、禁用操作。
4. 创建工作分支，命名与仓库规范一致。

### 2) Bootstrap Vue3+JS If Missing

仅在仓库缺少可用前端骨架时执行：

1. 用 Vite 初始化 Vue3 + JavaScript 项目。
2. 安装依赖并锁定包管理器（按仓库现状使用 npm/pnpm/yarn）。
3. 确保 `npm run dev` 可启动，目录结构可扩展为组件化实现。

### 3) Attach ESLint + Element Plus

1. 添加并配置 ESLint（优先复用仓库已有规则）。
2. 接入 Element Plus，建立统一入口（例如 `main.js` 全局注册）。
3. 处理基础样式重置与主题变量挂载点，避免后续大面积返工。

### 4) Pull Figma MCP Context

按顺序调用 Figma MCP 工具：

1. `get_design_context`：获取参考代码、布局语义、资源映射。
2. `get_variable_defs`：提取颜色、间距、字号等 token。
3. `get_screenshot`：拿节点截图用于视觉回归。

若节点过大：先按模块拆节点，再分段拉取上下文，避免一次性输出过载。

### 5) Component Decomposition And Implementation

1. 先定义页面层级：`Page -> Section -> Reusable Component`。
2. 把可复用块抽成组件，避免把整页写进单文件。
3. 使用 token 映射到样式变量，避免硬编码魔法数。
4. 优先实现结构和状态，再补齐像素级细节。
5. 对复杂块先搭静态骨架，再逐步接交互。

### 6) Quality Gates

在提交前必须通过：

1. `npm run lint`
2. `npm run build`

若任一步失败：先修复再继续，不带错进入 PR。

### 7) Local Review

1. 启动本地预览并与 Figma 截图逐屏对比。
2. 检查：布局、字号、色值、间距、组件状态、响应式断点。
3. 记录“有意偏差”并写入 PR 描述，避免审查误判。

### 8) Commit, Push, PR

1. 确认 `git status` 仅包含本任务相关改动。
2. 使用清晰 commit message（一次提交对应一个可审阅增量）。
3. 推送分支并用 `gh pr create` 创建 PR。
4. PR 描述包含：实现范围、验证命令结果、已知偏差、后续事项。

### 9) Trigger Codex Review

在 PR 评论中添加：`@codex review`

若仓库 AGENTS.md 对 review 指令格式有额外要求，按仓库要求覆盖此默认格式。

## Execution Notes

1. 优先复用仓库现有脚本与配置，避免引入第二套工程约定。
2. 不要在未确认需求前引入多余状态管理、路由重构或 UI 框架混搭。
3. 遇到 Figma 设计与现有设计系统冲突时，先在 PR 写清取舍与影响。

## References

1. 命令模板与标准节奏：`references/command-playbook.md`
2. 本地对稿与 PR 检查项：`references/review-checklist.md`
