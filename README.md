# Soul Chill 官網重設計

**建立**：2026-07-11 15:40（Fable 5 產出 v1 Demo）
**v2**：2026-07-11 16:10（沉浸式改版，見下方 v2 設計筆記）
**v2.1**：2026-07-11 20:50（10 張小靈魂插畫上線，ChatGPT 產圖由 Jesse 提供、已去背）
**取代**：Wix 舊站 https://soulchillstudio.wixsite.com/soulchillstudio
**狀態**：v2.1 已部署 GitHub Pages（Jesse 手機確認中）

插畫對應位置：瑜珈/孕婦/頌缽/徒手/植物上板 五張課程卡、Fish 介紹卡（打坐）、每月活動主圖（抱抱家族）、夜間緩降框（月亮）、小語2（跑步）、小語3（山丘）。原始檔在 Jesse 的 ~/Downloads（ChatGPT Image 2026-07-11 16:12 系列）。

## v2 設計筆記（2026-07-11）

Jesse 的 brief：「像走進我們的教室」= 老屋手作感、柔光、滿屋植物、黃色雲彩牆、淡淡香氣；進站「不急著告訴你什麼」，像 Headspace 一樣可愛（跟 LOGO 一樣），網站會呼吸。

參考定錨：氛圍基底 Ffern（收斂版）、互動放鬆 Calm/Open（呼吸圓）、溫度 Headspace（吉祥物微動畫）。

v2 加入的東西：
- **呼吸開場**：進站小幽靈帶你吸 4 秒吐 4 秒（點任意處跳過；同 session 只播一次；prefers-reduced-motion 自動略過）
- **雲彩牆背景**：奶油黃/碧空/草植三色柔光雲塊全站緩慢漂移（= 教室的黃色雲彩油漆）
- **小幽靈**（`assets/mascot.png`，從主 LOGO 去背取出）：Hero 飄浮 + 深綠段探頭 + 課程卡 LOGO 磚
- **蕨葉 SVG**：Hero 兩角手繪感蕨葉輕輕搖（= 教室的鹿角蕨）
- **心靈小語 × 4**：段落間的呼吸點 + 文楷金句（品牌金句庫）
- **新動線**：先照片牆「走進來看看」→ 老師 → 才是課程（= Jesse 的「先看大家在這裡的樣子」）
- **字體**：標題與小語改 LXGW WenKai TC（霞鶩文楷），手寫課本感
- **照片牆**：拍立得式微旋轉 + 文楷手寫感圖說
- 捲動浮現改成「霧慢慢散開」（blur 漸清）

## 檔案結構

```
projects/soulchill官網/
├── index.html      # 整個網站（單一檔案：HTML + CSS + JS 全在裡面）
├── assets/         # 照片（已壓縮）+ LOGO
└── README.md       # 本檔
```

預覽方式：直接雙擊 `index.html` 用瀏覽器打開即可，不需要任何伺服器。

## 設計決策

- **單頁式**：品項多但每項資訊淺，一頁滾動 + 錨點導覽最適合「統一入口」的定位；未來單一品項要深入（例如跑班報名頁）再開子頁面連過去
- **雙線視覺**：動線「先喜歡跑步」用草植綠 `#b9ca74`、靜線「用心生活」用碧空藍 `#76d9d5`，完全依 brand_naming_map §8 CIS
- **不放課表與價格**：課表、價格常變動，網站只講「有什麼」，最新資訊一律導去官方 LINE。這是維護成本最低的分工
- **命名對齊 brand_naming_map §3**：傑西跑步班 / Soul Chill Park Run / 1:1 個人課表 / 慢慢進步 / 夜間緩降計畫，一字不差

## 待 Jesse 補的素材（照片換掉即可，檔名不變）

| 檔案 | 現況 | 理想 |
|---|---|---|
| `assets/tree_up.jpg`（瑜珈團體課卡片） | 大樹氛圍照代打 | 教室瑜珈課實拍 |
| `assets/tree_bench.jpg`（孕婦瑜珈卡片＋空間租借卡片） | 公園大樹代打 | 孕婦瑜珈實拍＋教室空間照 |
| `assets/fern_hand.jpg`（頌缽卡片） | 蕨葉照代打（氛圍尚可） | 頌缽實拍 |
| 徒手調整、植物上板課兩張卡片 | 目前用 LOGO 磚 | 各一張實拍（放進 assets/ 後改 index.html 對應 `<img src>`） |
| Fish 形象照（關於我們） | 目前用手寫字 placeholder | Fish 個人照一張 |

