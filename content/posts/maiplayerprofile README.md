---
title: "打造專屬 Maimai 玩家名片卡"
date: 2026-03-15
tags: ["遊戲", "Web", "Python"]
draft: false
---

# Maiplayerprofile：打造專屬 Maimai 玩家名片卡

這是一個基於 Gradio 的小工具，用 Python 組合本地素材，快速生成可下載的 Maimai 玩家卡影像（PNG）。非常適合想要用輕量方式形式化自己的遊戲成績展示，或在社群中分享個人風格帶牌。

## 1. 為什麼做這個專案

- Maimai 風格卡片在玩家圈非常受歡迎，但手動尋找模版、組合圖片耗時。
- 透過程式化輸入，快速得到一致視覺、可加裝圖框、角色立繪和盤面資訊。
- 離線運作，資源自由新增，不受外部 API 變動影響。

## 2. 核心功能

- 文字輸入：暱稱、稱號、Rating、段位、等級、角色ID、框ID、底板ID。
- 用量指標：支援 Mega/Lovely/EX +/-、自定義稱號與附註。
- 素材庫瀏覽：`res/images/{Chara,Icon,Frame,Plate}`，列出影像並可複製 ID 直接套用。
- 圖像輸出：生成 PNG，下載按鈕一鍵完成。

## 3. 安裝與快速啟動

```powershell
cd <project-folder>
python -m venv .venv
.\.venv\Scripts\Activate.ps1  # 或 .\.venv\Scripts\activate.bat
pip install -r requirements.txt
python app.py
```

打開 terminal 顯示的 Gradio URL，開始輸入資料、選定素材、產生卡片。

## 4. 專案結構解讀

- `app.py`：Gradio UI、輸入欄位、API 端點。
- `main.py`：從資料組合、素材貼圖、文字繪製到最終輸出。
- `res/images/`：素材夾，包含 `Chara`、`Icon`、`Frame`、`Plate` 等。

## 5. 如何自定義資源

- 新增自訂資源至：`res/images/Chara`、`Icon`、`Frame`、`Plate`。
- 命名建議：前綴 `UI_` + ID（例如 `UI_GoldenFrame.png`），系統從檔名抽出 ID，使用者可透過 ID 選取。
- 如果想加入「稀有星光框」或「限定風格」，直接把圖放進素材資料夾，重啟 app 即可。

## 6. 延伸玩法

- 生成「批量玩家卡」，例如一個 Excel 清單養成系列。
- 加入「自動更新成績」欄位，結合 Maimai API（社群、dohatama 等）。
- 轉成動態 GIF/影片，搭配音效分享在 Discord/YouTube。

## 7. 小提示

- 若素材尺寸偏差，建議使用 `Pillow` 先統一 280x280（或項目設定尺寸）。
- 設置 `output_format='PNG'`、`quality=95` 以免壓縮失真。
- 建議保留一套「預設模板」，方便快速產出固定風格卡。

---

📌 已完成：這篇貼文可直接當你的部落格內容（md）。如要，我可以再幫你加入文章封面圖片示意及圓形截圖程式碼。
