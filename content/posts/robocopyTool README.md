---
title: "用 Python 封裝 Robocopy"
date: 2026-03-15
tags: ["Python"]
draft: false
---

# robocopyTool：用 Python 封裝 Robocopy

這是一個 Windows 目標導向的小工具，透過 Python 生成 `robocopy` 命令，簡化排程備份、增量同步，並加上可讀日誌與錯誤重試。

## 1. 為什麼要這個工具

- Robocopy 是 Windows 內建強大複製工具，但原生命令行語法不易記。
- 直接執行時容易忘記 `/MIR`、`/R`、`/W`、`/XO` 的細節，失誤可能導致資料遺失。
- 拿 Python 包裝可：
  - 讀 JSON / YAML 設定
  - 自動補上預設排除與保留時間
  - 失敗時重試、發送通知

## 2. 功能總覽

- 來源/目的地同步（含子目錄與屬性）
- 增量備份：`/MIR`、`/XO`、`/R:3`、`/W:5`
- 黑名單排除：`.git`、`node_modules`、`*.tmp`、`*.log`
- 日誌輸出：`robocopy.log` 及簡潔終端摘要
- 例外處理：遇到錯誤自動重試，必要時回傳系統代碼

## 3. 安裝與運行

```bash
cd <project-folder>
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python main.py
```

如果想打包 exe（方便分發）：

```bash
pip install pyinstaller
pyinstaller --onefile main.py
```

## 4. 快速範例（含參數）

假設 `config.json`：

```json
{
  "src": "C:\\source",
  "dst": "D:\\backup",
  "exclude": ["node_modules", "*.tmp", "*.log"],
  "mode": "mirror",
  "retry": 2,
  "wait": 3
}
```

`main.py` 會產生類似：

```powershell
robocopy "C:\source" "D:\backup" /MIR /XO /R:2 /W:3 /LOG+:"robocopyTool.log" /NP /NDL /NFL
```

## 5. 專案架構

- `main.py`：讀設定、建立命令、執行 shell => robocopy
- `config.json`：來源、目標、排除、模式、重試
- `requirements.txt`：需要的第三方（如 `schedule` 或 `pyyaml`，可選）

## 6. 進階功能建議

- 加入 `schedule`（或 Windows Task Scheduler）做定時執行。
- 使用 `hashlib` 對比 MD5，先校驗資料是否真的變動再複製。
- 增加「異地備份」機制，先同步到外接硬碟，再複製到網路位置。
- 整合 Email/Line 通知：備份完成、失敗、異常檔案清單。

## 7. 文章結尾可放

- 應用場景：家庭資料備份、工作文件版本管理、伺服器檔案授權保全
- 未來方向：跨平台 `rsync` + `robocopy` 的統一封裝、簡易 Web UI、歷史版本回溯

---