## 待確認的資訊

- 教室地址（台北／台中）要不要放 footer？目前只寫「台北・台中」
- Threads 帳號 handle（要放的話補進「找到我們」）
- 官方 LINE 用的是舊官網上的 `lin.ee/ipjH3LI`；repo 裡另有 `lin.ee/rMpSGFV` 與 `@104wzemj`，如果主窗口不同要換

## 目前的預覽網址（GitHub Pages，2026-07-11 上線）

- **公開預覽**：https://soulchillstudio.github.io/soulchill-website/
- 部署 repo：https://github.com/soulchillstudio/soulchill-website（公開，只放網站檔案）
- **主檔仍在本 repo**（`projects/soulchill官網/`），這裡是 source of truth；改完後要重新部署：

```bash
cd "/Users/jesse/Documents/Soul Chill Agents/projects/soulchill官網"
rsync -av --delete --exclude .git ./ ~/.soulchill-website-deploy/
cd ~/.soulchill-website-deploy && git add -A && git commit -m "update site" && git push
```

（部署工作目錄 `~/.soulchill-website-deploy/` 若不存在，`git clone https://github.com/soulchillstudio/soulchill-website.git ~/.soulchill-website-deploy` 一次即可）

## 正式上線方案（買網域後）

1. 買網域（例如 soulchill.tw）
2. 兩個選項：
   - **GitHub Pages 綁自訂網域**（現成，加 CNAME 即可）
   - **Cloudflare Pages**（跟現有 soulchill-forms Worker 同帳號，之後表單/報名整合更順）

## 維護方式

- 所有文案直接改 `index.html`，各區塊有 `<!-- ═══ 區塊名 ═══ -->` 註解標記
- 顏色統一在 CSS 開頭 `:root` 變數，改一處全站生效
- 換照片：丟新照片進 `assets/`（建議寬 ≤1600px、壓 80% 品質），改對應 `<img src>`

## 改站前的設計體檢紀律（2026-07-13 立）

> 來源：Nate（Skool）的前端設計 CLAUDE.md。整份是為「用 Tailwind 像素級複刻參考圖」寫的，多半不適用本站（純手寫 CSS 的沉浸式品牌站）。只抽下面兩條真正有用的，其餘（Tailwind、參考圖複刻、Windows Puppeteer 路徑）不採用。

**紀律 1｜改完站別只用肉眼看，跑一次截圖體檢（尤其手機）**

1. 本機起 server（避免 file:// 的資產路徑怪癖）：
   `cd "projects/soulchill官網" && python3 -m http.server 8000`
2. 截兩個寬度：手機 390px、桌機 1280px（在這個環境請我用 playwright MCP 截）
3. 把圖讀進來逐項比對，講**具體**差異、不是「感覺怪怪的」：字級、間距、對齊、色號、圓角、陰影
4. 至少跑兩輪，改到沒有可見差異為止
   • 手機那關是重點：v2.1 之前的「iOS 無限下捲」就是一次手機截圖比對會當場抓到的東西

**紀律 2｜動 CSS／換圖前先回 `docs/brand_cis/` 拿真資產**

• 顏色只用 `:root` 裡的 CIS 變數（`--forest` / `--grass` / `--sky` / `--cream`…），不臨時新增即興 hex
• 換圖優先用 `docs/brand_cis/`（插畫在 `06_吉祥物_插畫/`、實拍在 `03_照片庫`），placeholder 只是暫代、要換掉

**⚠️ 反向護欄｜不要引進「高質感 SaaS」那套**

Nate 檔的 anti-generic guardrails（多層 radial 漸層、噴砂噪點、疊層陰影、把每個面做高低差）是為行銷落地頁寫的。本站定位是「低設計才像 Jesse 本人」（memory `feedback_story_authentic`）。小靈魂、呼吸開場、文楷的溫度優先於 polish。想加「質感」時先問一句：這是讓站更溫暖，還是更像新創官網？
