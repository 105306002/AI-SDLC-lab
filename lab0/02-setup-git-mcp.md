# 2. 設定 Git MCP Server

> 🎯 **目標**: 配置 Git MCP Server，讓 Bob 可以使用 Git MCP 執行 Git 操作

---

## 📖 什麼是 Git MCP Server？

**MCP (Model Context Protocol)** 是一個讓 AI 助手與外部工具溝通的協議。

**Git MCP Server** 讓 Bob 可以：
- 📊 查看 Git 狀態 (`git status`)
- 📝 查看提交歷史 (`git log`)
- 🔍 查看檔案差異 (`git diff`)
- 🌿 管理分支 (`git branch`)
- ➕ 暫存檔案 (`git add`)
- 💾 提交變更 (`git commit`)
- 📤 推送到遠端 (`git push`)

**為什麼需要它？**
- ✅ Bob 可以幫你執行 Git 指令
- ✅ 不需要手動切換到終端機
- ✅ Bob 可以自動分析 Git 狀態
- ✅ 提高開發效率

---

## 📋 前置需求

在開始設定前，請確保：

- ✅ 已安裝 **Bob AI 助手**（參考 [01-install-and-explore-bob.md](./01-install-and-explore-bob.md)）
- ✅ 已安裝 **Node.js**
- ✅ 已安裝 Git


### 檢查 Node.js & Git 版本

開啟終端機（Terminal）並執行：

```bash
node -v
git --version
```



