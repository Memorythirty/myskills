# 新电脑安装指南

本文档帮助你在新电脑上快速安装和配置所有 Claude Code Skills。

## 环境要求

- [Node.js](https://nodejs.org/) 18+（用于 npx 命令）
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)（仅 GitHub 连接需要）
- [Claude Code](https://docs.anthropic.com/claude-code) 已安装

## 安装步骤总览

```
步骤 1: 安装可自动安装的 Skills（4 个）
步骤 2: 配置 GitHub 连接
步骤 3: 配置 Gitee 连接
步骤 4: 验证安装
```

---

## 步骤 1: 安装可自动安装的 Skills

打开终端，依次执行以下命令：

```bash
# 文档处理 skills（4 个）
npx skills add appautomaton/document-SKILLs -g -y

# 工具发现
npx skills add vercel-labs/skills@find-skills -g -y

# 学习工具
npx skills add softaworks/agent-toolkit@ship-learn-next -g -y
```

安装完成后，重载 VSCode：`Ctrl+Shift+P` → `Developer: Reload Window`

---

## 步骤 2: 配置 GitHub 连接

### 2.1 安装 github-connect skill

```bash
git clone https://github.com/Memorythirty/connect-github-mcp-skill.git
cd connect-github-mcp-skill
```

复制文件：
- 复制斜杠命令文件到 `~/.claude/commands/`（支持 `/连接github` 和 `/github-connect`）
- 复制配置和文档文件到 `~/.claude/skills/`

在 Claude Code 中输入 `/连接github`，AI 将自动引导完成 GitHub MCP 连接。

### 2.2 获取 GitHub Token

1. 访问 https://github.com/settings/tokens
2. 点击 "Generate new token" → "Classic"
3. 勾选权限：`repo`、`read:org`、`workflow`
4. 点击 "Generate token" 并复制

### 2.3 验证

在 Claude Code 中请求获取 GitHub 用户信息，确认连接成功。

---

## 步骤 3: 配置 Gitee 连接

### 3.1 安装 gitee-connect skill

```bash
git clone https://github.com/Memorythirty/connect-gitee-mcp-skill.git
cd connect-gitee-mcp-skill
```

复制文件：
- 复制斜杠命令文件到 `~/.claude/commands/`（支持 `/gitee-connect`）
- 复制配置和文档文件到 `~/.claude/skills/`

在 Claude Code 中输入 `/gitee-connect`，AI 将自动引导完成 Gitee MCP 连接。

### 3.2 获取 Gitee Token

1. 访问 https://gitee.com/profile/personal_access_tokens
2. 填写描述，勾选权限：`projects`、`issues`、`pull_requests`、`notifications`
3. 点击 "创建" 并复制 Token

### 3.3 验证

在 Claude Code 中请求获取 Gitee 用户信息，确认连接成功。

---

## 步骤 4: 验证安装

在 Claude Code 中执行以下指令，确认各 skill 正常工作：

| 指令 | 预期结果 |
|------|----------|
| `/find-skills` | 能够搜索 skills |
| `/review` | 能够列出 PR（需 GitHub 连接） |
| `/gitee-connect` | 检查 Gitee MCP 连接状态 |
| `/连接github` 或 `/github-connect` | 检查 GitHub MCP 连接状态 |

---

## Skills 清单

### 可自动安装（6 个）

| Skill | 安装命令 |
|-------|----------|
| docx | `npx skills add appautomaton/document-SKILLs -g -y` |
| pdf | 同上（批量安装） |
| pptx | 同上（批量安装） |
| xlsx | 同上（批量安装） |
| find-skills | `npx skills add vercel-labs/skills@find-skills -g -y` |
| ship-learn-next | `npx skills add softaworks/agent-toolkit@ship-learn-next -g -y` |

### GitHub 仓库安装（2 个）

| Skill | 仓库 | 指令 |
|-------|------|------|
| github-connect | https://github.com/Memorythirty/connect-github-mcp-skill | `/连接github` |
| gitee-connect | https://github.com/Memorythirty/connect-gitee-mcp-skill | `/gitee-connect` |

### 内置 Skills（7 个，无需安装）

| Skill | 指令 | 作用 |
|-------|------|------|
| review | `/review` | 代码审查 |
| security-review | `/security-review` | 安全审查 |
| simplify | `/simplify` | 代码简化 |
| init | `/init` | 初始化 CLAUDE.md |
| loop | `/loop` | 循环执行任务 |
| claude-api | `/claude-api` | Claude API 开发 |
| agent-browser | `/agent-browser` | 浏览器自动化 |

---

## 故障排查

| 问题 | 解决方案 |
|------|----------|
| npx 命令不存在 | 安装 Node.js: https://nodejs.org/ |
| docker mcp 命令不存在 | 更新 Docker Desktop 到最新版 |
| Skill 安装后不生效 | 重载 VSCode: `Ctrl+Shift+P` → `Developer: Reload Window` |
| GitHub Token 401/403 | 重新生成 Token 并更新 Secret |
| Gitee 工具不可用 | 检查 .mcp.json 配置和 enabledMcpjsonServers |

---

**最后更新**: 2026-05-13
**维护者**: Memorythirty
