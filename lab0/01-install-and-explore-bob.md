> 📝 **備註**: IBMer 下載 Bob IDE 檔案與 Bob Shell 語法請遵照內部文件，此份專為教學使用。

# Lab 0: 安裝 Bob AI 助手與環境熟悉

> 🎯 **目標**: 在開發環境中完整安裝 Bob AI 助手。請注意，**Bob IDE (介面)** 與 **Bob CLI (手腳)** 兩者皆為必要組件，缺一不可。

---

## 🛠️ 步驟 1：安裝 Bob IDE (核心操作介面)

請先安裝核心應用程式，這將作為你與 AI 互動的主要視窗。

* **Windows**: 前往 [Bob 官網](https://bob.ibm.com/download) 下載 `.exe` 安裝檔並執行。
* **macOS**: 前往 [Bob 官網](https://bob.ibm.com/download) 下載 `.dmg`，將 **Bob.app** 拖曳至 Applications 資料夾並啟動。

---

## 🛠️ 步驟 2：安裝 Bob CLI / BobShell (核心驅動工具)
這是賦予 Bob 執行指令權限的關鍵。請注意，Bob CLI 依賴於開發環境的基礎建設。

> ⚠️ **前置需求 (Prerequisites)**:
> 在開始安裝前，請確認您的電腦已安裝 **Node.js (建議版本 v22 以上)**。
> * **驗證方式**：開啟終端機輸入 `node -v` & `npm -v `，若無版本顯示請至 [Node.js 官網]( https://nodejs.org/en) 下載。
#### **📢 Windows 使用者特別注意：環境變數 (PATH) 設定**
在 Windows 環境下，若安裝後輸入 `node -v` & `npm -v ` 顯示「無法辨識指令」，請檢查系統環境變數：
1. 按下 `Win + S` 搜尋並開啟「**編輯系統環境變數**」。
2. 點擊「**環境變數 (N)...**」按鈕。
3. 在「**使用者變數**」區塊中找到 `Path`，點選「**編輯**」。
4. 點擊「**新增**」，並貼入`C:\Program Files\nodejs`。
5. **重要**：設定完成後，必須**重啟** PowerShell 才會生效 測試 `node -v` & `npm -v `。

> 💡 **進階 Tips: 為什麼要學 CLI 模式？**
> 雖然 IDE Chat 視窗很方便，但 CLI 模式支援 **管道操作 (Piping)** 與 **自動化腳本 (Scripting)**。當你需要批次處理大量檔案，或在無介面的伺服器環境（如 SSH）操作時，CLI 將是你的最強利器。

### **方式 A：透過 VS Code 快速安裝 (推薦)**
如果你已開啟 VS Code，這是最簡單的安裝路徑：
1. 按下 `Ctrl + Shift + P` (Win) 或 `Cmd + Shift + P` (macOS)。
2. 輸入並執行指令：
   ```plaintext
   > bobide
   ```
💡 此指令會自動在背景下載並掛載 Bob 核心組件與必要的依賴環境。

### **方式 B：透過終端機手動安裝 (傳統方式)**
若方式 A 無法執行，請根據您的作業系統開啟終端機並輸入以下指令：

#### **macOS / Linux (Terminal)**
```bash
curl -fsSL https://bob.ibm.com/download/bobshell.sh | bash
```

#### **Windows (PowerShell)**
```bash
powershell -ep Bypass 'irm -Uri "https://bob.ibm.com/download/bobshell.ps1" | iex'
```

## 🚀 啟動 Bob Shell 的兩種方式

安裝完成後，你可以根據任務需求隨時切換啟動模式：

### **1. IDE 視窗模式**
此方式會在 VS Code 內部開啟專署終端機。

1. 按下 `Ctrl + Shift + P` (Win) 或 `Cmd + Shift + P` (macOS)。
2. 在 VS Code 命令選擇區輸入並執行：
   ```plaintext
   > run bobshell
   ```

### **2. Terminal CLI 模式**

如果你習慣在自己的 **Terminal** 操作，或者需要執行跨系統的任務，可以直接在終端機呼叫 Bob。

在終端機（Terminal / PowerShell）中直接輸入：

```bash
bob
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
