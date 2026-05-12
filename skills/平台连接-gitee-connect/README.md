# 平台连接-gitee-connect

## 作用
保证新对话与 Gitee 保持连接，支持：
- 自动检查 .mcp.json 配置是否存在
- 验证 Gitee Token 是否已配置
- 检查 enabledMcpjsonServers 是否包含 gitee
- 自动修复配置（如需要）
- 验证连接是否成功

## 安装来源
- 仓库地址: https://github.com/Memorythirty/connect-gitee-mcp-skill

## 安装方式（AI 可自动执行）

### 方式一：使用斜杠命令（推荐）
1. 克隆仓库到任意位置
2. 复制 `gitee-connect.md` 到 `~/.claude/commands/`
3. 复制 `connect-gitee-mcp.json` 和 `connect-gitee-mcp.md` 到 `~/.claude/skills/`
4. 在 Claude Code 中输入 `/gitee-connect`

### 方式二：AI 自动配置
1. 确保用户已提供 Gitee Personal Access Token
2. 在 `~/.claude/.mcp.json` 中添加 gitee 配置（合并到已有 mcpServers）：
   ```json
   {
     "mcpServers": {
       "gitee": {
         "url": "https://api.gitee.com/mcp",
         "headers": {
           "Authorization": "Bearer <TOKEN>"
         }
       }
     }
   }
   ```
3. 在 `~/.claude/settings.local.json` 的 `enabledMcpjsonServers` 中添加 `"gitee"`
4. 重载 VSCode（Ctrl+Shift+P → Developer: Reload Window）

### Token 获取
- 访问 https://gitee.com/profile/personal_access_tokens
- 创建 Token，勾选: projects, issues, pull_requests, notifications

## 指令
- `/gitee-connect` - 检查并确保 Gitee MCP 连接正常

## 可用工具
| 工具 | 功能 |
|------|------|
| list_user_repos | 列出用户仓库 |
| get_file_content | 获取文件内容 |
| create_repo | 创建仓库 |
| fork_repository | Fork 仓库 |
| list_repo_pulls | 列出 PR |
| create_pull | 创建 PR |
| merge_pull | 合并 PR |
| list_repo_issues | 列出 Issue |
| create_issue | 创建 Issue |
| get_user_info | 获取用户信息 |
| search_files_by_content | 搜索文件 |
| list_user_notifications | 列出通知 |
