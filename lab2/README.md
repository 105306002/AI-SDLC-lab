# Lab 2: 程式碼實作

> 🎯 **目標**: 使用 Bob IDE 讀取本地的設計文件（Markdown），並讓 AI 根據該設計自動產生對應的 Java 程式碼。

---

## 📋 前置需求

- [ ] ✅ 已完成 Lab 0 & Lab 1
- [ ] ✅ 本地目錄已具備設計文件（例如：`docs/architecture_spec.md` 或 `design.md`）

---

## 📖 學習目標

完成本 Lab 後，你將學會：
- 如何在 **Bob IDE** 中引用本地 Markdown 文件作為 Context（上下文）。
- 讓 Bob IDE 根據設計規範精準產生 Java 專案結構與程式碼。

---

## 🔧 步驟概覽

### 步驟 1: 讀取設計文件並產生代碼
在 **Bob IDE (VS Code 右側 Bob 對話框)** 中輸入以下指令。 

> ⚠️ **注意**：請根據你在 Lab 1 實際產出的檔案路徑與檔名來修改 `@` 後的內容（例如 `@docs/design.md`）。

**指令範本：**
```text
請讀取 @docs/你的設計文件名稱.md ，按照這份文件的架構定義，幫我寫出對應的 Java 程式碼檔案。
```

> 💡 **Bob 小教室**：使用 `@` 符號可以讓 Bob 直接「看見」該檔案內容，確保產出的程式碼完全符合你在 Lab 1 定義的規格。

---

## 📁 預期輸出

完成本 Lab 後，你的專案目錄應出現以下檔案：

- [ ] `java-api/src/main/java/.../AccountController.java`
- [ ] `java-api/src/main/java/.../AccountService.java`

---

## ✅ 驗證檢查

- [ ] **規格對照**：產出的 Java 程式碼是否符合設計文件中的端點路徑與邏輯？
- [ ] **編碼規範**：程式碼是否遵循標準 Java 命名規範（如 CamelCase）？
- [ ] **編譯檢查**：嘗試執行 `mvn compile` 確保產出的程式碼語法正確。

---

**下一步**: 👉 [Lab 3: 單元測試](../lab3/README.md)
