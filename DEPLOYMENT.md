# 部署與雲端 API 金鑰設定完整指南 (DEPLOYMENT & API KEYS GUIDE)

本文件說明如何部署 **Google Sheets + Google Apps Script 雲端後端**、如何申請與找回 **Google Books / TMDB / Spotify API 金鑰**，以及 **GitHub Pages 前端自動部署與資安保護機制**。

---

## 🔒 資安與隱私保護說明（上傳 GitHub 絕不外洩個人金鑰）

1. **原始碼與打包檔零金鑰硬編碼**：
   - 本專案所有前端程式碼（`src/`）、打包成品（`dist/`、`github-pages-直接上傳版`）與後端腳本（`apps-script/Code.gs`）**皆不包含任何個人 API Key、Token、通行碼或真實的 `script.google.com/macros/s/.../exec` 網址**。
2. **金鑰僅儲存在您的私人環境**：
   - **方式 A（在 App 畫面「⚙️ 設定」中輸入）**：所有網址與 API Key 僅儲存在**您當前手機或電腦瀏覽器的本機儲存空間 (`localStorage`)**，不會上傳至 GitHub，其他人打開您的 GitHub Pages 網址看到的會是空白的設定欄。
   - **方式 B（推薦！設定於 Google Apps Script「指令碼屬性 Script Properties」）**：將 API Key 存在您私人 Google 帳號下的 Apps Script 後台屬性中。如此一來，手機與電腦只要貼上第一格 `Apps Script Web App URL`（搭配選用的 `API_PASSCODE`），就能直接透過後端代理搜尋書籍、電影與 Podcast，**換手機或平板也不必重新輸入那一長串 API Key**！

---

## 一、建立與找回 Google Sheets + Google Apps Script Web App URL

### A. 首次建立步驟
1. **建立 Google Sheets 試算表**：
   - 前往您的 Google Drive，新增一份空白的 **Google 試算表**，命名為 `生活紀錄APP資料庫`。
2. **開啟 Apps Script 編輯器**：
   - 在試算表上方選單點擊 **「擴充功能 (Extensions)」 ➔ 「Apps Script」**。
3. **貼上後端程式碼**：
   - 將本專案 [`apps-script/Code.gs`](../apps-script/Code.gs) 檔案中的所有內容，完整複製並取代 Apps Script 編輯器中的預設內容，按 `Ctrl + S` 儲存。
4. **初始化工作表**：
   - 在上方函式下拉選單選擇 `setupSheets`，點擊 **「執行 (Run)」**。
   - 第一次執行時，Google 會跳出「需要授權」視窗，請依序點擊：**審查權限 ➔ 選擇您的 Google 帳號 ➔ 進階 (Advanced) ➔ 前往專案（不安全）➔ 允許 (Allow)**。
   - 執行完成後，試算表會自動建立或無損升級 8 張工作表：`Books`、`ReadingLogs`、`Habits`、`HabitLogs`、`MediaLibrary`、`WatchRecords`、`PodcastEpisodes`、`PodcastListenRecords`。
5. **部署為網頁應用程式 (Web App)**：
   - 點擊右上角 **「部署 (Deploy)」 ➔ 「新增部署作業 (New deployment)」**。
   - 選取類型：**「網頁應用程式 (Web app)」**。
   - **執行身分 (Execute as)**：選擇 **「我 (Me)」**。
   - **誰可以存取 (Who has access)**：選擇 **「所有人 (Anyone)」**（讓 GitHub Pages 能跨網域連線）。
   - 點擊 **「部署」**，複製產生的 **網頁應用程式網址 (`https://script.google.com/macros/s/.../exec`)**。

### B. 已經建過，要去哪裡找回網址？
- 打開您的 Google 試算表 ➔ 點擊上方 **「擴充功能」＞「Apps Script」** ➔ 點擊右上角藍色 **「部署」＞「管理部署作業」**，即可直接看到並複製 `https://script.google.com/macros/s/.../exec` 網址。

---

## 二、如何申請與找回各項 API Key（皆為免費申請）

### 1️⃣ Google Books API Key（書籍封面與簡介搜尋）

> 💡 **說明**：不填也能直接搜尋書籍；若遇到免費匿名共用配額上限，填入自己的 Key 即可享有每日免費專屬配額。

