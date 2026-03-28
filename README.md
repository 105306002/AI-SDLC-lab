# AI-SDLC-lab 

**AI 驅動的軟體開發生命週期工作坊** > 透過 Bob AI Agent 與 MCP 協議，體驗從需求分析到程式碼交付的「零手動」開發轉型。

---

## 專案核心

本指南旨在展示 **AI-SDLC (AI-Assisted Software Development Life Cycle)** 的實踐路徑。我們將傳統的線性開發任務，轉化為由 AI 驅動的自動化工作流：

| 傳統開發 | → | AI-SDLC 自動化流程 |
|---------|---|-------------------|
| 📋 手動解讀 Issue 與撰寫文件 | → | **自動化需求分析**：從 GitHub 提取需求並產生設計文件 |
| 💻 踏踏實實逐顆重構與實作 | → | **智能程式碼生成**：根據設計規範自動產出高品質 Java 代碼 |
| ✅ 撰寫單調的單元測試 | → | **自動化測試防線**：產生 JUnit 5 測試並確保 Edge Cases 覆蓋 |
| 🚀 繁瑣的分支管理與 PR 流程 | → | **智能 Git 工作流**：透過 AI Agent 操作指令完成提交與 PR |

---

## Lab 實作路徑

本工作坊包含 5 個循序漸進的實驗室（預計總時數：1.5 - 2 小時）：

### [Lab 0: 環境設置與工具準備](./lab0/README.md) 

配置 **Bob AI** 與 **MCP Server (Git / GitHub)**，建立 AI 操作本地與遠端工具的橋樑。

---

### [Lab 1: 分析與設計](./lab1/README.md) 

練習讓 Bob 讀取 GitHub Issue 並分析舊有的 .NET 代碼，自動產出驗收標準（AC）與設計文件。

---

### [Lab 2: 程式碼實作](./lab2/README.md) 

使用 **Context-Aware** 技術，讓 Bob 讀取 Lab 1 的設計文件，精準生成 Java 業務邏輯。

---

### [Lab 3: 單元測試](./lab3/README.md) 

利用 AI 快速建立測試防線，使用 **Mockito** 進行依賴模擬，確保遷移後的代碼品質。

---

### [Lab 4: 提交與 Pull Request](./lab4/README.md) 

體驗 AI Agent 的工具操作能力，一鍵完成分支建立、代碼提交並自動關聯 Issue 建立 PR。

---

## 技術架構與工具

- **核心助教**: **Bob AI Agent** (VS Code 整合助手)
- **溝通協議**: **MCP (Model Context Protocol)** - 讓 AI 具備「手」能操作工具
- **整合工具**: Git MCP Server / GitHub MCP Server / Podman
- **範例技術棧**: .NET (Legacy) → Java & Spring Boot (Target) / JUnit 5

---

## 學習成果

完成所有實驗室後，你將能夠：

- ✅ 掌握 **AI Agent** 在日常開發中的實際應用場景。
- ✅ 理解 **MCP 協議**如何打破 AI 與本地工具之間的隔閡。


---

## 快速開始

### 前置需求

- **作業系統**: Windows 10/11 或 macOS
- **開發工具**: VS Code
- **執行環境**: Node.js 22.15+
- **版本控制**: Git
- **GitHub 帳號**: 用於 Fork 專案與建立 Issues

### 開始學習

1. **從 Lab 0 開始**
   
   前往 [Lab 0](./lab0/README.md) 完成環境設置

2. **循序完成各個 Lab**
   
   每個 Lab 都有詳細的步驟說明，建議按照順序完成


---

## 📄 授權

此專案僅供教學使用。

---

**準備好重新定義你的開發流程了嗎？** 👉 [開始 Lab 0](./lab0/README.md)
