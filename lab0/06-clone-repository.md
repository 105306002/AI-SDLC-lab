## 06. Clone Repository

**🎯 目標**：將已經 Fork 到你帳號下的 `modernization-demo` 專案 **Clone**（下載）到你的本地電腦，準備開始開發。

---

### 前置需求
在開始本章節前，請確保你已完成以下準備工作：
* [ ] 已完成 **步驟 05**，成功建立 Issues。
* [ ] 已正確設定 **Git MCP Server、GitHub MCP Server**。

---

### 知識準備：什麼是 Clone？

**Clone** 是將遠端伺服器（GitHub）上的專案完全複製一份到你「本地電腦」的動作。

#### 為什麼要 Clone？
* ✅ **本地開發**：在自己的電腦上使用慣用的編輯器（如 VS Code）編寫程式。
* ✅ **離線工作**：程式碼下載後，大部分的操作（Commit, Checkout Branch）都可以在離線狀態完成。
* ✅ **同步版本**：建立本地與遠端的連結，方便後續透過 `Push` 上傳修改或 `Pull` 下載更新。

---

### 實作步驟：使用 Bob 執行本地 Clone

在傳統流程中，你需要去 GitHub 複製 SSH 或 HTTPS URL；但在 **BobShell** 中，你只需要用自然語言表達意圖，Bob 會自動找出你帳號下的專案路徑並執行下載。

#### 1. 啟動 BobShell
開啟終端機，輸入 `bob` 進入互動模式。

#### 2. 執行自然語言 Clone 指令
請確保處於進階模式，並對 Bob 輸入以下指令：

```bash
/mode advanced
使用MCP Server Clone 專案 modernization-demo repository 到本機
```

#### 3. 驗證 Clone 結果
Bob 會自動執行 clone 操作，完成後你應該會看到：
- 📁 專案資料夾已建立在本機
- ✅ Git 倉庫初始化完成
- 🔗 遠端連結已設定

---

## 📂 準備進入 Lab 1

Clone 完成後，你需要切換到專案目錄，才能繼續後續的 Lab 1 操作。

Lab 1 將使用 BobShell CLI 進行操作，你可以選擇以下兩種方式切換到專案目錄：

### 方法 1：在 BobShell 中直接切換（快速方式）

直接在當前的 BobShell 中輸入：
```bash
cd modernization-demo
```

Bob 會幫你執行 `cd` 命令並切換到該目錄。

> ⚠️ **重要提醒**：使用此方法時，雖然 Bob 會執行 `cd` 命令，但 BobShell 的提示符仍會顯示「You are in home directory」。這是正常現象，實際上目錄已經切換成功，後續的 Git 和檔案操作都會在專案目錄下執行。

### 方法 2：重新啟動 BobShell（推薦方式）

如果你希望 BobShell 的提示符正確顯示專案目錄，可以使用此方法：

1. **退出當前的 BobShell**
   
   按 `Ctrl+C` 退出

2. **在終端機中切換到專案目錄**
   ```bash
   cd modernization-demo
   ```

3. **重新啟動 BobShell**
   ```bash
   bob
   ```
   
   現在 BobShell 會正確顯示你在 `modernization-demo` 目錄下。



---

## ✅ 完成檢查

完成本章節後，請確認：

- [ ] 已成功 Clone modernization-demo 專案到本機
- [ ] 已在 BobShell 中切換到專案目錄
- [ ] 可以在檔案總管中看到專案檔案結構

---

**下一步**: 👉 [Lab 1: 分析與設計](../lab1/README.md)
