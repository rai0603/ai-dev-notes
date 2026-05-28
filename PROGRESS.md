# ai-dev-notes — 進度

## 2026-05-29 — PROJECT 06 AICMS 開發日記頁完成 + 實機截圖整合

### 新增頁面：`notes/aicms.html`（首篇 /notes/ 子頁）

「想喝牛奶最後蓋了一座牧場」AICMS 開發故事頁。沿用 ai-dev-notes 黑黃 design tokens，860 wrap，獨立 nav + footer。

頁面結構：
- Hero（PROJECT 06 tag + 5 格統計：4 週 / 8 痛點 / 4 外掛 / 3 App / 1 牧場）
- 需求漂移三階段（🥛 → 🤔 → 🐄，5/03 / 5/06 / 5/07）
- 8 大痛點 × 解決方案（每張 pain card 含 problem / solution 兩欄 + 技術 tag）
- 4 週 × 11 條工作軸甘特圖 + 12 個里程碑卡片
- 外掛市集 bonus banner（牧場全景）
- Closing CTA 連到 ai-cms.cc

8 痛點對應：架站匯入 / no-code 編輯 / 預約系統 / 排班系統 / 員工 portal / AI 客服 / 上線一條龍 / 內建 Analytics。

### 首頁 `index.html` 新增 PROJECT 06 卡片

仿 PROJECT 05 結構，badge `badge-large` 大型專案，footer 連到 `notes/aicms.html` 跟 `ai-cms.cc`。

### 對外連結：每張 pain card 底部加 ai-cms.cc 行銷頁連結

- Pain 1: wordpress-import + geo-native-site
- Pain 2: geo-native-site
- Pain 3 / 4 / 5 / 7 / 8: solution（預約、排班、portal、上線、Analytics 段落）
- Pain 6: ai-chat-booking + mcp-gateway

`pain-foot` 結構：mono 字 + 金線 underline，hover 反白。

### 實機截圖 18 張整合 + PII 模糊

從 `/Users/waterman/Developer/AICMS/實機截圖/` 取 19 張原圖，用 Python + PIL 處理：

- 重命名為語義檔名（p1-media / p2-editor / p3-orders / p4-coaches / p6-mcp / p7-checklist / p8-overview ...）
- PII 區域 Gaussian blur radius=18：
  - `p3-orders.png`：訂單管理客人欄整條（姓名+電話）
  - `p3-group.png`：教練 chip 真名 + 客戶區（姓名+電話+email）
  - `p4-coaches.png`：教練名單姓名+email+電話三欄
- 其餘 15 張無 PII，直接 copy

腳本：`/tmp/process_aicms_screenshots.py`（給定百分比座標、批次處理）。

每張 pain card 對應截圖布局：
- Pain 1: 2-col（媒體庫 + nav）
- Pain 2: 3-col（編輯器 + FAQ + Hero）
- Pain 3: 2-col（訂單 + 散客團）
- Pain 4: 2-col（排班週視圖 + 教練名單）
- Pain 6: 4 張 2×2 grid（KB + persona + 安全 + MCP）
- Pain 7: 1 張 full width（GEO 自檢）
- Pain 8: 3-col（總覽 + 即時 + 縣市）
- Bonus: full-width banner（外掛市集）

互動：點任何截圖彈 lightbox 全螢幕（ESC 關閉）。

### FB 貼文文案（給 user 自行發布）

3 版迭代後定稿：純文字、不用奇怪符號、8 個痛點用「一、」起頭分段、術語替換成一般人能懂的中文（搜尋優化 / 拖拉式編輯器 / 給未來 AI 接的介面 等）。

### Git

3 commits push 到 main：

- `6d989fd` Add PROJECT 06 AICMS + 開發日記頁面
- `6894ddf` Add marketing-site cross-links to each pain card
- `8e7afc0` Add 18 實機截圖 + lightbox + 外掛市集 bonus banner

GitHub Pages auto-deploy 完成。線上：

- https://rai0603.github.io/ai-dev-notes/notes/aicms.html
- https://rai0603.github.io/ai-dev-notes/（首頁 PROJECT 06 卡片）

### 啟用的新模式

`notes/<slug>.html` 子頁系統正式啟用，aicms.html 是首篇。未來加新筆記照此模式（HTML 自帶 nav 回首頁 + 沿用 design tokens + lightbox JS 可抄）。

未來其他專案若也想開發開發故事頁，可參考 aicms.html 結構：Hero 三段故事 + 痛點對照卡片 + 甘特圖 + 外連 + bonus banner + closing CTA。
