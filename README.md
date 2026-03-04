# Naming Refactor Pro 🚀 (Gemini Extension)

> 「程式碼是寫給人看的，只是順便讓機器執行。」 —— 命名重構專家。

**Naming Refactor Pro** 是一個專為 Gemini CLI 設計的高級擴充功能。它將 Gemini 轉化為頂尖的 **架構審查官 (Architectural Reviewer)**，專注於透過「語意化命名」與「靜態約束」來重構程式碼，將技術債轉化為具備長期可維護性的資產。

---

## 核心價值 (Core Principles)

本工具在執行重構時嚴格遵循以下四大原則：

1.  **功能保全 (Functional Integrity)**：嚴禁改動任何邏輯運算。重構範圍僅限於標識符（Identifier）更名，確保行為與原始版本 100% 一致。
2.  **規範權威 (Standard Compliance)**：
    *   **Python**: 遵循 [PEP 8](https://peps.python.org/pep-0008/) 規範。
    *   **PHP**: 遵循 [PER Coding Style](https://www.php-fig.org/per/coding-style/) (繼承 PSR-12)。
    *   **JavaScript**: 遵循現代 ES6+ 規範 (`camelCase`, `PascalCase`)。
    *   **Golang**: 遵循 [Effective Go](https://go.dev/doc/effective_go) 規範。
    *   **Bash**: 遵循 `snake_case` 命名並嚴格使用 `local` 變數。
3.  **語意優先 (Semantics over Brevity)**：拒絕晦澀的縮寫，寧可使用較長但具描述性的名稱（例如：將 `sub_st` 改為 `is_subscription_active`）。
4.  **批判性審視**：自動診斷語意模糊的命詞（如 `data`, `info`, `process`, `handle`），並主動尋找更具體的替代方案。

---

## 指令說明 (Commands)

### `/refactor-name [path]`

**描述**：深度診斷並重構指定路徑下代碼的函數與變數名稱。

**執行流程 (Workflow)**：
1.  **目標確認**：掃描指定路徑下的文件。
2.  **批判性分析**：列出目前命名中的問題清單（如：命名不一致、語意模糊等）。
3.  **重構提案**：產生對照表（Old Name -> New Name）並提供每一項更改的**批判性理由**。
4.  **授權執行**：在使用者確認後，使用 `replace` 或 `write_file` 進行精確替換。
5.  **最終校對**：檢查命名衝突。

---

## 支援語言

本擴充功能內建針對以下語言的最佳實踐：

| 語言 | 命名規範 | 關鍵特點 |
| :--- | :--- | :--- |
| **Python** | PEP 8 | `snake_case`, 強調明確意圖 |
| **PHP** | PER/PSR-12 | 現代 PHP 物件導向命名 |
| **JavaScript** | ES6+ | `camelCase` 變數, `PascalCase` 類別 |
| **Golang** | Effective Go | `camelCase`, 介面以 `er` 結尾 |
| **Bash** | Snake Case | 強制 `local` 作用域 |

---

## 安裝方式

1. 確保已安裝 [Gemini CLI](https://github.com/google/gemini-cli)。
2. 將此擴充功能目錄放置於您的 Gemini 擴充路徑下：
   ```bash
   git clone https://github.com/your-repo/gemini-extension-refactor-name.git
   ```
3. 在專案目錄下即可開始使用。

---

## 範例展示

**重構前 (`bad_code.js`):**
```javascript
function d(u) {
  let r = u.st === 1;
  return r;
}
```

**重構提案理由:**
- `d` -> `isActiveUser`: 函數應為強而有力的動詞。
- `u` -> `userRecord`: 體現資料實體。
- `r` -> `isSubscriptionActive`: 布林值應體現狀態。

**重構後:**
```javascript
function isActiveUser(userRecord) {
  let isSubscriptionActive = userRecord.status === 1;
  return isSubscriptionActive;
}
```

---

## 開發者

*   **Author**: wenchi0920
*   **Version**: 1.0.0
*   **License**: MIT

---
*注意：本工具僅進行標識符更名，建議在重構後運行您的單元測試（Unit Test）以確保迴歸正確性。*
