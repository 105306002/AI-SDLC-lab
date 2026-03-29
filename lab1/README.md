# Lab 1: 分析與設計

> 🎯 **目標**: 使用 Bob CLI 取得 Issue（工單）需求，分析 .NET 程式碼，並根據 Issue 與程式碼產生設計文件與驗收標準，最後更新到 Issue 的 Comment。

---

## 📋 前置需求

- ✅ 已完成 Lab 0
- ✅ 已 Fork 並 Clone `modernization-demo` 專案
- ✅ 已建立 GitHub Issues
- ✅ 已在終端機中切換到專案目錄

---

## 🚀 開始前的準備

在開始 Lab 1 之前，請確保你已經在 Bob CLI 中進入專案目錄：

### 確認工作目錄

如果你已經完成 Lab 0 的步驟 6，應該已經在 `modernization-demo` 目錄下啟動了 Bob CLI。

如果尚未啟動或需要重新啟動，請在終端機中執行：

```bash
# 切換到專案目錄
cd modernization-demo

# 啟動 BobShell
bob
```

---

## � 學習目標

完成本 Lab 後，你將學會：

- 使用 Bob CLI 取得 GitHub Issue  
- 使用 Bob CLI 分析 .NET 程式碼  
- 產生驗收標準與架構設計 Markdown 文件  
- 將設計文件更新至 Issue Comment  

---

## 🔧 步驟概覽

### 步驟 1: 使用 CLI 取得 Issue

在 BobShell（Bob CLI）切換到 Advanced Mode 並在終端機輸入：

```bash
在 modernization-demo 專案中，使用 Github MCP Server 取得我的 Issue
```
> 💡 **提示**：這步驟會觸發 GitHub MCP Server，列出你在 `modernization-demo` 專案下的所有任務。

---

### 步驟 2: 產生設計文件與驗收標準
在 **BobShell (Bob CLI)** 終端機中輸入以下指令，進行深度分析與文件產出：

```bash
使用 MCP 工具 根據我的 Issue 以及 .NET 程式碼，產生驗收標準與最佳化的 Markdown 設計文件，將設計文件儲存到專案目錄中，並將結果更新到 Issue 的 Comment 中。
```

> 💡 **提示**：Bob 會同時讀取 Issue 需求與 `.cs` 檔案邏輯，執行以下操作：
> 1. 在專案目錄下產出設計文件（例如：`docs/design.md` 或 `architecture_spec.md`）
> 2. 透過 GitHub MCP 將設計摘要回填至 GitHub Issue Comment

---

## 📁 預期輸出
完成本 Lab 後，你應該達成以下產出：

- [ ] **本地文件**：專案目錄下出現設計說明文件（例如：`design.md` 或 `architecture_spec.md`）。
- [ ] **雲端同步**：GitHub Issue（如 #1）已出現由 Bob AI 自動回覆的設計摘要與驗收標準。

---

## ✅ 驗證檢查
- [ ] **架構完整性**：設計文件是否包含完整的 .NET 與 Java 對照說明？
- [ ] **Issue 同步**：確認瀏覽器上的 Issue Comment 是否已成功更新？
- [ ] **準確性**：驗收標準是否與專案中的 `AccountService.cs` 邏輯相符？

---

**下一步**: 👉 [Lab 2: 程式碼實作](../lab2/README.md)
