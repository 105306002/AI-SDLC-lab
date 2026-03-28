# 3. 設定 GitHub MCP Server

> 🎯 **目標**: 配置 GitHub MCP Server，讓 Bob 可以使用 GitHub MCP 存取 GitHub API

---

## 📖 什麼是 GitHub MCP Server？

**GitHub MCP Server** 讓 Bob 可以：
- 📋 讀取和管理 Issues
- 🔀 建立和管理 Pull Requests
- 📝 讀取和更新 Repository 資訊
- 👥 管理 Collaborators
- 🏷️ 管理 Labels 和 Milestones
- 📤 推送檔案到 GitHub

**為什麼需要它？**
- ✅ Bob 可以自動建立 Issues
- ✅ Bob 可以建立 Pull Requests
- ✅ Bob 可以查看專案狀態
- ✅ 提高團隊協作效率

---

## 📋 前置需求

在開始設定前，請確保：

- ✅ 已安裝 **Bob AI 助手**
- ✅ 已設定 **Git MCP Server**（參考 [02-setup-git-mcp.md](./02-setup-git-mcp.md)）
- ✅ 有 **GitHub 帳號**
- ✅ 已安裝 **Node.js(v18.0.0++)**



## ✅ 前置檢查：Node.js 版本

在開始之前，請確認您已安裝符合要求的 Node.js 版本。

### **檢查步驟**

開啟終端機（Terminal / PowerShell），執行以下命令：

```bash
node --version
```
---

## 🔑 步驟 1: 建立 GitHub Personal Access Token

### 1.1 登入 GitHub

