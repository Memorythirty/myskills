# My Skills Collection

我的 Claude Code Skills 集合

## 已安装的 Skills

| 分类 | Skill | 作用 | 安装来源 |
|------|-------|------|----------|
| 文档处理 | docx | Word 文档处理 | appautomaton/document-SKILLs |
| 文档处理 | pdf | PDF 文档处理 | appautomaton/document-SKILLs |
| 文档处理 | pptx | PowerPoint 文档处理 | appautomaton/document-SKILLs |
| 文档处理 | xlsx | Excel 文档处理 | appautomaton/document-SKILLs |
| 工具发现 | find-skills | 查找可用 skills | vercel-labs/skills |
| 学习工具 | ship-learn-next | 学习内容转化为行动计划 | softaworks/agent-toolkit |
| 代码质量 | review | 代码审查 | 内置 |
| 代码质量 | security-review | 安全审查 | 内置 |
| 代码质量 | simplify | 代码简化 | 内置 |
| 项目管理 | init | 初始化 CLAUDE.md | 内置 |
| 自动化 | loop | 循环执行任务 | 内置 |
| 开发工具 | claude-api | Claude API 开发 | 内置 |
| 浏览器 | agent-browser | 浏览器自动化 | 内置 |

## 目录结构

```
skills/
├── 文档处理-docx/
│   └── README.md
├── 文档处理-pdf/
│   └── README.md
├── 文档处理-pptx/
│   └── README.md
├── 文档处理-xlsx/
│   └── README.md
├── 工具发现-find-skills/
│   └── README.md
├── 学习工具-ship-learn-next/
│   └── README.md
├── 代码质量-review/
│   └── README.md
├── 代码质量-security-review/
│   └── README.md
├── 代码质量-simplify/
│   └── README.md
├── 项目管理-init/
│   └── README.md
├── 自动化-loop/
│   └── README.md
├── 开发工具-claude-api/
│   └── README.md
└── 浏览器-agent-browser/
    └── README.md
```

## 使用方式

每个 skill 文件夹包含：
- `README.md` - 作用、安装来源、安装方式、指令说明

## 安装命令

```bash
# 文档处理 skills
npx skills add appautomaton/document-SKILLs -g -y

# find-skills
npx skills add vercel-labs/skills@find-skills -g -y

# ship-learn-next
npx skills add softaworks/agent-toolkit@ship-learn-next -g -y
```

## Skills 使用指令

```bash
# 文档处理
/docx          # 处理 Word 文档
/pdf           # 处理 PDF 文档
/pptx          # 处理 PowerPoint 文档
/xlsx          # 处理 Excel 文档

# 工具发现
/find-skills   # 查找可用 skills

# 学习工具
/ship-learn-next  # 将学习内容转化为行动计划

# 代码质量
/review           # 代码审查
/security-review  # 安全审查
/simplify         # 代码简化

# 项目管理
/init             # 初始化 CLAUDE.md

# 自动化
/loop             # 循环执行任务

# 开发工具
/claude-api       # Claude API 开发

# 浏览器
/agent-browser    # 浏览器自动化
```
