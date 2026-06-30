# 仓库贡献指南

## 项目概述

本仓库是一个 GitHub Pages 静态站点，用于托管某 Android 应用的法律文档（隐私政策和用户协议）。站点通过自定义域名 `jqyx.hjcyy.cn`（在 `CNAME` 中配置）对外发布，无需任何构建步骤，GitHub 直接提供 HTML 文件服务。

## 项目结构与模块组织

- `index.html` —— 站点根目录的落地页 / 隐私政策页面。
- `PrivacyPolicy.html` —— 独立的隐私政策文档。
- `UserAgreement.html` —— 独立的用户协议文档。
- `CNAME` —— GitHub Pages 的自定义域名记录（`jqyx.hjcyy.cn`）。
- `README.md` —— 项目简要说明。

仓库中没有源码目录、测试目录、依赖文件或 CI 配置，所有内容均为手工编辑的单文件 HTML。

## 构建、测试与本地开发命令

本项目没有构建系统。本地预览方式：

```bash
# 使用 Python 启动本地服务器
python -m http.server 8000

# 浏览器打开 http://localhost:8000
```

部署是自动的：推送到 `master` 分支后，GitHub Pages 会在约 1 分钟内发布站点。

## 编码规范与命名约定

- HTML 文件将 CSS 以内联样式或嵌入式 `<style>` 块的方式保留，以维持单文件布局。
- 文档类文件使用 `PascalCase` 命名（如 `PrivacyPolicy.html`、`UserAgreement.html`），基础设施类文件使用小写（如 `index.html`、`CNAME`）。
- 始终以 UTF-8 无 BOM 格式保存文件，并保留 `charset=UTF-8` 的 meta 标签。

### 编码警告

现有的 HTML 文档中存在 GBK 编码的中文被错误地按 UTF-8 解释的情况，表现为乱码（不可读的字符片段）。请勿盲目进行查找替换来"修复"，否则可能损坏内容；应从原始来源重新解码。

## 测试指南

本项目没有自动化测试。手动验证步骤：

1. 编辑后用浏览器逐一打开每个 `.html` 文件。
2. 确认页面能正常渲染，中文内容清晰可读。
3. 推送后访问 https://jqyx.hjcyy.cn 验证线上效果。

## 提交与 Pull Request 规范

参照现有 Git 历史，遵循以下约定：

- 使用简短的祈使语气摘要：如 `Update PrivacyPolicy.html`、`Create CNAME`、`Initial commit`。
- 在标题中指明被修改的文件。
- 尽量让每次提交只涉及一个文档。

Pull Request 要求：

- 提供一行说明，描述改了什么以及原因。
- 如有关联，链接对应的 issue 或合规需求。
- 若页面布局发生可见变化，附上截图。

## 安全与配置提示

- `CNAME` 是域名的权威配置，请勿重命名或删除。
- 法律文本具有合规敏感性，仅修改目标条款，未经确认不要重新表述具有法律约束力的内容。