如果沒有安裝 Node.js：
- **Windows**: 前往 [nodejs.org](https://nodejs.org) 下載安裝
- **macOS**: 使用 Homebrew: `brew install node`

如果沒有安裝 Git：
- **Windows**: 前往 [Git 官網](https://git-scm.com/) 下載安裝
- **macOS**: 使用 Homebrew: `brew install git`

---

# 🔧 Git MCP Server 設定指南

本指南將引導你透過 **Bob** 設定 Model Context Protocol (MCP)，串接 Git 工具以強化 AI 的版本控制能力。

---

## 📥 設定步驟

### 步驟 1: 找到 MCP 設定檔

#### 使用 VS Code 介面開啟
1. 按下 Bob 插件介面右上角的齒輪 **Settings**。
   <img width="734" height="121" alt="Image" src="https://github.com/user-attachments/assets/fa74493c-bd73-498f-9b79-5cf6329fd6cc" />
2. 在選單中選取 **MCP**。
3. 找到 **Global MCP** 區塊，按下 **Open**。
   <img width="545" height="510" alt="Image" src="https://github.com/user-attachments/assets/16d72949-4591-47fb-a2dc-c8f14abc2f6e" />
4. 系統會自動開啟 `mcp_settings.json` 檔案。

---

### 步驟 2: 新增 Git MCP Server 配置

在 `mcp_settings.json` 的 `"mcpServers"` 區塊中新增以下配置：

```json
{
  "mcpServers": {
    "git": {
      "command": "npx",
      "args": [
        "-y",
        "@cyanheads/git-mcp-server"
      ],
      "env": {
        "MCP_TRANSPORT_TYPE": "stdio",
        "MCP_LOG_LEVEL": "info"
      },
      "alwaysAllow": [],
      "disabledTools": []
    }
  }
}
```
### 設定後請`完全`關閉 Bob IDE 再重新啟動

## ⚙️ 配置說明

在 `mcp_settings.json` 中，各項參數代表意義如下：

* **`"git"`**: MCP Server 的識別名稱。
* **`"command": "npx"`**: 使用 Node.js 套件執行器。
* **`"args"`**:
    * `-y`: 自動確認安裝套件。
    * `@cyanheads/git-mcp-server`: 指定執行的 Git MCP 套件。
* **`"env"`**:
    * `MCP_TRANSPORT_TYPE`: 通訊方式（設定為 `stdio`）。
    * `MCP_LOG_LEVEL`: 日誌等級（建議設為 `info`）。

---

## ✅ 驗證設定

### 方法 1: 檢查 MCP 狀態燈號
1. 點擊 Bob 右上角的 **Settings** > **MCP**。
2. 查看 **Git** MCP Server 的狀態燈號：
    * 🟢 **綠色燈** = 設定成功，正常運作。
    * 🔴 **紅色燈** = 設定失敗，請檢查 JSON 語法或環境變數。

<img width="618" height="684" alt="Image" src="https://github.com/user-attachments/assets/e91a5a1a-c79f-4a59-8bda-f0a8f65955d2" />

### 方法 2: 使用 Bob 測試對話
1. 開啟 Bob 聊天面板。
2. 輸入：`Git MCP Server 工具有哪些`


---

## 🧪 Bob CLI 測試工具清單

開啟終端機並執行以下指令，確認 Git MCP 工具是否已成功掛載：

```bash
/mcp list
```

<img width="1512" height="982" alt="Image" src="https://github.com/user-attachments/assets/f0a0401b-953c-479e-ae1f-9145f8930cfb" />

---

## 🔍 進階設定 (Optional非必要)

### 調整日誌等級

如果需要更詳細的日誌（用於除錯）：

```json
{
  "mcpServers": {
    "git": {
      "env": {
        "MCP_LOG_LEVEL": "debug"  // 改為 debug
      }
    }
  }
}
```

日誌等級選項：
- `error`: 只顯示錯誤
- `warn`: 顯示警告和錯誤
- `info`: 顯示一般資訊（推薦）
- `debug`: 顯示詳細除錯資訊

### 停用特定工具

如果不想讓 Bob 執行某些 Git 操作：

```json
{
  "mcpServers": {
    "git": {
      "disabledTools": [
        "git_push",    // 停用推送
        "git_reset"    // 停用重置
      ]
    }
  }
}
```

### 自動允許特定操作

如果想讓 Bob 自動執行某些操作而不詢問：

```json
{
  "mcpServers": {
    "git": {
      "alwaysAllow": [
        "git_status",  // 自動允許查看狀態
        "git_log",     // 自動允許查看日誌
        "git_diff"     // 自動允許查看差異
      ]
    }
  }
}
```

---

## ❌ 常見問題排解

### 問題 1: npx 指令找不到

**症狀**: 
```
Error: npx: command not found
```

**解決方法**:
1. 確認 Node.js 已正確安裝：`node -v`
2. 重新安裝 Node.js
3. 重新啟動終端機 VSCode

### 問題 2: Git MCP Server 啟動失敗

**症狀**: Bob 顯示「Git MCP Server 連接失敗」

**解決方法**:
1. 檢查 `mcp_settings.json` 語法是否正確（JSON 格式）
2. 查看 Bob 的錯誤日誌（VSCode 輸出面板）
3. 嘗試手動執行：`npx -y @cyanheads/git-mcp-server`

### 問題 3: Bob 無法執行 Git 操作

**症狀**: Bob 說「我無法執行 Git 操作」

**解決方法**:
1. 確認已重新啟動 Bob
2. 檢查 MCP Server 是否正在運行
3. 嘗試切換到 Advanced 模式（Bob 右上角）並請 Bob 解決 error


## 📊 設定檔完整範例

以下是一個完整的 `mcp_settings.json` 範例：

```json
{
  "mcpServers": {
    "git": {
      "command": "npx",
      "args": [
        "-y",
        "@cyanheads/git-mcp-server"
      ],
      "env": {
        "MCP_TRANSPORT_TYPE": "stdio",
        "MCP_LOG_LEVEL": "info"
      },
      "alwaysAllow": [],
      "disabledTools": []
    }
  }
}
```

---



## ✅ 完成檢查

完成本章節後，請確認：

- [ ] `mcp_settings.json` 已正確配置
- [ ] Bob 已重新啟動
- [ ] Bob 可以使用MCP Server執行 `git status`
- [ ] Bob 可以使用MCP Server查看 Git 日誌
- [ ] Bob 可以使用MCP Server列出分支

---

## 🎉 恭喜！

你已經成功設定 Git MCP Server！Bob 現在可以幫你執行 Git 操作了。

**下一步**: 👉 [設定 GitHub MCP Server](./03-setup-github-mcp.md)



