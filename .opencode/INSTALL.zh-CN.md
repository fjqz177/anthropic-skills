# Anthropic Skills for OpenCode 安装教程

## 前置要求

- 已安装 [OpenCode.ai](https://opencode.ai)

## 安装步骤

### macOS / Linux

```bash
git clone https://github.com/anthropics/skills.git ~/.anthropic-skills

mkdir -p ~/.config/opencode/skills
ln -s ~/.anthropic-skills/skills/* ~/.config/opencode/skills/
```

### Windows (PowerShell)

```powershell
git clone https://github.com/anthropics/skills.git "$env:USERPROFILE\.anthropic-skills"

New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.config\opencode\skills"
Get-ChildItem "$env:USERPROFILE\.anthropic-skills\skills" -Directory | ForEach-Object {
    New-Item -ItemType SymbolicLink -Path "$env:USERPROFILE\.config\opencode\skills\$($_.Name)" -Target $_.FullName
}
```

> **注意:** 在 Windows 上创建符号链接可能需要管理员权限或启用开发者模式。

安装完成后重启 OpenCode 即可发现这些技能。

验证方法：可以问 OpenCode "列出可用的技能"

## 可用技能列表

### 文档处理

- **docx** — 使用 OpenXML SDK (.NET) 创建、编辑和格式化专业的 Word 文档
- **pdf** — 阅读、合并、拆分、加水印、填写表单、OCR 识别以及创建 PDF 文档
- **pptx** — 使用 PptxGenJS 生成、编辑和阅读 PowerPoint 演示文稿
- **xlsx** — 打开、创建、阅读、分析、编辑和验证 Excel 电子表格文件

### 创意设计

- **algorithmic-art** — 使用 p5.js 创建算法艺术，支持随机种子和交互式参数探索
- **canvas-design** — Canvas 设计，包含专业排版和字体资源
- **brand-guidelines** — 品牌指南的处理和应用
- **frontend-design** — 创建独特、生产级的前端界面，追求高质量设计

### 开发与技术

- **webapp-testing** — 使用 Playwright 与本地 Web 应用进行交互和测试
- **mcp-builder** — 构建高质量的 MCP（Model Context Protocol）服务器
- **claude-api** — Python 和 TypeScript 的 Claude API 集成模式

### 生产力与工作流

- **skill-creator** — 创建新技能，使用评估测试，并迭代改进性能
- **doc-coauthoring** — 协作式文档创建工作流
- **internal-comms** — 企业内部沟通模板
- **slack-gif-creator** — 为 Slack 创建动画 GIF 贴纸
- **theme-factory** — 主题创建和定制
- **web-artifacts-builder** — Web 构建工具包

## 更新技能

```bash
cd ~/.anthropic-skills && git pull
```

符号链接会自动指向更新后的内容，无需重新链接。

## 卸载

### macOS / Linux

```bash
rm -rf ~/.config/opencode/skills
rm -rf ~/.anthropic-skills
```

### Windows (PowerShell)

```powershell
Remove-Item -Recurse -Force "$env:USERPROFILE\.config\opencode\skills"
Remove-Item -Recurse -Force "$env:USERPROFILE\.anthropic-skills"
```

## 常见问题

### 技能无法识别

1. 确认符号链接已创建：`ls -la ~/.config/opencode/skills/`
2. 确认每个技能文件夹中都包含 `SKILL.md` 文件
3. 安装后记得重启 OpenCode

### 权限不足（Windows）

如果创建符号链接时遇到权限错误，可以尝试：

1. 在 Windows 设置中启用开发者模式
2. 或者以管理员身份运行 PowerShell

### Clone 失败

如果 `git clone` 命令失败，请确保已安装并正确配置了 Git：

```bash
git --version
```

## 获取帮助

- 官方文档：[Agent Skills 使用指南](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
- 问题反馈：[https://github.com/anthropics/skills/issues](https://github.com/anthropics/skills/issues)