前往 [github.com](https://github.com) 並登入你的帳號

### 1.2 進入 Token 設定頁面

1. 點擊右上角的 **個人頭像**
2. 選擇 **Settings**（設定）
3. 在左側選單中，滾動到最下方
4. 點擊 **Developer settings**（開發者設定）
5. 點擊 **Personal access tokens**
6. 選擇 **Tokens (classic)**
7. 點擊 **Generate new token** → **Generate new token (classic)**

### 1.3 設定 Token

填寫以下資訊：

**Note（備註）**:
```
Bob AI - SDLC Workshop
```

**Expiration（有效期限）**:
- 選擇 **90 days**（90 天）
- 或 **No expiration**（永不過期，不建議）

**Select scopes（選擇權限）**:

勾選以下權限：

✅ **repo** - 完整的 repository 存取權限
  - ✅ repo:status
  - ✅ repo_deployment
  - ✅ public_repo
  - ✅ repo:invite
  - ✅ security_events

✅ **workflow** - 更新 GitHub Actions workflows

✅ **write:packages** - 上傳套件到 GitHub Package Registry
  - ✅ read:packages

✅ **delete:packages** - 刪除套件

✅ **admin:org** - 完整的組織存取權限（如果使用組織帳號）
  - ✅ write:org
  - ✅ read:org

✅ **admin:public_key** - 管理公鑰
  - ✅ write:public_key
  - ✅ read:public_key

✅ **admin:repo_hook** - 管理 repository hooks
  - ✅ write:repo_hook
  - ✅ read:repo_hook

✅ **user** - 更新使用者資料
  - ✅ read:user
  - ✅ user:email
  - ✅ user:follow

✅ **project** - 存取專案
  - ✅ read:project

### 1.4 產生 Token

1. 滾動到頁面底部
2. 點擊 **Generate token**（產生 token）
3. **重要**: 複製產生的 token（只會顯示一次！）
4. 將 token 儲存到安全的地方（例如密碼管理器）

Token 格式類似：
```
ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

---

## 🔧 步驟 2: 設定 GitHub MCP Server



### 2.2 開啟設定檔

使用 VSCode 開啟 `mcp_settings.json`

### 2.3 新增 GitHub MCP Server 配置

在現有的 `git` 配置，新增 `github` 配置：

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-github"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<你的 GitHub Token>",
        "GITHUB_HOST": "https://github.com"
      }
    },
    "git": {
      "command": "npx",
      "args": [
        "-y",
        "@cyanheads/git-mcp-server"
      ],
      "env": {
        "MCP_TRANSPORT_TYPE": "stdio",
        "MCP_LOG_LEVEL": "debug"
      },
      "alwaysAllow": [],
      "disabledTools": []
    }
  }
}

```

**重要**: 將 `<你的 GitHub Token>` 替換為你在步驟 1.4 複製的 token！

### 2.4 儲存設定檔

1. 按下 `Ctrl+S` (Windows) 或 `Cmd+S` (macOS) 儲存
2. 確認檔案已儲存

### 2.5 重新啟動 Bob

**重要**: 必須重新啟動 Bob 才能載入新的 MCP 設定

1. 關閉 VSCode
2. 重新開啟 VSCode
3. 等待 Bob 啟動（約 10-15 秒，首次啟動會下載 Docker 映像）

---

## ✅ 驗證設定
<img width="721" alt="github" src="https://github.ibm.com/user-attachments/assets/ae0ea877-247b-4b22-a586-0097e3b52f22" />

### 測試 1: 檢查 GitHub 連接

1. 開啟 Bob IDE 聊天面板
2. 切換到 **Advanced 模式**
3. 輸入以下訊息：
   ```
   請使用 GitHub MCP Server 列出我的 repositories
   ```
4. Bob 會顯示你的 GitHub repositories 列表

---

## 🧪 CLI 測試 MCP Server

除了透過 Bob 測試，也須使用命令列直接測試 GitHub MCP Server 是否正常運作。

### 測試方法

開啟終端機並執行：
```bash
/mcp list
```
若出現以下 github 工具則已經設定成功：
![Bob 顯示 MCP Server 工具列選單](https://github.ibm.com/user-attachments/assets/f08c5e99-b353-4523-86c3-1a73f40795f0)


---

## 🔍 進階設定 (Optional)

### 自動允許特定操作

如果想讓 Bob 自動執行某些操作而不詢問：

```json
{
  "mcpServers": {
    "github": {
      "alwaysAllow": [
        "list_issues",
        "issue_read",
        "list_pull_requests",
        "pull_request_read"
      ]
    }
  }
}
```

### 停用特定工具

如果不想讓 Bob 執行某些 GitHub 操作：

```json
{
  "mcpServers": {
    "github": {
      "disabledTools": [
        "delete_repository",
        "merge_pull_request"
      ]
    }
  }
}
```

### 使用 GitHub Enterprise

如果你的組織使用 GitHub Enterprise：

```json
{
  "mcpServers": {
    "github": {
      "args": [
        "run",
        "--rm",
        "-i",
        "--pull=always",
        "-e",
        "GITHUB_PERSONAL_ACCESS_TOKEN=your_token",
        "-e",
        "GITHUB_API_URL=https://github.your-company.com/api/v3",
        "ghcr.io/github/github-mcp-server"
      ]
    }
  }
}
```

---

## ❌ 常見問題排解

### 問題 1: Podman 找不到

**症狀**: 
```
Error: podman: command not found
```

**解決方法**:
1. 確認 Podman 已安裝並啟動
2. 重新啟動終端機/VSCode



---

## 🔒 安全性注意事項

### ⚠️ 保護你的 Token

1. **不要分享 Token**: Token 等同於你的密碼
2. **不要提交到 Git**: 確保 `mcp_settings.json` 在 `.gitignore` 中
3. **定期更換 Token**: 建議每 90 天更換一次
4. **發現洩漏立即撤銷**: 如果 Token 不小心洩漏，立即到 GitHub 撤銷

### 撤銷 Token

如果需要撤銷 Token：

1. 前往 GitHub Settings → Developer settings → Personal access tokens
2. 找到你的 Token
3. 點擊 **Delete** 或 **Revoke**
4. 產生新的 Token 並更新設定

---

## ✅ 完成檢查

完成本章節後，請確認：

- [ ] 已建立 GitHub Personal Access Token
- [ ] Token 已儲存到安全的地方
- [ ] `mcp_settings.json` 已正確配置
- [ ] Bob 已重新啟動
- [ ] Bob 可以列出你的 repositories
- [ ] Bob 可以讀取 Issues
- [ ] 了解如何保護 Token 安全

---

## 🎉 恭喜！

你已經成功設定 GitHub MCP Server！Bob 現在可以幫你管理 GitHub 專案了。

**下一步**: 👉 [Fork Repository](./04-fork-repository.md)



