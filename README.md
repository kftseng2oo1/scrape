# 網站爬蟲策略分析器 v2

輸入網址或貼上 HTML，由 Claude 分析網站結構，產生爬蟲策略、CSS Selector 與 Python／Node.js 程式碼。

**線上使用**：https://kftseng2oo1.github.io/scrape/

## 主要功能
- 兩種輸入：🌐 輸入網址（經 Worker 抓取）、📋 貼上 HTML（F12 → Copy outerHTML）
- 自動清理 HTML、偵測是否為 SPA（需要 Puppeteer 動態爬取）
- 分析結果以串流方式逐步顯示，顯示 Token 用量
- 產出：網站結構說明、建議策略、Selector 清單、Python 與 Node.js 範例程式碼（一鍵 COPY）
- Selector 測試器：在貼上的 HTML 中高亮符合的元素
- 內建範例網站：書籍電商、Hacker News、名言靜態頁、PTT

## 技術與依賴
- 單檔 HTML PWA（`index.html` 內含全部 HTML/CSS/JS），`manifest.json` + `sw.js` 提供安裝到主畫面與離線快取。
- 後端：`arcar.kftseng2oo1.workers.dev/scrape-analyze`（SSE 串流）
- `index.html` 內附 Worker 端 `handleScrapeAnalyze` 的參考實作
