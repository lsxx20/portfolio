# Portfolio 使用說明
## 你拿到的檔案

```
portfolio/
├── index.html       首頁（作品列表 + 關於我）
├── smangus.html     Smangus case study（含互動地圖 iframe）
├── vibemap.html     ← 你要自己建，用 smangus.html 當模板
├── chempion.html    ← 你要自己建，用 smangus.html 當模板
└── assets/          ← 建立這個資料夾放截圖
    ├── smangus-hero.jpg
    ├── smangus-preview.jpg
    ├── vibemap-preview.jpg
    ├── chempion-preview.jpg
    └── ...
```

---

## 立刻要做的事（按順序）

### Step 1：截圖
截這些畫面，存到 assets/ 資料夾：

**Smangus：**
- `smangus-hero.jpg`      — 網站首頁的整體截圖（最漂亮的那張）
- `smangus-preview.jpg`   — 給首頁卡片用的預覽圖（地圖截圖）
- `basemap-toggle.jpg`    — 地圖切換的那個畫面
- `color-coded-map.jpg`   — 藍紅色點在地圖上的樣子
- `3d-model.jpg`          — 3D 地景模型
- `migration-stages.jpg`  — 遷徙路線的彩色 pin 標示

**VibeMap：**
- `vibemap-preview.jpg`   — 給首頁卡片用的預覽圖
- `vibemap-before-1.jpg`  — 現有版本的搜尋頁截圖
- `vibemap-before-2.jpg`  — 現有版本的結果頁截圖（有地圖）
（Figma redesign 截圖之後做好再加）

**ChemPion：**
- `chempion-preview.jpg`  — 給首頁卡片用的預覽圖
（Figma mockup 截圖之後做好再加）

---

### Step 2：替換 index.html 的佔位符

在 index.html 裡搜尋 `REPLACE`，一個一個換掉：

1. Hero 區塊的 `map-placeholder` → 換成 `<img src="assets/smangus-hero.jpg">`
2. 三個卡片的 `card-visual-placeholder` → 換成對應的截圖

---

### Step 3：確認 iframe 連結

在 smangus.html 裡，兩個 iframe 的 src 已經設定為：
- `https://lsxx20.github.io/mybook2/_static/maps/smangus_immigration.html`
- `https://lsxx20.github.io/mybook2/_static/maps/kinaji_marikowan_points.html`

在瀏覽器直接打開這兩個連結，確認地圖可以正常顯示。
如果路徑不對，修改 iframe 的 src 屬性。

---

### Step 4：替換 smangus.html 的截圖佔位符

搜尋所有 `REPLACE:`，換成對應的 img 標籤：
```html
<!-- 原本 -->
<div class="dot-placeholder">REPLACE: basemap-toggle.jpg</div>

<!-- 換成 -->
<img src="assets/basemap-toggle.jpg" alt="Basemap toggle" style="width:100%; display:block;">
```

---

### Step 5：建立 vibemap.html 和 chempion.html

把 smangus.html 複製兩份，改名：
- `vibemap.html`
- `chempion.html`

然後替換：
- 標題、描述、meta 資訊
- Case study 的文字內容（從 portfolio_plan_complete.md 複製）
- 截圖
- VibeMap 的 iframe 改成你的 Streamlit App 的 embed（如果支援的話）
  或者放 before/after 的截圖對比

---

## 部署到 GitHub Pages

```bash
# 在你的 GitHub 建立一個新的 repo，叫 portfolio
# 把這些檔案 push 上去

git init
git add .
git commit -m "Initial portfolio"
git remote add origin https://github.com/lsxx20/portfolio.git
git push -u origin main

# 然後去 GitHub repo 的 Settings > Pages
# Source 選 main branch
# 幾分鐘後就可以在 https://lsxx20.github.io/portfolio/ 看到
```

---

## 注意事項

**互動地圖 iframe：**
如果你的地圖 HTML 檔案在同一個 repo 裡，直接用相對路徑：
```html
<iframe src="maps/smangus_immigration.html" ...>
```

如果在另一個 repo（lsxx20.github.io/mybook2），用完整 URL：
```html
<iframe src="https://lsxx20.github.io/mybook2/_static/maps/smangus_immigration.html" ...>
```

**截圖建議：**
- 用 Chrome 的 DevTools 截圖（Cmd+Shift+P → Screenshot），解析度更高
- 或者用 Screely.com 把截圖自動加上漂亮的裝置框
- 截圖尺寸至少 1200px 寬

**字體：**
已經用 Google Fonts 載入 Syne 和 DM Sans，有網路就能看。
如果要離線使用，下載字體檔案放進去。
