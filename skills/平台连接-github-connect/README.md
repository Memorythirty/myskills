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
- 自定义 skill（基于 Docker MCP Gateway）

## 安装方式
1. 安装并启动 Docker Desktop

2. 获取 GitHub Personal Access Token（Classic）：
   - 访问 https://github.com/settings/tokens
   - 勾选 repo、read:org、workflow 权限

3. 设置 Secret：
   ```powershell
   docker mcp secret set github.personal_access_token=<your_token>
   ```

4. 安装模板：
   ```powershell
   docker mcp template use dev-workflow --name dev-workflow
   ```

5. 全局连接：
   ```powershell
   docker mcp client connect claude-code --profile dev_workflow --global
   ```

6. 激活 Profile：在 Claude Code 中执行 `mcp-activate-profile: dev_workflow`

7. 重载 VSCode（Ctrl+Shift+P → Developer: Reload Window）

## 指令
- `/github connect` - 检查并确保 GitHub MCP 连接正常

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
