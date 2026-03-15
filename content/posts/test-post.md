---
title: "我做了一個 Markdown 編輯器"
date: 2026-03-14
tags: ["工具", "Web", "Markdown"]
draft: false
---
最近用純 HTML + JavaScript 做了一個跑在瀏覽器裡的 Markdown 編輯器，不需要安裝任何東西，開啟即用。
功能特色

分割畫面：左側編輯、右側即時預覽，中間分隔線可以拖動調整比例
多分頁：可以同時開啟多個文件，分頁顯示修改狀態
格式工具列：一鍵插入粗體、斜體、程式碼、連結、標題、列表、引用
鍵盤快捷鍵：Ctrl+B 粗體、Ctrl+I 斜體、Ctrl+K 連結、Ctrl+S 儲存
開啟 / 儲存：支援本機 .md 檔案讀取與下載
字數統計：即時顯示目前字數

使用方式
直接在下方編輯器輸入 Markdown 語法，右側會同步渲染結果。
點擊工具列的 ⊕ 開啟 可載入本機 Markdown 檔案，↓ 儲存 可下載為 .md。

{{< rawhtml >}}
<iframe
  src="/tools/markdown-editor.html"
  style="width:100%;height:600px;border:none;border-radius:8px;overflow:hidden;"
  loading="lazy"
  title="Markdown Editor">
</iframe>
{{< /rawhtml >}}