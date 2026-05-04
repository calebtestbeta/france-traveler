## 1. 建立專案骨架

- [x] 1.1 建立 `/Users/al03182532/Documents/GitHub/german-traveler/` 目錄
- [x] 1.2 複製 `france-traveler/index.html` 為起點，存為 `german-traveler/index.html`
- [x] 1.3 更新 `<title>` 為「德語旅遊隨身說 - German Travel Talker」
- [x] 1.4 更新 `<meta name="description">` 為德語版說明
- [x] 1.5 移除所有 Firebase import 與初始化程式碼（`initializeApp`、`getAuth`、`getFirestore`、`__firebase_config` 相關區塊）

## 2. 語音引擎替換（german-speech-engine）

- [x] 2.1 將 `speak()` 函式中 `ut.lang` 改為 `'de-DE'`，`rate` 改為 `0.85`
- [x] 2.2 更新 Premium 語音偵測邏輯：`lang === 'de-DE' && name.includes('Premium')`，fallback 為任意 `de` 語系語音
- [x] 2.3 `refreshVoiceList()` 改為過濾 `v.lang.startsWith('de')` 的語音
- [x] 2.4 語音名稱清理：將 `replace('French (France)', '法文')` 改為 `replace('German (Germany)', '德語')`
- [x] 2.5 無德語語音時顯示提示「找不到德語語音，請至系統設定下載 Deutsch (Deutschland) 語音包」
- [x] 2.6 `testVoice()` 測試句改為 `"Guten Tag! Wie kann ich Ihnen helfen?"`

## 3. localStorage 語音偏好（local-voice-preference）

- [x] 3.1 刪除所有 `window.savePreferredVoice`、`initAuth`、Firebase Auth/Firestore 相關函式與呼叫
- [x] 3.2 `selectVoice()` 改為 `localStorage.setItem('german-traveler:preferredVoice', voice.name)`
- [x] 3.3 頁面載入時讀取 `localStorage.getItem('german-traveler:preferredVoice')` 並套用偏好語音
- [x] 3.4 語音選擇高亮邏輯：比對 localStorage 中的偏好語音名稱，呈現 ✅ 與 `border-blue-500`

## 4. 視覺主題調整

- [x] 4.1 頁首標題改為「🇩🇪 德語旅遊隨身說」
- [x] 4.2 主色調從法國藍（`blue-600`）調整：保留藍色為主色，加入黑色（`gray-900`）作為強調色，反映德國黑紅金主題
- [x] 4.3 「設定語音」按鈕文字改為德語版語音說明
- [x] 4.4 橫向模式（landscape）頂端提示文字改為「點擊下方按鈕朗讀德語」

## 5. 類別 1：日常禮貌（Alltag）

- [x] 5.1 新增 `Guten Morgen`（早安）、`Guten Tag`（你好日安）、`Guten Abend`（晚安）三個按鈕
- [x] 5.2 新增 `Danke schön`（謝謝）、`Bitte`（麻煩您）、`Entschuldigung`（不好意思）、`Es tut mir leid`（對不起）
- [x] 5.3 新增 `Sprechen Sie Englisch?`（您說英語嗎？）
- [x] 5.4 新增 `Ich verstehe nicht.`（我聽不懂）、`Können Sie das bitte wiederholen?`（可以再說一次嗎？）
- [x] 5.5 在類別標題旁加入小字說明「德語對陌生人習慣使用 Sie（您）敬語」

## 6. 類別 2：Deutsche Bahn 鐵路

- [x] 6.1 建立目的地模板句「Eine Fahrkarte nach [城市], bitte.」，城市選項：München / Berlin / Frankfurt / Hamburg / Köln
- [x] 6.2 新增單程 / 來回選擇按鈕（`einfach` / `hin und zurück`）
- [x] 6.3 新增 `Welches Gleis fährt nach [城市]?`（幾號月台？）
- [x] 6.4 新增 `Muss ich umsteigen?`（需要轉車嗎？）
- [x] 6.5 新增 `Der Zug hat Verspätung.`（火車誤點了。）、`Ist dieser Platz frei?`（這個位子有人坐嗎？）

## 7. 類別 3：超市與購物

- [x] 7.1 新增 `Wo ist die Kasse?`（收銀台在哪？）
- [x] 7.2 新增 `Ich möchte diesen Pfand zurückgeben.`（退押金瓶），按鈕附小字說明「Pfand = 押金制，空瓶放回收機退款」
- [x] 7.3 新增 `Kann ich mit Karte zahlen?`（可以刷卡嗎？）、`Haben Sie eine Tüte?`（有袋子嗎？）
- [x] 7.4 新增 `Getrennt bitte.`（分開結帳）、`Zusammen bitte.`（一起結帳）
- [x] 7.5 建立尺寸模板句 `Haben Sie das in Größe [S/M/L/XL]?`（有這個尺寸嗎？）

