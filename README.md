# 蘑菇守望 PWA v0.3

一個可在 iPhone Safari、Android Chrome、Windows 瀏覽器使用的靜態 PWA。**無需 Mac、Flutter、Firebase、帳號或遊戲登入。**

## 功能
- 多個蘑菇位置，各自設定 1～1440 分鐘倒數，預設 5 分鐘
- 到期時，若網頁仍在前景，顯示提示、嘗試播放短聲與震動（依瀏覽器支援）
- 手動記錄特殊蘑菇與好友邀請
- localStorage 本機資料保存、JSON 匯出與匯入
- HTTPS 下可註冊 Service Worker，加入主畫面，快取供離線開啟

## 在 iPhone 使用（最簡單）
1. Windows 將**本資料夾內的所有檔案**（index.html、style.css、app.js、sw.js、manifest.webmanifest、icons 資料夾）上傳到 GitHub repository 根目錄。
2. GitHub repository → Settings → Pages → Build and deployment → Deploy from a branch → main / (root) → Save。
3. 待 GitHub Pages 產生 `https://帳號.github.io/專案名稱/` 網址，在 iPhone 的 Safari 開啟。
4. 點「分享」→「加入主畫面」→「加入」，從主畫面啟動「蘑菇守望」。
5. 輸入位置及預估分鐘數，使用「設定 → 測試提醒」測試畫面與聲音。iOS 必須允許使用者互動才能初始化聲音，靜音模式也可能影響提示。

## 在 Windows 本機測試
在專案目錄執行 `python -m http.server 8000`，瀏覽器開啟 `http://localhost:8000`。本機 HTTP 網站的 Service Worker 支援因環境而異；正式測試請使用 HTTPS 的 GitHub Pages。

## 已知限制，請務必了解
- **沒有可靠的 iPhone 背景倒數提醒。** 在 iOS，網站 JavaScript 計時器不能在 App 關閉/背景時保證觸發通知。iOS 16.4+ 加入主畫面的 PWA 可用 Web Push，但必須另外部署推播伺服器與訂閱、授權。此版沒有伺服器，所以**不具備背景推播**。
- 這個 PWA 不會讀取《Pikmin Bloom》遊戲資料，不能自動偵測蘑菇，也不會自動讀取好友邀請通知。
- 特殊蘑菇回報目前只有本機記錄，沒有社群共享。
- 預設 5 分鐘是**可調整的估算**，不保證官方重生機制或位置固定。
- 紀錄在當前瀏覽器的本機儲存空間，其他裝置不會自動同步。清理網站資料可能會清空紀錄。
- 本工具與 Niantic / Pikmin Bloom 無官方關聯。

## 專案結構
`index.html` UI；`style.css` 介面；`app.js` 本機狀態、倒數及備份；`sw.js` 離線快取；`manifest.webmanifest` PWA 安裝設定；`icons/` 圖示。
