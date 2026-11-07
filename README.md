# 蘑菇守望 v0.5 — 附近蘑菇地圖（PWA）

可用於 iPhone Safari、Android Chrome、Windows。基於 v0.4 增加「🗺️ 地圖」頁籤：

- 手機 GPS 定位、600m / 1.5km / 3km / 10km 篩選與距離排序。
- 地圖上點選座標，手動記錄蘑菇名稱、類型、尺寸與位置。標記消失／重新出現、再次確認時間。
- 地圖與清單顯示**本機紀錄**，以及 v0.4 已授權外部 JSON 資料來源（若有設定且成功連線）。可匯入自己整理的 JSON 座標資料。
- 保留 v0.4 的倒數、特殊回報、好友邀請、資料匯出與外部雷達功能；沿用原本 localStorage key，舊紀錄不需重新輸入。

## 非即時遊戲資料

**本程式不能直接讀取 Pikmin Bloom 遊戲內蘑菇，也不能保證附近所有蘑菇完整列出。** 尚未取得可用、經授權的即時資料源。本機位置不是社群回報，外部資料需取得授權並符合 CORS 與指定 JSON 格式。沒有任何功能會要求登入遊戲帳號或讀取遊戲封包。

Safari 必須在 HTTPS 環境取得定位權限。地圖圖層需要網路存取 Leaflet CDN、OpenStreetMap 圖磚；載入地圖時會向第三方服務發出正常網路請求。地圖不載入時仍可操作文字清單。手機鎖屏／關閉 App 不會可靠背景掃描或推播。

## 更新現有 GitHub Pages

1. 下載 ZIP 解壓縮，將 **ZIP 內全部檔案與 icons 資料夾**上傳至 repo `pikmin-reminder` 的**根目錄**，覆蓋同名檔案。
2. GitHub 提交後，等待 Pages 顯示部署成功。
3. 在 iPhone 開啟 `https://kenny80268-ctrl.github.io/pikmin-reminder/`，若仍顯示舊版，關閉主畫面 PWA 或清除該網站快取，再重新整理。
4. 點「🗺️ 地圖」→「📍 定位」→ 可按「＋ 記錄附近蘑菇」新增第一筆。

## 匯入資料範例

```json
{
  "mushrooms": [
    {"name":"我記錄的公園蘑菇", "type":"紅", "size":"一般", "lat":24.16, "lon":120.64, "updatedAt":"2026-11-07T08:00:00+08:00"}
  ]
}
```

上面座標僅為**結構範例**，不是遊戲真實資料。請勿上傳包含私人位置的備份到公開 GitHub repository。

## 技術

原生 HTML/CSS/JS + Leaflet 1.9.4 CDN + OpenStreetMap 瓦片。毋須 Node、Firebase、帳號或 API key。未經 iPhone 實機與 GitHub Pages 線上部署驗證。