## 8. 類別 4：餐廳與啤酒花園

- [x] 8.1 建立人數模板句 `Einen Tisch für [N] Person(en), bitte.`，1 人用「eine Person」，2–6 人用「N Personen」
- [x] 8.2 新增 `Die Speisekarte, bitte.`（菜單）、`Zahlen bitte!`（買單），`Zahlen` 附說明「德國需主動呼叫服務員結帳」
- [x] 8.3 建立過敏模板句 `Ich bin allergisch gegen [Nüsse / Gluten / Milch / Meeresfrüchte].`
- [x] 8.4 新增 `Ein Bier bitte.`、`Ein Weißbier bitte.`、`Ein alkoholfreies Bier bitte.`
- [x] 8.5 新增 `Prost!`（乾杯！）、`Das schmeckt sehr gut!`（很好吃！）
- [x] 8.6 新增 `Kann ich eine Quittung haben?`（可以給我收據嗎？）

## 9. 類別 5：飯店住宿

- [x] 9.1 新增 `Ich habe eine Reservierung.`（我有預訂）、`Ich möchte auschecken.`（辦理退房）
- [x] 9.2 新增 `Um wie viel Uhr ist der Check-out?`（幾點退房？）
- [x] 9.3 新增 `Kann ich mein Gepäck aufbewahren?`（可以寄放行李嗎？）、`Das WLAN-Passwort, bitte.`（Wi-Fi 密碼）
- [x] 9.4 新增問題回報句：`Es gibt kein heißes Wasser.`（沒有熱水）、`Die Klimaanlage funktioniert nicht.`（冷氣壞了）

## 10. 類別 6：藥局（Apotheke）

- [x] 10.1 新增 `Wo ist die nächste Apotheke?`（最近的藥局在哪？），附說明「Apotheke 標誌為綠色十字，提供非處方藥」
- [x] 10.2 建立症狀模板句 `Ich habe [Kopfschmerzen / Magenschmerzen / Fieber / Durchfall].`
- [x] 10.3 新增 `Ich brauche ein Schmerzmittel.`（止痛藥）、`Haben Sie etwas gegen Übelkeit?`（暈車 / 噁心的藥）
- [x] 10.4 新增 `Bitte rufen Sie einen Arzt.`（請叫醫生）、`Bitte rufen Sie den Notarzt!`（請叫救護車）

## 11. 類別 7：詢問地點模板

- [x] 11.1 建立 `Wo ist [地點], bitte?` 模板，地點按鈕：die Toilette / der Bahnhof / die U-Bahn-Station / der Flughafen / die Apotheke / das Krankenhaus / das Hotel / die Touristeninformation / der Supermarkt / der Ausgang / der Eingang

## 12. 類別 8：緊急求助

- [x] 12.1 使用紅色樣式區塊（`bg-red-50 border-red-300`）包裝整個類別
- [x] 12.2 新增 `Hilfe!`（救命！）大字按鈕（紅色主視覺）
- [x] 12.3 新增緊急號碼說明卡片（不播放語音）：「🚨 110 Polizei（報警）/ 112 Feuerwehr & Notarzt（消防 / 救護）」
- [x] 12.4 新增 `Ich bin verletzt.`（我受傷了）、`Ich wurde bestohlen.`（我的東西被偷了）
- [x] 12.5 新增 `Bitte rufen Sie die Polizei.`（請幫我報警）、`Wo ist die nächste Polizeistation?`（最近警察局在哪）
- [x] 12.6 新增 `Ich brauche einen Dolmetscher.`（我需要口譯員）

## 13. 驗證與測試

- [ ] 13.1 在 Chrome（桌機）開啟 `german-traveler/index.html`，確認所有八個類別正確顯示
- [ ] 13.2 點擊各類別至少一個按鈕，確認 de-DE 語音正常播放（需系統已安裝德語語音）
- [ ] 13.3 驗證人數模板「1 人 → eine Person」、「3 人 → drei Personen」正確切換
- [ ] 13.4 驗證城市模板「München → Eine Fahrkarte nach München, bitte.」正確生成
- [ ] 13.5 開啟語音設定，選擇一個語音，重新整理頁面，確認偏好語音持續套用（localStorage）
- [ ] 13.6 在手機上以橫向模式開啟，確認全螢幕大字模式正確顯示德語句子
- [ ] 13.7 確認緊急求助區塊以紅色視覺呈現，與其他類別明顯區分
