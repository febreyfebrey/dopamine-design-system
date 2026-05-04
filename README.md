# Dopamine Design System

Memphis-poster + 多巴胺配色的迷你 design system。純 CSS、無依賴、手機優先。

> 從「支出管理」專案抽出的元件庫，可以直接 drop 到任何專案用。

---

## 快速開始

複製 `dopamine.css` 到你的專案，然後：

```html
<!doctype html>
<html lang="zh-Hant">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <link rel="stylesheet" href="dopamine.css" />
</head>
<body>
  <button class="btn primary">開始用</button>
</body>
</html>
```

完整可運行範例：[`starter.html`](starter.html) / 視覺型錄：[`examples.html`](examples.html)

---

## 設計原則

1. **手機優先**：mobile-first RWD，桌機是補強
2. **少色多空**：白底 + 黑字 + dopamine 重點色當點綴
3. **節制使用色彩**：主色（粉）只在主動作（FAB / primary button）；成員身份用色塊
4. **無 emoji**：用文字 / SVG / 純色塊代替
5. **設計 tokens 為主**：所有值都來自 `:root`，沒有 magic numbers

---

## Tokens

### Colors

| Token | 值 | 用途 |
|-------|-----|------|
| `--bg` | `#fafaf7` | 頁面底色（米白） |
| `--surface` | `#ffffff` | 卡片底 |
| `--surface-2` | `#f3f3ef` | 次層 / hover |
| `--border` | `#e8e8e2` | 邊框 |
| `--border-strong` | `#d2d2cb` | 強調邊框 |
| `--text` | `#1a1a22` | 主要文字 |
| `--text-muted` | `#5e6170` | 次要文字 |
| `--text-subtle` | `#9498a4` | 弱文字 |
| `--accent` | `#F65BA8` | 主色（桃紅） |
| `--accent-hover` | `#E04590` | 主色 hover |
| `--accent-soft` | `#FCE2EE` | 主色淡底（focus glow） |
| `--positive` | `#3FA856` | 正向（已付） |
| `--warn` | `#E89A2B` | 警示（未付） |
| `--negative` | `#E5446D` | 危險 |

**Dopamine 色盤**（給成員、tag 等識別色）：
- `--dopa-red`：`#F4583C` 紅橘
- `--dopa-yellow`：`#FBD33F` 太陽黃
- `--dopa-green`：`#3CD060` 鮮綠
- `--dopa-blue`：`#3D7DD5` 寶藍
- `--dopa-pink`：`#FF8FB5` 粉
- `--dopa-lavender`：`#B48BD9` 薰衣草
- `--dopa-mint`：`#5DD4A8` 薄荷
- `--dopa-coral`：`#FF7B5C` 珊瑚

### Spacing scale (4px base)

```
--s-1: 4px      tight (label→input)
--s-2: 8px      related items
--s-3: 12px     compact padding
--s-4: 16px     default section gap (最常用)
--s-5: 20px     large card padding
--s-6: 24px     major section
--s-8: 32px     huge breaks
```

### Border radius

```
--r-xs:  6px    badges
--r-sm:  8px    inputs / 小按鈕
--r-md:  10px   buttons
--r-lg:  12px   row cards
--r-xl:  14px   primary cards / modals
--r-pill 999px  chips / pills
```

### Type scale

```
--fs-xs:   11px   tiny labels
--fs-sm:   12px   captions / hints
--fs-base: 13px   body
--fs-md:   14px   primary content
--fs-lg:   16px   card amount / heading
--fs-xl:   20px   stat values
--fs-hero: 32px   hero amount
```

---

## 元件

### Buttons

```html
<button class="btn primary">儲存</button>
<button class="btn ghost">取消</button>
<button class="btn danger">刪除</button>
<button class="btn small">小按鈕</button>
<button class="icon-btn">×</button>
```

### Cards

```html
<!-- 大卡 -->
<div class="card">
  <h3>標題</h3>
  <p>內容</p>
</div>

<!-- 列表卡（可點擊、有 hover lift） -->
<div class="row-card">
  <strong>項目</strong>
  <span>$1,234</span>
</div>
```

### Chips

```html
<div class="chips">
  <button class="chip active">全部</button>
  <button class="chip">已付</button>
  <button class="chip">未付</button>
</div>
```

### Badges

```html
<span class="badge paid">已付</span>
<span class="badge unpaid">未付</span>
<span class="badge share">分攤</span>
<span class="badge settled">已結算</span>
<span class="badge neutral">中性</span>
```

### Member pill (色塊識別)

```html
<span class="member-pill" style="--c:#3D7DD5;">Febrey</span>
<span class="member-pill" style="--c:#FF8FB5;">Ivan</span>
<span class="member-pill small" style="--c:#3CD060;">小尺寸</span>
```

