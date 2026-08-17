# homework-hub — 功課練習樞紐

小朋友功課嘅互動解題動畫集（Three.js × 廣東話語音旁白），用 GitHub Pages 發佈。

## 結構（科目 → 補習班 → 年級 → 課程 → 章節）

```
index.html                        ← 揀科目（數學／中文／英文／科學）
maths/                            ← 數學
  index.html                      ← 揀課程（補習班）
  xueersi/                        ← 學而思
    index.html                    ← 揀年級（P1、P2⋯）
    p1/                           ← P1（小一）
      index.html                  ← 揀課程／學期（暑期班、秋季班⋯）
      2026-summer/                ← 2026 暑期班（7–8月）
        index.html                ← 揀 Chapter
        chapter-07/               ← Chapter 7：看圖列算式（4 條動畫）
          index.html
          q1_birds.html + birds_audio/（7 MP3）
          q2_ducks.html + ducks_audio/
          q3_fishbowl.html + fishbowl_audio/
          q4_swans.html + swans_audio/
chinese/                          ← 中文（待加）
english/                          ← 英文（待加）
science/                          ← 科學（待加）
```

## 點解要分到咁細？

同一個補習班，唔同年級、唔同學期都會有「Chapter 7」——
分開 `p1/2026-summer/` 同將來嘅 `p1/2026-autumn/`，
新課程加入嚟都唔會撞名撞路徑。

## 加新內容嘅方法

1. 行去對應嘅 `科目/課程/年級/學期/` 開新 chapter 資料夾，例如 `maths/xueersi/p1/2026-autumn/chapter-01/`
   （新學期記得加返嗰層嘅 `index.html`，抄 `2026-summer/index.html` 改）
2. 擺入動畫 HTML + 同名 `_audio/` 資料夾（MP3 同 HTML 必須同層，HTML 用相對路徑搵 MP3）
3. 加一個 `index.html` 列出該 chapter 嘅題目（抄 `chapter-07/index.html` 改，留意麵包屑層數）
4. 喺上一級 index 加一張卡
5. commit + push，1–2 分鐘後 GitHub Pages 自動更新

## 操作

- 電腦：Space 播放／暫停、→ 下一小步、← 退回、S 重置
- iPad／手機：點一下畫面＝播放／暫停（第一次點會解鎖 iOS 音頻）
- 每條動畫左下角有 🔊 靜音掣

## 技術備忘

- 動畫靠 CDN 載入 Three.js（需要網絡）
- 語音係 edge-tts（zh-HK-HiuMaanNeural）預生成嘅 MP3，相對路徑載入
- 動畫 HTML 由本地 `0020-Maths_Questions` project 嘅 pipeline 產出，呢個 repo 只擺成品