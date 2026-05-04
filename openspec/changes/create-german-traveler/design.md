## Context

`france-traveler` 是一個 507 行的單一 HTML 靜態頁面，以 Tailwind CSS CDN、Web Speech API 與 Firebase 為核心。點擊詞句按鈕即觸發 `speak()` 朗讀，並更新頂端大字顯示區；手機橫放時切換到全螢幕模式方便對方閱讀。Firebase 僅用於儲存偏好語音，屬輕度使用。

目標是以最小改動複製此架構，產出 `german-traveler/index.html`，對象是前往德語區（德國、奧地利、瑞士）的台灣旅客，詞句內容要針對當地文化習慣重新設計。

## Goals / Non-Goals

**Goals:**
- 產出一個能直接在瀏覽器開啟（含 GitHub Pages）的單一 HTML 檔案
- 語音合成使用 `de-DE`，以 Web Speech API 驅動
- 詞句內容針對德國在地情境：Deutsche Bahn 鐵路、Pfand 押金、Apotheke 藥局、Biergarten 文化、Siezen 敬語規範等
- 語音偏好以 localStorage 儲存（純靜態，免 Firebase）
- 視覺主題帶德國風格（黑紅金配色調整）

**Non-Goals:**
- 不建立多語言切換功能（純德語版）
- 不保留 Firebase（移除後端依賴）
- 不修改 france-traveler 任何檔案
- 不追加 PWA、Service Worker 等功能

## Decisions

### 決策 1：localStorage 取代 Firebase

**選擇**：`localStorage.setItem('preferred-de-voice', voiceName)` 儲存偏好語音。

**理由**：Firebase 設定需要 `__firebase_config` 注入（Claude AI 環境專用），直接部署到 GitHub Pages 無法運作。localStorage 純靜態、零依賴，對「記住偏好語音」這個唯一的持久化需求已足夠。

**替代方案**：保留 Firebase — 增加設定複雜度且有環境依賴，不值得。

---

### 決策 2：詞句組織方式採八大類、固定句＋模板句並用

**選擇**：
1. 日常禮貌（Alltag）
2. Deutsche Bahn 鐵路購票
3. 超市與購物（Pfand / Kasse）
4. 餐廳與啤酒花園
5. 飯店住宿
6. 藥局（Apotheke）
7. 詢問地點模板（Wo ist…?）
8. 緊急求助

**理由**：德國旅遊與法國旅遊的痛點不同——火車（DB App / Schalter 窗口購票）、超市押金瓶回收（Pfand）、藥局購藥，是台灣旅客最常措手不及的場景，法語版沒有對應的類別，需要從頭設計。

---

### 決策 3：保持「Siezen」正式敬語為預設

**選擇**：所有對話句型預設使用 `Sie`（您）敬語形式。

**理由**：在德國面對陌生人、店員、車站服務員時，使用 `du` 可能被視為無禮，`Sie` 是旅遊情境的安全選擇。說明文字中會提示這一點。

---

### 決策 4：模板句人數選擇改為德語基數詞

**選擇**：`ein / zwei / drei / vier / fünf / sechs` 對應數字 1–6，搭配 `Person / Personen` 單複數變化。

**理由**：法語版用 `une/deux/trois…` 的邏輯相同，但德語名詞格變化需同步處理（`für eine Person` / `für zwei Personen`）。

## Risks / Trade-offs

- **德語語音可用性** → 部分裝置（尤其舊版 iOS）可能無內建德語語音；在設定面板加入提示，建議用戶前往系統設定下載 `Deutsch (Deutschland)` 語音包
- **敬語覆蓋不全** → 某些緊急用語（如「救命！」`Hilfe!`）不涉及敬語，不需特別說明；複雜的格變化情境在詞句中直接給出完整句子，不要求用戶自行組合
- **瑞士德語差異** → 應用以標準德語（Hochdeutsch）為準，瑞士德語（Schweizerdeutsch）口語差異大，不在範圍內；在說明中標注「適用德國 / 奧地利，瑞士德語區以英語或標準德語溝通同樣有效」
