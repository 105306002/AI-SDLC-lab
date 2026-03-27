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
- ✅ 已安裝 **Node.js**（版本 16 或以上）


### 檢查 Node.js 版本

開啟終端機（Terminal）並執行：

```bash
node --version
```

應該顯示類似：`v18.x.x` 或更高版本

如果沒有安裝 Node.js：
- **Windows**: 前往 [nodejs.org](https://nodejs.org) 下載安裝
- **macOS**: 使用 Homebrew: `brew install node`

---

# 🔧 Git MCP Server 設定指南

本指南將引導你透過 **Bob** 設定 Model Context Protocol (MCP)，串接 Git 工具以強化 AI 的版本控制能力。

---

## 📥 設定步驟

### 步驟 1: 找到 MCP 設定檔

你可以選擇手動路徑搜尋，或透過 VS Code 介面直接開啟。

#### 方法 A: 手動路徑開啟
1. 在 VS Code 中按下 `Ctrl+P` (Windows) 或 `Cmd+P` (macOS)。
2. 輸入路徑並按 **Enter**：
   - **Windows**: `C:\Users\<你的使用者名稱>\.bob\settings\mcp_settings.json`
   - **macOS**: `~/.bob/settings/mcp_settings.json`

<img width="800" alt="path" src="https://github.ibm.com/user-attachments/assets/34e23b51-7804-41b7-a4c6-dca99efd5253" />

---

#### 方法 B: 使用 VS Code 介面開啟
1. 按下 Bob 插件介面右上角的齒輪 **Settings**。
   <img width="734" alt="set" src="https://github.ibm.com/user-attachments/assets/ba59255c-da0f-4a52-b71f-a53816cadfe7" />
2. 在選單中選取 **MCP**。
3. 找到 **Global MCP** 區塊，按下 **Open**。
   <img width="600" height="500" src="https://github.ibm.com/user-attachments/assets/f9b4a774-6966-48a7-a59b-21f3bf7919d0" />
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

<img width="618" alt="status" src="https://github.ibm.com/user-attachments/assets/b4b6c250-15d7-4188-a0d6-20225fa3611c" />

### 方法 2: 使用 Bob 測試對話
1. 開啟 Bob 聊天面板。
2. 輸入：`請使用 Git MCP Server 查看目前的 Git 狀態`
3. Bob 應會自動呼叫工具並回傳結果。

---

## 🧪 CLI 測試工具清單

開啟終端機並執行以下指令，確認 Git MCP 工具是否已成功掛載：

```bash
/mcp list
```

<img width="1512" alt="git_cli" src="https://github.ibm.com/user-attachments/assets/a52bdf33-254f-49ae-8517-a7b27ac2a094" />

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
1. 確認 Node.js 已正確安裝：`node --version`
2. 重新安裝 Node.js
3. 重新啟動終端機 VSCode

### 問題 2: Git MCP Server 啟動失敗

**症狀**: Bob 顯示「Git MCP Server 連接失敗」

**解決方法**:
1. 檢查 `mcp_settings.json` 語法是否正確（JSON 格式）
2. 確認 Git 已安裝：`git --version`
3. 查看 Bob 的錯誤日誌（VSCode 輸出面板）
4. 嘗試手動執行：`npx -y @cyanheads/git-mcp-server`

### 問題 3: Bob 無法執行 Git 操作

**症狀**: Bob 說「我無法執行 Git 操作」

**解決方法**:
1. 確認已重新啟動 Bob
2. 檢查 MCP Server 是否正在運行
3. 嘗試切換到 Advanced 模式（Bob 右上角）並且 Bob 解決 error


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



