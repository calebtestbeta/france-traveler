## ADDED Requirements

### Requirement: 語音合成使用 de-DE 語系
`speak()` 函式 SHALL 設定 `SpeechSynthesisUtterance.lang = 'de-DE'`，且優先選用裝置上名稱含 `Premium` 的 de-DE 語音；若無則 fallback 至任意 `de` 語系語音。

#### Scenario: 點擊任意詞句觸發德語語音
- **WHEN** 使用者點擊任一詞句按鈕
- **THEN** `window.speechSynthesis.speak()` SHALL 以 `lang: 'de-DE'` 的 utterance 朗讀對應德語文字，語速 `rate: 0.85`

---

### Requirement: 語音選擇列表過濾 de 語系語音
語音設定面板 SHALL 只列出 `voice.lang.startsWith('de')` 的語音；若裝置無任何德語語音，SHALL 顯示提示訊息「找不到德語語音，請至系統設定下載 Deutsch (Deutschland) 語音包」。

#### Scenario: 裝置有 de 語音時列出選項
- **WHEN** 使用者開啟語音設定面板
- **THEN** 面板 SHALL 列出所有 `lang` 以 `de` 開頭的語音，每項含名稱與「測試」按鈕

#### Scenario: 裝置無 de 語音時顯示提示
- **WHEN** 使用者開啟語音設定面板且裝置無德語語音
- **THEN** 面板 SHALL 顯示「找不到德語語音」的提示與安裝指引

---

### Requirement: 測試語音使用標準德語測試句
`testVoice()` 函式 SHALL 以 `"Guten Tag! Wie kann ich Ihnen helfen?"` 作為測試句播放，而非法語版的 `"Bonjour, comment allez-vous ?"`。

#### Scenario: 點擊測試按鈕播放德語測試句
- **WHEN** 使用者在語音設定面板點擊某語音的「測試」按鈕
- **THEN** Web Speech API SHALL 以該語音朗讀 `"Guten Tag! Wie kann ich Ihnen helfen?"`
