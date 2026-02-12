# 目前最佳版本備忘 (Best Version Snapshot)

此檔案記錄目前公認最佳的 UI/版面設定，之後若要調整可對照此版本。

---

## 結構概要

- **單一 HTML**：`index.html` 含樣式、結構與遊戲邏輯。
- **方向鍵**：僅一組，來自 HTML `.controls`（▲▼◀▶），無 Canvas 內虛擬 D-pad。
- **Canvas**：無外層 `game-wrapper`，直接放在 `layout-main` 內；圓角矩形（16px 桌機 / 18px 手機）。

---

## 版面邏輯

### 桌機 (min-width: 769px)
- Canvas：`height: 90vh`、`width: auto`，以高度等比縮放，不水平拉伸；圓角 16px。
- 方向鍵：`position: fixed`、右下角（right: 40px, bottom: 40px），後方有深色圓角底板（`.controls::after`）。
- 主容器：`layout-desktop` 寬度 `max-width: 100%`。

### 手機直向 (max-width: 768px) 與 直向平板 (max-width: 1024px + orientation: portrait)
- **2:1 比例**：`layout-main` 使用 `grid-template-rows: 2fr 1fr`，上 2/3 給 Canvas、下 1/3 給方向鍵。
- **水平置中**：`justify-items: center`、`align-items: center`；方向鍵 `position: static`、`margin: 0 auto`，在版面內不裁切。
- Canvas：圓角 18px，`max-height: 100%` 配合 grid 第一格。
- 底部留安全距離：`padding-bottom: max(12px, env(safe-area-inset-bottom))`。

### 手機橫向 (max-width: 1024px + orientation: landscape)
- 方向鍵：`position: fixed`、右下角（right / bottom 含 safe-area）。
- Canvas：略小於螢幕、圓角 18px、等比縮放。

---

## 內容與互動

- **周清月的記者證**：以 HTML 跳窗（`#popup`）顯示，不畫在 Canvas 內；進入互動區顯示、離開關閉。
- **背景**：深色漸層（body）；裝 Canvas 的區塊為透明底。
- **淡入**：主要區塊有 `fade-in-soft` 動畫。

---

## 檔案狀態

- 記錄日期：約 2025–02（依專案修改日）。
- 若之後要「回到這版本」，可依此備忘還原版面與行為；或使用 Git 在此 commit 打 tag（例如 `git tag best-ui-v1`）。
