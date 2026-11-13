# 修道解惑所 · SOULDRY 靈魂解渴販賣機

林瑋揚（Josh）賢德青年現場互動課的網頁系統。10 罐飲料＝10 個生活問題（渴），開罐揭曉經典答句（解渴）。

## 三個介面
| 介面 | 網址 | 用途 |
|------|------|------|
| 玩家（手機） | `index.html` | 報到、選題選組、開罐、討論上傳、互評、看成績 |
| 主講者（投影） | `host.html` | 跟著階段切換的大螢幕（QR、選題看板、座位區、倒數、報告、頒獎） |
| 後台（控台） | `admin.html` | 階段控制、分組監看、手動移組、計時、成績結算、重置 |

## 技術
- 純前端（HTML/CSS/JS），GitHub Pages 代管
- Firebase Realtime Database + Storage（專案 `souldry-7a7df`，asia-southeast1）即時同步
- 十題內容在 `data.js`、名冊在 `roster.js`、Firebase 設定在 `config.js`
- Firebase 安全規則見 `firebase-rules.md`（活動型、無登入；活動後可關閉）

> 內部活動工具，頁面皆設 `noindex`。
