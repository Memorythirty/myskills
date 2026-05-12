# 平台连接-github-connect

## 作用
保证新对话与 GitHub 保持连接，支持：
- 自动检查 Docker 是否运行
- 验证 GitHub Secret 是否已设置
- 检查 Profile 是否存在
- 验证客户端连接状态
- 自动重新连接（如需要）
- 验证连接是否成功

## 安装来源
- 仓库地址: https://github.com/Memorythirty/connect-github-mcp-skill

## 安装方式（AI 可自动执行）

### 方式一：使用斜杠命令（推荐）
1. 克隆仓库：`git clone https://github.com/Memorythirty/connect-github-mcp-skill.git`
2. 复制 `连接github.md` 到 `~/.claude/commands/`（命令名：`/连接github`）
3. 复制 `connect-github-mcp.json` 和 `connect-github-mcp.md` 到 `~/.claude/skills/`
4. 在 Claude Code 中输入 `/连接github`

### 方式二：AI 自动配置（Docker MCP）
1. 检查 Docker Desktop 是否运行：`docker info 2>&1 | Select-String -Pattern 'Server Version'`
2. 检查 Secret：`docker mcp secret ls`（需包含 github.personal_access_token）
3. 检查 Profile：`docker mcp profile list`（需包含 dev_workflow）
4. 检查连接：`docker mcp client ls --global`（claude-code 需为 connected）
5. 缺失步骤自动引导用户补充（Token、dev-workflow模板、全局连接）

### Token 获取
- 访问 https://github.com/settings/tokens
- 创建 Classic Token，勾选: repo, read:org, workflow

## 指令
- `/连接github` - 检查并确保 GitHub MCP 连接正常

## 可用工具
| 工具 | 功能 |
|------|------|
| get_me | 获取当前用户信息 |
| search_repositories | 搜索仓库 |
| create_repository | 创建仓库 |
| fork_repository | Fork 仓库 |
| list_issues | 列出 Issue |
| issue_write | 创建/更新 Issue |
| list_pull_requests | 列出 PR |
| create_pull_request | 创建 PR |
| merge_pull_request | 合并 PR |
| get_file_contents | 获取文件内容 |
| create_or_update_file | 创建/更新文件 |
| push_files | 批量推送文件 |
| search_code | 搜索代码 |
| list_commits | 列出提交 |
