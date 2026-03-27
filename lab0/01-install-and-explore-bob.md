> 📝 **備註**: IBMer 下載 Bob IDE 檔案與 Bob Shell 語法請遵照內部文件，此份專為教學使用。

# Lab 0: 安裝 Bob AI 助手與環境熟悉

> 🎯 **目標**: 在開發環境中完整安裝 Bob AI 助手（含 IDE 與 BobShell CLI），並熟悉其核心運作模式 (Modes)。

---


## 步驟 1：安裝 IDE  (核心操作介面)

### Windows 使用者
1. **下載**: 前往 [Bob 官方網站](https://bob.ibm.com/download)，點擊 **Download for Windows** 下載 `.exe` 安裝檔。
2. **安裝**: 雙擊執行安裝檔，按照引導完成安裝。
3. **啟動**: 安裝完成後，Bob 會自動整合並啟動 VS Code。

### macOS 使用者
1. **下載**: 前往 [Bob 官方網站](https://bob.ibm.com/download)，點擊 **Download for macOS** 下載 `.dmg` 檔案。
2. **安裝**: 雙擊 `.dmg` 並將 **Bob.app** 拖曳至 **Applications** 資料夾。
3. **啟動**: 從應用程式資料夾啟動 Bob，系統會自動開啟 VS Code。

---

## 步驟 2：安裝 BobShell CLI (命令列介面工具)

BobShell 是一個命令列介面（CLI），讓你不需開啟 VS Code 也能在 Terminal 中與 Bob 進行對話。

### 前置需求
- ✅ 已完成步驟 1，成功安裝 Bob IDE
- ✅ Bob IDE 至少啟動過一次

### macOS 使用者

1. **開啟 Terminal**
2. **執行安裝指令**：
```bash
curl -fsSL https://bob.ibm.com/download/bobshell.sh | bash
```
3. **驗證安裝**：
```bash
bob --version
```

### Linux 使用者

1. **開啟 Terminal**
2. **執行安裝指令**：
```bash
curl -fsSL https://bob.ibm.com/download/bobshell.sh | bash
```
3. **驗證安裝**：
```bash
bob --version
```

### Windows 使用者

1. **開啟 PowerShell**（以系統管理員身分執行）
2. **執行安裝指令**：
```powershell
powershell -ep Bypass 'irm -Uri "https://bob.ibm.com/download/bobshell.ps1" | iex'
```
3. **驗證安裝**：
```powershell
bob --version
```

### 測試 BobShell

安裝完成後，在終端機輸入：
```bash
bob
```

應該會進入 Bob 的互動模式，顯示類似以下的歡迎訊息：
```
Welcome to Bob Shell!
Type 'help' for available commands or start chatting.
>
```

輸入 `exit` 或按 `Ctrl+C` 可以退出 BobShell。

---

## 認識 Bob AI 運作模式 (Modes)


<img src="https://github.ibm.com/user-attachments/assets/7d9faebf-e94e-4c18-a0cd-e53001ee0954" width="400">

Bob 提供多種專門針對特定開發情境優化的 **運作模式 (Modes)**。透過切換模式，系統會調整其邏輯推理深度與內建工具集，以確保產出結果符合當前的開發階段。

### 為什麼需要切換模式？
選擇正確的模式能優化開發工作流並帶來以下效益：
* **工具集聯動 (MCP Support)**：例如 `Advanced` 模式可調用外部 **MCP Server**（如 GitHub, Instana），執行跨系統自動化操作。
* **上下文感知優化**：如 `Plan` 模式具備更強的專案全局掃描能力，適合架構分析。
* **產出精確度**：`Code` 模式會過濾冗餘解釋，直接提供高品質、可執行的代碼片段。

### 核心模式功能說明

| 模式名稱　　　　　　| 功能定位　　　　　 | 最佳使用場景 (效益)　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　 |
| :--------------------| :-------------------| :----------------------------------------------------------------------------------------------|
| **❓ Ask**　　　　　 | **通用知識檢索**　 | **技術諮詢與概念解釋**。適用於查詢語法定義、架構概念或一般性技術問題。　　　　　　　　　　　　|
| **📝 Plan**　　　　 | **任務規劃與分析** | **需求拆解與系統設計**。系統會分析專案目錄結構，協助產出實作步驟或邏輯分析報告。　　　　　　　|
| **💻 Code**　　　　 | **程式碼實作**　　 | **具體編碼與重構**。專注於產生高品質代碼實作，減少非技術描述，提升開發效率。　　　　　　　　　|
| **🛠️ Advanced**　　　| **工具集成與遷移** | **複雜場景與工具操作**。支援 **MCP Server** 擴充，包含 Github MCP Server。 |
| **🎯 Orchestrator** | **多代理協作編排** | **複雜任務自動化**。協調多個 AI 代理協同工作，適用於需要多步驟、跨領域的大型任務執行與管理。　|


---


## 初始狀態互動嘗試

在尚未開啟任何專案原始碼的情況下，請點擊 **VS Code 右側的 Bob 對話框**，嘗試切換不同模式並輸入以下指令，觀察其回饋差異：


#### **1. ❓ 切換至 Ask 模式**

<p align="left">
  <img width="700" alt="Ask Mode Chat" src="https://github.ibm.com/user-attachments/assets/767dc383-268c-4aa9-b45b-d2ad4a0c4595">
  <br>
  <em>(於 Ask 模式下進行初步對話測試)</em>
</p>

> **輸入指令：**
> 「請比較單體架構 (Monolithic) 與微服務架構 (Microservices) 在金融系統中的優缺點。」

---

#### **2. 📝 切換至 Plan 模式**

> **輸入指令：**
> 「如果我要進行 .NET 到 Java 的系統遷移，請幫我列出標準的分析流程與準備清單。」

---

#### **3. 💻 切換至 Code 模式**

> **輸入指令：**
> 「請提供一個 Java 實作 Singleton Pattern (執行緒安全) 的標準寫法。」

---

#### **4. 🛠️ 切換至 Advanced 模式**

> **輸入指令：**
> 「在 .NET 轉 Java 的現代化過程中，針對 decimal 到 BigDecimal 的型別轉換有哪些安全規範？」
---

#### **5. 🎯 切換至 Orchestrator 模式**

> **輸入指令:**
> 「請協調多個步驟來分析這個專案的架構,並產生一份包含依賴關係圖和重構建議的完整報告。」

---

## ✅ 模式熟悉度檢查清單

在進入下一步之前，請確認：
- [ ] 已成功安裝並在 VS Code 中看到 Bob 視窗。
- [ ] 已掌握在 Bob 視窗底部切換 **Modes** 的操作方式。
- [ ] 理解 **Advanced** 模式具備使用 **MCP Server** 擴充工具的能力。
- [ ] 已成功於右側對話框發送指令並獲得回應。

---

## 🎉 恭喜完成！

你已經成功安裝並初步熟悉了 Bob AI 助手的操作模式。

**下一步**: 👉 [設定 Git MCP Server，賦予 Bob 檔案操作權限](./02-setup-git-mcp.md)
