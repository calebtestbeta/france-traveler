## Why

`france-traveler` 驗證了「單一 HTML + Web Speech API」的旅遊快速翻譯架構：免安裝、即點即說、手機橫放全螢幕顯示。現在要以同樣的架構建立德語版 `german-traveler`，針對赴德（及奧地利、瑞士德語區）的台灣旅客，設計符合德國在地風土民情的常用詞句，解決旅途中對話、購票、用餐、醫療等現場溝通需求。

## What Changes

- **新建獨立單頁應用** `german-traveler/index.html`，完整複製 france-traveler 的 HTML/CSS/JS 架構
- **全面替換語言內容**：語音合成從 `fr-FR` → `de-DE`，所有法語詞句替換為德語，語音選單過濾從 `fr` → `de`
- **在地化詞句設計**：依德國旅遊情境重新設計八大類別，涵蓋：日常禮貌（Siezen 敬語文化）、Deutsche Bahn 鐵路購票、超市購物（REWE/Aldi Pfand 押金制）、餐廳與啤酒花園、飯店住宿、藥局（Apotheke）、詢問地點、緊急求助
- **模板句型更新**：人數選擇模板改為德語數詞（ein/zwei/drei…），「詢問地點」模板更換為德語常見地點
- **視覺主題微調**：標題、說明文字、配色由法國藍紅白 → 德國黑紅金（保持相同 Tailwind 架構）
- **移除 Firebase**：germany-traveler 採純靜態版本，語音偏好以 localStorage 儲存取代 Firestore，降低部署複雜度

## Capabilities

### New Capabilities
- `german-phrase-content`: 八大類 50+ 句德語詞句，依德國在地情境設計，含固定句與模板句
- `german-speech-engine`: Web Speech API 切換至 `de-DE`，語音選擇介面同步調整
- `local-voice-preference`: 以 localStorage 取代 Firebase 儲存使用者偏好語音，純靜態無後端

### Modified Capabilities
（無 — 新獨立專案，不修改 france-traveler）

## Impact

- **新目錄**：`/Users/al03182532/Documents/GitHub/german-traveler/`
- **唯一輸出**：`german-traveler/index.html`（單一自包含靜態頁面）
- **不影響**：`france-traveler/index.html` 原封不動
- **部署**：任何靜態網站託管均可（GitHub Pages、直接開啟本機均可）
