# 生活紀錄APP｜習慣打卡・閱讀計時・影視收藏・Podcast 收聽追蹤 Web App

專為個人日常成長與生活紀錄打造的手機優先（Mobile-First）科技極簡藍風格 Web App，整合 **每週習慣打卡追蹤**、**書籍閱讀紀錄与專注計時**、**電影／影集觀影紀錄**、**Podcast 每日收聽紀錄** 與 **Google Sheets 雲端跨裝置同步**，並完整支援 **PWA 加入手機主畫面**。

---

## 🔒 資安與隱私保護確認（上傳 GitHub 絕不外洩個人金鑰）

- **原始碼與打包檔 100% 不含個人私密金鑰**：本專案內的所有原始碼（`src/`）、後端腳本（`apps-script/Code.gs`）與打包檔案（`dist/` 及 `github-pages-直接上傳版`）**皆沒有寫死任何個人的 API Key、Token、通行碼或真實的 `Apps Script Web App URL`**，可安心上傳至公開的 GitHub Repository。
- **金鑰儲存位置**：您在 App 畫面「⚙️ 設定」中填入的網址與 API Key **只會保存在您個人手機／電腦瀏覽器的本機儲存空間 (`localStorage`)**，或由您自行保存在私人的 **Google Apps Script 指令碼屬性 (Script Properties)** 中，外人無法從 GitHub 看到您的任何金鑰或試算表網址。

---

## ✨ 核心功能模組

1. **S01 首頁（生活紀錄APP）**
   - 五大功能入口：`當週打卡`、`英語學習（開發中）`、`閱讀紀錄`、`影視紀錄`、`Podcast 每日收聽紀錄` 與 `運動紀錄（連接居家健身 App）`。
2. **S02 當週打卡**
   - 支援週次切換（`◀` / `▶` / `回到本週`）與三大即時統計卡片（`本週總達成率`、`完成次數 / 目標`、`本週閱讀專注時長`）。
   - 手機版預設以**兩欄並列收合卡片**呈現，免去上下滑動困擾；點擊任一習慣卡片即彈出專屬打卡視窗（支援週一～週日打卡、本週休息切換、編輯與刪除）。
3. **S04 ～ S09 閱讀紀錄與專注計時**
   - **創建書籍**：輸入書名、作者或 ISBN 自動透過 Google Books API 搜尋書籍封面与完整簡介，並可選擇閱讀狀態（`閱讀中` / `待看` / `已看完`）。
   - **書單一覽**：支援**「閱讀中／待看清單／已看完」與「閱讀年份」雙層小標題分組**（可自由切換 `狀態 ▸ 年份` 或 `年份 ▸ 狀態`），卡片上可直接一鍵切換閱讀狀態、編修或刪除書籍。
   - **書籍詳情與閱讀紀錄**：支援手機上下捲動與一鍵展開完整書籍摘要，並可新增、編輯或刪除每一筆閱讀計時紀錄与筆記。
4. **M01 ～ M04 影視紀錄（電影／影集／動漫）**
   - 串接 TMDB API 搜尋電影與影集海報、年份与中文簡介；支援年份小標題分組、星級評分、觀看平台、觀影心得以及作品編修與刪除。
5. **P01 ～ P05 Podcast 每日收聽紀錄**
   - 支援搜尋中英文 Podcast 節目與單集（Spotify Web API / Apple Podcasts 公開目錄雙引擎）、手動新增單集、記錄每日實際收聽分鐘數与心得收穫、查看今日／本週／本月統計，以及在收聽歷史依月份或指定日期篩選檢視。
6. **L01 心靈燈塔 Lighthouse（情緒傾訴・筆記本抄寫鼓勵卡・安心語句庫・晚間回望）**
   - **點亮今日燈塔卡**：提供「焦慮、孤單、疲憊、自我懷疑、健康擔憂、工作壓力」六種情緒與「其他感受」自由輸入，結合四種陪伴模式（溫柔安慰／理性整理／幫我停止胡思亂想／給我繼續前進的力量），產生包含**核心鼓勵（15～30字）**、**適合抄進實體筆記本的段落（80～160字）**、**「今天只需要……」小行動**與**自我提問**的燈塔卡；支援收藏、重新產生、複製文字、儲存紀錄及健康專業醫療提醒。
   - **我的安心語句庫**：依情緒分類篩選、關鍵字搜尋、取消收藏、查看日期，並支援「**隨機抽一張安心卡**」重溫過去留給自己的光。
   - **晚間回望**：每日記錄「今天最困難的事情、我是怎麼撐過來的、哪件事情最後沒有想像中糟、明天想對自己說的一句話」，支援柔和米白與靜謐夜海（亮／深色）主題切換與緩慢呼吸微光動畫。
