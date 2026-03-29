# Installing Anthropic Skills for OpenCode

## Prerequisites

- [OpenCode.ai](https://opencode.ai) installed

## Installation

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

> **Note:** Creating symbolic links on Windows may require administrator privileges or Developer Mode enabled.

Restart OpenCode to discover the skills.

Verify by asking: "List available skills"

## Available Skills

### Document Processing

- **docx** — Professional DOCX document creation, editing, and formatting using OpenXML SDK (.NET)
- **pdf** — Read, merge, split, watermark, fill forms, OCR, and create PDF documents
- **pptx** — Generate, edit, and read PowerPoint presentations with PptxGenJS
- **xlsx** — Open, create, read, analyze, edit, and validate Excel/spreadsheet files

### Creative & Design

- **algorithmic-art** — Creating algorithmic art using p5.js with seeded randomness and interactive parameter exploration
- **canvas-design** — Canvas design with professional typography and font resources
- **brand-guidelines** — Brand guidelines processing and application
- **frontend-design** — Create distinctive, production-grade frontend interfaces with high design quality

### Development & Technical

- **webapp-testing** — Interact with and test local web applications using Playwright
- **mcp-builder** — Build high-quality MCP (Model Context Protocol) servers
- **claude-api** — Claude API integration patterns for Python and TypeScript

### Productivity & Workflow

- **skill-creator** — Create new skills, test them with evals, and iteratively improve performance
- **doc-coauthoring** — Collaborative document creation workflows
- **internal-comms** — Enterprise internal communications templates
- **slack-gif-creator** — Create animated GIF stickers for Slack
- **theme-factory** — Theme creation and customization
- **web-artifacts-builder** — Web artifacts construction toolkit

## Updating

```bash
cd ~/.anthropic-skills && git pull
```

Symlinks will automatically point to the updated content — no need to re-link.

## Uninstalling

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

## Troubleshooting

### Skills not found

1. Verify symlinks exist: `ls -la ~/.config/opencode/skills/`
2. Each skill folder should contain a `SKILL.md` file
3. Restart OpenCode after installation

### Permission denied (Windows)

If you encounter permission errors when creating symbolic links, try:

1. Enable Developer Mode in Windows Settings
2. Or run PowerShell as Administrator

### Clone fails

If `git clone` fails, ensure you have Git installed and configured:

```bash
git --version
```

## Getting Help

- Official documentation: [Agent Skills Guide](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
- Report issues: [https://github.com/anthropics/skills/issues](https://github.com/anthropics/skills/issues)
