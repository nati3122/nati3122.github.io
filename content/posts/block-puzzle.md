---
title: "Block Puzzle — 我做的方塊消除遊戲"
date: 2026-03-15
tags: ["遊戲", "Web", "JavaScript"]
draft: false
---
用純 HTML + JavaScript 做的方塊益智遊戲，不需安裝、開啟即玩，支援手機觸控與桌面拖曳。
玩法
把下方的方塊拖曳到網格上，填滿整行或整列就會消除得分。同時消除越多條，Combo 加成越高。放不下任何方塊時遊戲結束。

最高分自動儲存在瀏覽器
遊戲進度重整後自動恢復
支援 PWA，可加到手機主畫面離線遊玩

原始碼
github.com/nati3122/block-puzzle

{{< rawhtml >}}
<iframe
  src="/games/block-puzzle/index.html"
  style="width:100%;height:780px;border:none;border-radius:10px;overflow:hidden;"
  loading="lazy"
  title="Block Puzzle">
</iframe>
{{< /rawhtml >}}