7. **H01 ～ H04 登山紀錄（步道搜尋・山岳代表封面・登山歷程日誌・週月回顧）**
   - **步道搜尋與自建雙引擎**：支援即打即搜，同時即時比對「內建熱門步道庫（金面山、七星山、象山、劍潭山等 15 條經典路線）」與「個人自建路線庫」，查無步道時可一鍵快速自建。
   - **雙來源山岳封面**：整合 Wikimedia Commons 官方開放 API 搜尋真實山岳照片（明確標註攝影者、CC 授權與來源），以及 10 款精心設計的風格預設山岳封面（山岳稜線、森林步道、雲海日出、岩石山徑等）。
   - **快速新增登山紀錄**：必填僅「登山路線」與「登山日期」，選填實際距離 (km)、耗時、爬升 (m)、本次體感難度、個人評分 (1~5 星級)、同行山友、心得備忘與健行筆記連結。
   - **多維度登山歷史與個人圖鑑**：提供每週（週一至週日切換與次數統計）、每月（年份與月份切換）及全部紀錄（新到舊排序、關鍵字即時搜尋、年份篩選），以精美個人山岳圖鑑卡片回顧每一次登頂的感動。

---

## 🔑 如何申請、找回與設定雲端網址及 API Key

（完整步驟亦收錄於 [`docs/DEPLOYMENT.md`](./docs/DEPLOYMENT.md)）

### 1️⃣ Google Sheets 雲端網址 (`Apps Script Web App URL`)
- **首次建立**：
  1. 在 Google Drive 新增空白試算表 ➔ 點選上方 **「擴充功能」＞「Apps Script」**。
  2. 將 [`apps-script/Code.gs`](./apps-script/Code.gs) 完整貼上並儲存 ➔ 上方選單選擇 `setupSheets` 點擊 **「執行」** 完成授權與工作表建立。
  3. 點擊右上角 **「部署」＞「新增部署作業」** ➔ 類型選 **「網頁應用程式 (Web app)」**、執行身分選 **「我 (Me)」**、誰可以存取選 **「所有人 (Anyone)」** ➔ 部署後複製 `https://script.google.com/macros/s/.../exec` 網址。
- **找回已建立的網址**：
  - 打開試算表 ➔ **「擴充功能」＞「Apps Script」** ➔ 右上角 **「部署」＞「管理部署作業」** 即可複製。

### 2️⃣ Google Books API Key（選填，解決匿名配額限制）
- **首次申請**：前往 **[Google Cloud Console](https://console.cloud.google.com/)** ➔ 建立專案 ➔ 在「API 和服務 ＞ 程式庫」搜尋並啟用 **`Books API`** ➔ 在「憑證 (Credentials)」點擊 **「＋ 建立憑證 ＞ API 金鑰」** 取得 `AIzaSy...` 金鑰。
- **找回已建立的金鑰**：直接開啟 **[https://console.cloud.google.com/apis/credentials](https://console.cloud.google.com/apis/credentials)** 點擊「顯示金鑰 (Show key)」即可複製。

### 3️⃣ TMDB API Key / Read Access Token（影視紀錄搜尋電影／影集海報）
- **首次申請**：前往 **[TMDB 官網](https://www.themoviedb.org/)** 註冊登入 ➔ 點擊右上角頭像 **「設定 (Settings)」＞「API」** ➔ 選擇 **「Developer」** 填寫基本個人用途表單，即可立即取得免費 **API Key** 或 **API Read Access Token**。
- **找回已建立的金鑰**：登入後直接開啟 **[https://www.themoviedb.org/settings/api](https://www.themoviedb.org/settings/api)** 即可直接複製。

### 4️⃣ Spotify Client ID & Secret（選填，Podcast 搜尋）
- Podcast 預設支援免金鑰搜尋；若欲使用 Spotify 官方 API，可至 **[Spotify Developer Dashboard](https://developer.spotify.com/dashboard)** 點擊「Create app」（勾選 `Web API`，Redirect URI 填 `http://localhost`），進入 App 的 **Settings** 即可查看 **Client ID** 與 **Client Secret**。

### 💡 設定方式（二擇一）
- **方式 A（在 App 內設定）**：打開 App ➔ 進入「當週打卡」點擊右上角 **「⚙️ 設定」** ➔ 貼上上述網址與 API Key 並點擊「儲存設定」。
- **方式 B（推薦！設定於 Apps Script 後台，電腦與手機免重填）**：在 Apps Script 左側點擊齒輪 **「專案設定 ⚙️」** ➔ 滑到最下方 **「指令碼屬性 (Script Properties)」**，新增屬性 `GOOGLE_BOOKS_API_KEY`、`TMDB_API_KEY`、`SPOTIFY_CLIENT_ID`、`SPOTIFY_CLIENT_SECRET`（以及選用的 `API_PASSCODE`）。設定後，電腦和手機只要填第一格 `Apps Script Web App URL` 就能同步所有資料並共享後端 API 金鑰！

---

## 📂 專案重要文件

- [部署與 API 金鑰設定完整指南 (`docs/DEPLOYMENT.md`)](./docs/DEPLOYMENT.md)
- [畫面跳轉與操作流程 (`docs/USER_FLOW.md`)](./docs/USER_FLOW.md)
- [功能規格說明書 (`docs/FEATURES.md`)](./docs/FEATURES.md)
- [Google Sheets 資料模型 (`docs/DATA_MODEL.md`)](./docs/DATA_MODEL.md)
- [測試報告 (`docs/TEST_REPORT.md`)](./docs/TEST_REPORT.md)
- [Google Apps Script 後端原始碼 (`apps-script/Code.gs`)](./apps-script/Code.gs)
