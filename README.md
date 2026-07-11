# Soul Chill 官網重設計

**建立**：2026-07-11 15:40（Fable 5 產出 v1 Demo）
**取代**：Wix 舊站 https://soulchillstudio.wixsite.com/soulchillstudio
**狀態**：v1 Demo，待 Jesse 回饋

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
