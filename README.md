# 習慣紀錄APP｜自我成長與閱讀追蹤 Web App

依據 Canva 白板設計打造的手機優先（Mobile-First）科技極簡藍風格 Web App，整合 **每週習慣打卡追蹤**、**自動書籍封面搜尋**、**閱讀專注碼表計時** 與 **Google Sheets 雲端同步**，並完整支援 **PWA 加入手機主畫面**。

---

## ✨ 核心功能模組

1. **S01 首頁（習慣紀錄APP）**
   - 四大功能入口：`當週打卡`、`英語學習（開發中）`、`閱讀紀錄`、`運動紀錄（連接居家健身 App）`。
2. **S02 當週打卡**
   - 支援週次切換（`◀` / `▶` / `回到本週`）。
   - 三大即時統計卡片：`本週總達成率`、`完成次數 / 目標`、`本週閱讀專注時長`。
   - 預載 3 個預設習慣（`英文-看一篇新聞or文章`、`看書 or 聽書 or podcast筆記`、`騎機車`），並支援於 `⚙️ 設定` 與 `✏️ 編輯` 中自由新增、修改、刪除習慣或標記本週休息。
3. **S04 ～ S09 閱讀紀錄與專注計時**
   - **S05 創建書籍**：輸入書名自動透過 Google Books API 搜尋書籍封面，支援確認選用、換一張或使用極簡預設封面；新增後自動跳轉至 **S06 書單一覽**。
   - **S06 書單一覽**：雙欄畫廊模式呈現所有書籍封面，支援書名關鍵字即時過濾。
   - **S07 書籍詳情與閱讀紀錄**：呈現書籍創建日期、書名與歷史閱讀紀錄表格（閱讀日期、閱讀時長、備註）；點擊「回首頁」返回 **S04 閱讀紀錄主選單**。
   - **S08 新增閱讀紀錄**：選擇日期與下拉選單中的書籍，自動顯示已儲存的書籍封面，點擊「開始計時」進入碼表頁。
   - **S09 閱讀碼表計時**：精準時間戳記差值計時器（防手機休眠誤差）、支援暫停／繼續、撰寫閱讀備註，點擊「結束」自動儲存並跳轉至該書詳情頁。

---

## 🛠️ 技術架構

- **前端框架**：React 18 + TypeScript + Vite
- **UI 樣式**：Tailwind CSS（科技極簡藍主題 + `Noto Sans TC` 繁體中文字型）
- **路由管理**：React Router v6 (`HashRouter` 相容 GitHub Pages 靜態子路徑重新整理)
- **PWA 支援**：`vite-plugin-pwa` (Manifest, 192/512 Icons, Apple Touch Icon, Service Worker 自動更新)
- **雲端資料庫**：Google Sheets + Google Apps Script (`LockService` 併發控制 + `text/plain` 跨域安全通訊)

---

## 📂 專案重要文件

- [畫面跳轉與操作流程 (`docs/USER_FLOW.md`)](./docs/USER_FLOW.md)
- [功能規格說明書 (`docs/FEATURES.md`)](./docs/FEATURES.md)
- [Google Sheets 資料模型 (`docs/DATA_MODEL.md`)](./docs/DATA_MODEL.md)
- [部署與雲端設定指南 (`docs/DEPLOYMENT.md`)](./docs/DEPLOYMENT.md)
- [測試報告 (`docs/TEST_REPORT.md`)](./docs/TEST_REPORT.md)
- [Google Apps Script 後端原始碼 (`apps-script/Code.gs`)](./apps-script/Code.gs)