### Forms

```html
<div class="field">
  <label>家庭名稱</label>
  <input type="text" placeholder="例：我家" />
</div>

<div class="grid-2">
  <div class="field">
    <label>金額</label>
    <input type="number" />
  </div>
  <div class="field">
    <label>日期</label>
    <input type="date" />
  </div>
  <div class="field grow">
    <label>備註</label>
    <input type="text" />
  </div>
</div>

<p class="hint">提示文字</p>
```

### Modal

```html
<div class="modal">
  <div class="modal-backdrop" data-close></div>
  <div class="modal-panel">
    <div class="modal-header">
      <h3>標題</h3>
      <button class="icon-btn" data-close>×</button>
    </div>
    <div class="modal-body">
      <!-- content -->
      <div class="modal-footer">
        <div class="spacer"></div>
        <button class="btn ghost" data-close>取消</button>
        <button class="btn primary">儲存</button>
      </div>
    </div>
  </div>
</div>
```

加 `.modal-panel-wide` 變寬版。預設手機從底部滑上來、桌機置中。

### Toast

```html
<div class="toast">已儲存</div>
```

### FAB（手機底部主按鈕）

```html
<button class="fab" aria-label="新增">＋</button>
```

### Menu sheet（右上選單）

```html
<div class="menu-sheet">
  <div class="modal-backdrop" data-close></div>
  <div class="menu-panel">
    <button class="menu-item">設定</button>
    <button class="menu-item">匯出</button>
    <hr class="menu-divider" />
    <button class="menu-item danger">刪除</button>
  </div>
</div>
```

### Confetti decoration（可選裝飾）

```html
<div class="confetti" aria-hidden="true">
  <span class="confetti-piece p-tri" style="--c:#F4583C; --r:18deg;  --sz:1.6; top:90px;  left:4%;"></span>
  <span class="confetti-piece p-bar" style="--c:#FBD33F; --r:-25deg; --sz:1.3; top:118px; right:3%;"></span>
  <span class="confetti-piece p-dot" style="--c:#3CD060; --sz:1.0;            top:30%;  right:18%;"></span>
  <span class="confetti-piece p-sq"  style="--c:#3D7DD5; --r:18deg;  --sz:1.4; top:50%;  left:5%;"></span>
</div>
```

形狀：`p-tri`（三角）/ `p-bar`（長條）/ `p-dot`（圓點）/ `p-sq`（方塊）。  
變數：`--c`（顏色）/ `--r`（旋轉角度）/ `--sz`（大小倍數，0.7~1.6 自然）。

> 要讓 confetti 在內容後面、卡片之間露出來，需要把主要內容容器設成 `position: relative; z-index: 1`。

---

## 客製化

### 換主色

在你的 CSS 蓋掉就好：

```css
:root {
  --accent: #4FA3DD;          /* 改成藍色 */
  --accent-hover: #3D8FCF;
  --accent-soft: #DCEEFC;
  --shadow-fab: 0 8px 24px -6px rgba(79, 163, 221, 0.5);
}
```

### 換字級

```css
:root {
  --fs-base: 14px;            /* 整體放大 */
  --fs-md: 15px;
  --fs-lg: 17px;
}
```

### 暗色模式（自己加）

預留暗色變數：

```css
@media (prefers-color-scheme: dark) {
  :root {
    --bg: #1a1a22;
    --surface: #25252e;
    --surface-2: #2f2f3a;
    --text: #f0f0f5;
    /* ... */
  }
}
```

> 目前 v1.0 只有亮色，暗色待你需要時自己加（推薦從這裡的 token 結構延伸）。

---

## 瀏覽器相容

- 用了 `color-mix()` （member pill 透明度）— 需要 Chrome 111+ / Safari 16.2+ / Firefox 113+
- 用了 `@media (max-width: 480px)` 等基本 RWD — 全瀏覽器
- 沒用任何 preprocessor、build tool、polyfill

如果要支援更舊瀏覽器，把 `color-mix()` 改成手動設好的 hex：

```css
.member-pill {
  background: var(--c);  /* 直接用色，沒透明度 */
  opacity: 0.15;
  /* ...或 fork dopamine.css 自己挑 */
}
```

---

## 檔案

| 檔案 | 說明 |
|------|------|
| `dopamine.css` | 全部 tokens + components（單檔） |
| `examples.html` | 視覺型錄（每個元件都 demo） |
| `starter.html` | 空白起手模板 |
| `README.md` | 本文件 |

---

## 授權 / 修改

這是個人專案抽出的東西，隨便用、隨便改、不用問。

如果你發現新 use case 需要的元件還沒有，**抽出後 PR / 直接加進 dopamine.css** 的對應 section。
