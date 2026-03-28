# 5. 創建 Issues 模擬工單

> 🎯 **目標**: 在你的 Fork 專案中創建 Issues，模擬真實的開發工單

---

## 什麼是 GitHub Issues？

**GitHub Issues** 是 GitHub 內建的工單系統，用於：
- 追蹤待辦事項
- 回報 Bug
- 提出新功能建議
- 記錄開發任務
- 團隊討論

<img width="615" height="417" alt="Image" src="https://github.com/user-attachments/assets/38d94547-1276-498d-9a26-38351f757ce6" />



**為什麼要使用 Issues？**
- ✅ 清楚記錄要做什麼
- ✅ 追蹤進度
- ✅ 團隊協作
- ✅ 與 Pull Request 連結
- ✅ 自動化工作流程

---

## 前置需求

在開始前，請確保：

- ✅ 已 **Fork** modernization-demo 專案
- ✅ 已設定 **GitHub MCP Server**

---
## 步驟 1: 透過 BobShell 創建 Issue 

在正式開始遷移程式碼之前，我們需要建立一張工單（Issue）來追蹤進度。即使不開啟瀏覽器，我們也能在 **BobShell** 中完成這項操作。

#### 1. 執行指令
請確保你仍處於 `bob` 的互動介面中，並輸入以下指令：

```bash
/mode advanced

使用 MCP 在我的 modernization-demo 專案中創建一個 Issue，
    標題是 '將專案從.netcore 轉換為java 程式碼'，
    描述是 空白即可
```
#### 2. 觀察 AI 動作
Bob 會調用 **GitHub MCP** 執行以下流程：

1. **驗證專案**：確認 `modernization-demo` 存在於你的帳號下。
2. **建立工單**：自動發送 API 請求至 GitHub 建立 Issue。
3. **回傳結果**：成功後，Bob 會告知你 Issue 的編號（通常為 #1）。

#### 3. 驗證結果
你可以前往 GitHub 網頁的 **Issues** 標籤頁，確認工單已成功建立。

<img width="794" height="776" alt="Image" src="https://github.com/user-attachments/assets/f7206e40-0ae5-46e3-b597-e4ebd1b8c702" />

---

## ✅ 完成檢查

完成本章節後，請確認：

- [ ] 已建立 Issue 
- [ ] 了解如何使用 Bob 管理 Issues




---

**下一步**: 👉 [Clone Repository 到本機](./06-clone-repository.md)
