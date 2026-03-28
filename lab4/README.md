# Lab 4: 提交與 Pull Request

> 🎯 **目標**: 使用 Bob 將實作完成的程式碼提交至 GitHub 新分支，並建立與 Issue 關聯的 Pull Request (PR)。

---

## 📋 前置需求

- [ ] ✅ 已完成 Lab 0 至 Lab 3
- [ ] ✅ 本地 Java 程式碼已完成實作
- [ ] ✅ 所有單元測試皆已通過 (`mvn test` 顯示綠燈)

---

## 📖 學習目標

完成本 Lab 後，你將學會：
- 透過 **Bob IDE** 自動化執行 Git 指令（建立分支、提交程式碼）。
- 使用 **GitHub MCP Server** 遠端建立 Pull Request。
- 讓 Bob 自動將 PR 連結至對應的 GitHub Issue。
- 體驗從需求到交付的完整 **AI 輔助開發生命週期 (SDLC)**。

---

## 🔧 步驟概覽

### 步驟 1: 提交程式碼並建立 PR
在 **Bob IDE (VS Code 對話框)** 中輸入以下指令。Bob 將會自動幫你處理分支出現、檔案暫存、提交以及推送到雲端的操作。

**指令範本：**
```text
使用 MCP 建立一個名為 `feat/modernization-java` 的新分支，將所有變更提交上去，並根據我的 Issue 建立一個 Pull Request 到 main 分支。
```

---

## 📁 預期輸出
完成本 Lab 後，你應該達成以下結果：

- [ ] **GitHub 分支**：雲端已出現 `feat/modernization-java` 分支。
- [ ] **Pull Request**：GitHub 上已成功建立 PR，且標題與內容清楚描述了本次遷移。
- [ ] **Issue 連結**：PR 頁面的右側顯示已連結到對應的開發 Issue。
<img width="685" height="353" alt="Image" src="https://github.com/user-attachments/assets/0d361328-5f1c-4b14-a9c8-eb56897e9cfc" />

---

## ✅ 驗證檢查
- [ ] **變更確認**：在 GitHub PR 頁面檢查 "Files changed"，確認包含 Java 程式碼與測試檔。
- [ ] **描述完整性**：PR 的描述是否清楚說明了這是一個從 .NET 遷移至 Java 的變更？


---

## 🎉 恭喜完成！

**你已經完成了整個 AI 輔助開發流程！** 🚀

從 **分析設計 (Lab 1)** → **程式碼實作 (Lab 2)** → **單元測試 (Lab 3)** → **提交 PR (Lab 4)**，你已經親身體驗了如何利用 AI Agent 提升開發效率並確保品質。

這就是現代化軟體開發的全新樣貌！