- **如何申請（首次建立）**：
  1. 前往 **[Google Cloud Console](https://console.cloud.google.com/)** 並登入 Google 帳號。
  2. 點擊左上角「選取專案」➔ **「新增專案」**（名稱隨意，例如 `LifeRecordApp`）➔ 建立。
  3. 在頂部搜尋欄搜尋 **`Books API`**（或由左側「API 和服務」＞「程式庫」進入），點擊 **「啟用 (Enable)」**。
  4. 點選左側 **「API 和服務」＞「憑證 (Credentials)」** ➔ 點擊上方 **「＋ 建立憑證」＞「API 金鑰 (API key)」**。
  5. 複製產生的 `AIzaSy...` 開頭金鑰。
- **如何找回已建立的金鑰**：
  - 直接打開 **[https://console.cloud.google.com/apis/credentials](https://console.cloud.google.com/apis/credentials)**，在「API 金鑰」列表點擊 **「顯示金鑰 (Show key)」** 即可複製。

---

### 2️⃣ TMDB API Key / Read Access Token（影視紀錄電影、影集與動漫海報搜尋）

- **如何申請（首次建立）**：
  1. 前往 **[TMDB 官網 (The Movie Database)](https://www.themoviedb.org/)** 註冊免費帳號並完成信箱驗證。
  2. 登入後點擊右上角頭像 ➔ **「設定 (Settings)」** ➔ 左側選單點選 **「API」**。
  3. 點擊申請 API Key ➔ 選擇 **「Developer」** ➔ 滑到底部點擊 **「Accept」**。
  4. 表單填寫方式：
     - **Application Type**：選 `Personal` 或 `Website`
     - **Application Name**：`生活紀錄 App`
     - **Application URL**：填您的 GitHub Pages 網址或 `http://localhost`
     - **Application Summary**：`Personal movie and TV show tracking app for my own reading and watching logs.`
     - 其餘聯絡資訊填妥送出後，即可立即獲得 **API Key** 與 **API Read Access Token**（兩者任選一個貼入皆可）。
- **如何找回已建立的金鑰**：
  - 登入後直接打開 **[https://www.themoviedb.org/settings/api](https://www.themoviedb.org/settings/api)**，頁面上即會顯示您的 **API 金鑰** 與 **API 讀取存取權杖**。

---

### 3️⃣ Spotify Client ID & Client Secret（選填，Podcast 單集搜尋）

> 💡 **說明**：Podcast 模組預設已內建免金鑰公開搜尋後援（Apple Podcasts / iTunes 台灣公開目錄），不填也能直接搜尋中英文 Podcast 並一鍵在 Spotify 開啟。若想使用 Spotify 官方 Web API 搜尋，可依下列步驟申請：

- **如何申請與找回**：
  1. 前往 **[Spotify Developer Dashboard](https://developer.spotify.com/dashboard)** 並登入 Spotify 帳號。
  2. 點擊 **「Create app」**：
     - **App name**：`生活紀錄 App`
     - **Redirect URIs**：填 `http://localhost`
     - **Which API/SDKs are you planning to use?**：勾選 `Web API` ➔ 儲存。
  3. 點進建立好的 App ➔ 點擊右上角 **「Settings」**，即可看到 **Client ID**，點擊 **「View client secret」** 即可看到 **Client Secret**。

---

## 三、在 App 或 Google Apps Script 中設定金鑰（兩種方式）

### 方式一：直接在 App「⚙️ 設定」視窗填入（最快速）
1. 打開 App ➔ 進入「當週打卡」➔ 點擊右上角 **「⚙️ 設定」**（或由影視／Podcast 頁面的設定按鈕進入）。
2. 依序貼上：
   - **Apps Script Web App URL**：`https://script.google.com/macros/s/.../exec`
   - **API 通行碼**：若未設定可留空
   - **Google Books API Key**：`AIzaSy...`
   - **TMDB API Key / Read Access Token**：您的 TMDB 金鑰
   - **Spotify Client ID / Secret**：選填
3. 點擊 **「儲存設定」** 或 **「測試雲端同步」** 即可。

### 方式二：設定在 Google Apps Script「指令碼屬性」（跨電腦／手機免重填推薦！）
若不想每次換手機或清除瀏覽器快取都要重填金鑰，可打開您的 **Google Apps Script 編輯器** ➔ 點擊左側齒輪 **「專案設定 (Project Settings) ⚙️」** ➔ 滑到最下方 **「指令碼屬性 (Script Properties)」** ➔ 點擊 **「新增指令碼屬性」**，填入以下屬性名稱：

| 屬性名稱 (Property) | 值 (Value) 說明 |
| :--- | :--- |
| `API_PASSCODE` | （選填）您自訂的通行碼，防止外人呼叫您的 Web App 網址 |
| `GOOGLE_BOOKS_API_KEY` | （選填）您的 Google Books API Key (`AIzaSy...`) |
| `TMDB_API_KEY` | （選填）您的 TMDB API Key 或 Read Access Token |
| `SPOTIFY_CLIENT_ID` | （選填）您的 Spotify Client ID |
| `SPOTIFY_CLIENT_SECRET` | （選填）您的 Spotify Client Secret |

設定完成後按儲存，往後任何裝置只要填第一格 `Apps Script Web App URL`，就能直接透過後端安全呼叫所有搜尋 API！

---

## 四、GitHub Pages 部署設定

1. **方式 A（GitHub Actions 自動建置部署）**：
   - 將專案推送至 GitHub Repository 的 `main` 分支。
   - 進入 GitHub Repository ➔ **Settings** ➔ **Pages** ➔ **Build and deployment** 下的 **Source** 選擇 **「GitHub Actions」**。
   - 每次推送更新時，[`.github/workflows/deploy.yml`](../.github/workflows/deploy.yml) 會自動打包並發布。
2. **方式 B（直接上傳打包好的靜態檔）**：
   - 亦可直接將 `github-pages-直接上傳版` 資料夾內的所有檔案上傳至您的 GitHub Pages 分支根目錄。
