# 新电脑安装指南

本文档帮助你在新电脑上快速安装和配置所有 Claude Code Skills。

## 环境要求

- [Node.js](https://nodejs.org/) 18+（用于 npx 命令）
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)（仅 GitHub 连接需要）
- [Claude Code](https://docs.anthropic.com/claude-code) 已安装

## 安装步骤总览

```
步骤 1: 安装可自动安装的 Skills（4 个）
步骤 2: 配置 GitHub 连接（可选）
步骤 3: 配置 Gitee 连接（可选）
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

## 步骤 2: 配置 GitHub 连接（可选）

如果你需要使用 GitHub MCP，请按以下步骤操作：

### 2.1 获取 GitHub Token

1. 访问 https://github.com/settings/tokens
2. 点击 "Generate new token" → "Classic"
3. 勾选权限：`repo`、`read:org`、`workflow`
4. 点击 "Generate token" 并复制

### 2.2 安装配置

在 PowerShell 中执行：

```powershell
# 设置 Secret
docker mcp secret set github.personal_access_token=<你的Token>

# 安装模板
docker mcp template use dev-workflow --name dev-workflow

# 全局连接
docker mcp client connect claude-code --profile dev_workflow --global
```

在 Claude Code 中执行：
```
mcp-activate-profile: dev_workflow
```

重载 VSCode：`Ctrl+Shift+P` → `Developer: Reload Window`

### 2.3 验证

在 Claude Code 中输入 `/github connect`

---

## 步骤 3: 配置 Gitee 连接（可选）

如果你需要使用 Gitee MCP，请按以下步骤操作：

### 3.1 获取 Gitee Token

1. 访问 https://gitee.com/profile/personal_access_tokens
2. 填写描述，勾选权限：`projects`、`issues`、`pull_requests`、`notifications`
3. 点击 "创建" 并复制 Token

### 3.2 创建配置文件

在用户目录下创建 `.mcp.json`：

**Windows**: `C:\Users\<你的用户名>\.mcp.json`
**Mac/Linux**: `~/.mcp.json`

```json
{
  "mcpServers": {
    "gitee": {
      "url": "https://api.gitee.com/mcp",
      "headers": {
        "Authorization": "Bearer <你的Token>"
      }
    }
  }
}
```

### 3.3 启用 Gitee

编辑 `~/.claude/settings.local.json`，在 `enabledMcpjsonServers` 中添加 "gitee"：

```json
{
  "enabledMcpjsonServers": [
    "github",
    "gitee"
  ]
}
```

如果文件不存在，创建一个空的：
```json
{
  "permissions": {
    "allow": []
  },
  "enabledMcpjsonServers": [
    "gitee"
  ]
}
```

### 3.4 验证

重载 VSCode 后，在 Claude Code 中输入 `/gitee connect`

---

## 步骤 4: 验证安装

在 Claude Code 中执行以下指令，确认各 skill 正常工作：

| 指令 | 预期结果 |
|------|----------|
| `/find-skills` | 能够搜索 skills |
| `/review` | 能够列出 PR（需 GitHub 连接） |
| `/gitee connect` | 显示连接状态（需 Gitee 连接） |
| `/github connect` | 显示连接状态（需 GitHub 连接） |

---

## Skills 清单

### 可自动安装（4 个）

| Skill | 安装命令 |
|-------|----------|
| docx | `npx skills add appautomaton/document-SKILLs -g -y` |
| pdf | 同上（批量安装） |
| pptx | 同上（批量安装） |
| xlsx | 同上（批量安装） |
| find-skills | `npx skills add vercel-labs/skills@find-skills -g -y` |
| ship-learn-next | `npx skills add softaworks/agent-toolkit@ship-learn-next -g -y` |

### 需手动配置（2 个）

| Skill | 前置条件 |
|-------|----------|
| github-connect | Docker Desktop + GitHub Token |
| gitee-connect | Gitee Token + .mcp.json 配置 |

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

## 快速复制命令

### 一键安装所有可自动安装的 Skills

```bash
npx skills add appautomaton/document-SKILLs -g -y && \
npx skills add vercel-labs/skills@find-skills -g -y && \
npx skills add softaworks/agent-toolkit@ship-learn-next -g -y
```

### GitHub 连接快速配置（PowerShell）

```powershell
# 替换 <TOKEN> 为你的 GitHub Token
docker mcp secret set github.personal_access_token=<TOKEN>
docker mcp template use dev-workflow --name dev-workflow
docker mcp client connect claude-code --profile dev_workflow --global
```

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

**最后更新**: 2026-05-12
**维护者**: Memorythirty
