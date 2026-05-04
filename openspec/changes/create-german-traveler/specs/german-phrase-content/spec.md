## ADDED Requirements

### Requirement: 詞句分為八大在地化類別
應用 SHALL 包含以下八個類別的德語詞句，反映台灣旅客前往德語區的常見需求：
1. 日常禮貌（Alltag）
2. Deutsche Bahn 鐵路
3. 超市與購物
4. 餐廳與啤酒花園
5. 飯店住宿
6. 藥局（Apotheke）
7. 詢問地點模板
8. 緊急求助

#### Scenario: 頁面載入後顯示所有八個類別
- **WHEN** 使用者開啟 `german-traveler/index.html`
- **THEN** 頁面 SHALL 呈現八個區塊標題，各含至少 3 個可點擊詞句

---

### Requirement: 日常禮貌類別包含德國敬語文化常用句
「日常禮貌」類別 SHALL 包含以下句型，全部使用 `Sie`（您）敬語：
- `Guten Morgen`（早安）、`Guten Tag`（你好/日安）、`Guten Abend`（晚安）
- `Danke schön`（非常感謝）、`Bitte`（麻煩您 / 不客氣）
- `Entschuldigung`（不好意思 / 借過）、`Es tut mir leid`（對不起）
- `Sprechen Sie Englisch?`（您說英語嗎？）
- `Ich verstehe nicht.`（我聽不懂。）、`Können Sie das bitte wiederholen?`（可以再說一次嗎？）

#### Scenario: 點擊「Guten Tag」觸發語音播放與顯示更新
- **WHEN** 使用者點擊「你好（日安）」按鈕
- **THEN** 頂端顯示區 SHALL 更新為「你好 (日安)」與「Guten Tag」，且 Web Speech API SHALL 以 `de-DE` 語音朗讀「Guten Tag」

---

### Requirement: Deutsche Bahn 鐵路類別包含購票與候車常用句
「Deutsche Bahn 鐵路」類別 SHALL 包含以下情境詞句：
- `Eine Fahrkarte nach [目的地], bitte.`（一張去＿的票）→ 以模板句實現，目的地選項含：München / Berlin / Frankfurt / Hamburg / Köln
- `Einmal / Zweimal München, einfach / hin und zurück.`（單程 / 來回）
- `Welches Gleis fährt nach München?`（去慕尼黑是幾號月台？）
- `Muss ich umsteigen?`（需要轉車嗎？）
- `Der Zug hat Verspätung.`（火車誤點了。）
- `Ich habe eine Reservierung.`（我有訂位。）
- `Ist dieser Platz frei?`（這個位子有人嗎？）

#### Scenario: 選擇目的地城市更新模板句
- **WHEN** 使用者在鐵路類別點擊「München」目的地按鈕
- **THEN** 顯示區 SHALL 呈現「一張去慕尼黑的票，麻煩您」與「Eine Fahrkarte nach München, bitte.」，並自動播放語音

---

### Requirement: 超市與購物類別涵蓋 Pfand 押金與收銀台情境
「超市與購物」類別 SHALL 包含以下詞句，反映德國超市特有文化：
- `Wo ist die Kasse?`（收銀台在哪裡？）
- `Ich möchte diesen Pfand zurückgeben.`（我要退押金瓶。）→ 附說明「Pfand = 押金制，將空瓶放入回收機退款」
- `Haben Sie eine Tüte?`（有袋子嗎？）
- `Kann ich mit Karte zahlen?`（可以刷卡嗎？）
- `Getrennt bitte.`（分開結帳。）
- `Zusammen bitte.`（一起結帳。）
- `Wo sind die Toiletten?`（廁所在哪？）
- `Haben Sie das auch in Größe…?`（有＿號尺寸嗎？）→ 模板句，尺寸選項 S/M/L/XL

#### Scenario: 點擊 Pfand 詞句顯示補充說明
- **WHEN** 使用者點擊「我要退押金瓶（Pfand）」按鈕
- **THEN** 顯示區 SHALL 呈現德語句子，且按鈕卡片 SHALL 附帶小字說明「Pfand = 押金制，空瓶放回收機退款」

---

### Requirement: 餐廳與啤酒花園類別反映德國用餐文化
「餐廳與啤酒花園」類別 SHALL 包含：
- `Einen Tisch für [人數] Personen, bitte.`→ 模板句，人數 1–6（`eine Person` / `N Personen`）
- `Die Speisekarte, bitte.`（菜單，麻煩您。）
- `Ich bin allergisch gegen…`（我對＿過敏。）→ 模板句，選項：Nüsse（堅果）/ Gluten / Milch（乳製品）/ Meeresfrüchte（海鮮）
- `Das schmeckt sehr gut!`（非常好吃！）
- `Zahlen bitte!`（買單！）— 附說明「德國餐廳通常需要主動呼叫服務員結帳」
- `Getrennt bitte.`（分開付。）
- `Kann ich eine Quittung haben?`（可以給我收據嗎？）
- `Ein Bier / Ein Weißbier / Ein alkoholfreies Bier, bitte.`（一杯啤酒 / 白啤酒 / 無酒精啤酒）
- `Prost!`（乾杯！）
- `Eine große / kleine Maß, bitte.`（一公升 / 小杯啤酒，麻煩您。）— 附說明「Maß = 慕尼黑啤酒節 1 公升大杯」

#### Scenario: 人數模板句正確處理單複數
- **WHEN** 使用者選擇「1 人」
- **THEN** 顯示區 SHALL 呈現「Einen Tisch für eine Person, bitte.」
- **WHEN** 使用者選擇「3 人」
- **THEN** 顯示區 SHALL 呈現「Einen Tisch für drei Personen, bitte.」

---

### Requirement: 飯店住宿類別包含入住與問題回報常用句
「飯店住宿」類別 SHALL 包含：
- `Ich habe eine Reservierung. Mein Name ist…`（我有預訂，我叫＿。）
- `Um wie viel Uhr ist der Check-out?`（幾點可以退房？）
- `Kann ich mein Gepäck aufbewahren?`（可以寄放行李嗎？）
- `Das WLAN-Passwort, bitte.`（Wi-Fi 密碼是多少？）
- `Es gibt kein heißes Wasser.`（沒有熱水。）
- `Die Klimaanlage funktioniert nicht.`（冷氣壞了。）
- `Ich möchte auschecken.`（我要退房。）

#### Scenario: 點擊「我有預訂」觸發語音與顯示
- **WHEN** 使用者點擊「我有預訂」按鈕
- **THEN** 顯示區 SHALL 呈現「Ich habe eine Reservierung.」並播放 de-DE 語音

---

### Requirement: 藥局（Apotheke）類別涵蓋常見就診購藥需求
「藥局（Apotheke）」類別 SHALL 包含以下詞句，附帶德國藥局文化說明：
- `Wo ist die nächste Apotheke?`（最近的藥局在哪？）— 附說明「德國 Apotheke 標誌為綠色十字，分處方（Rezept）和非處方（OTC）藥品」
- `Ich habe Kopfschmerzen / Magenschmerzen / Fieber / Durchfall.`（頭痛 / 胃痛 / 發燒 / 腹瀉）→ 模板句
- `Ich brauche ein Schmerzmittel.`（我需要止痛藥。）
- `Ich bin auf dieses Medikament allergisch.`（我對這個藥物過敏。）
- `Haben Sie etwas gegen Übelkeit?`（有暈車 / 噁心的藥嗎？）
- `Bitte rufen Sie einen Arzt.`（請叫醫生。）
- `Bitte rufen Sie den Notarzt! / Notruf 112`（請叫救護車！/ 緊急號碼 112）

#### Scenario: 症狀模板句切換顯示
- **WHEN** 使用者在藥局類別點擊「頭痛」
- **THEN** 顯示區 SHALL 呈現「Ich habe Kopfschmerzen.」並播放語音

---

### Requirement: 詢問地點模板句以 Wo ist…? 結構動態組合
「詢問地點」類別 SHALL 提供按鈕組合生成 `Wo ist [地點], bitte?` 句型，地點選項 SHALL 包含：
- `die Toilette`（廁所）
- `der Bahnhof`（火車站）
- `die U-Bahn-Station`（地鐵站）
- `der Flughafen`（機場）
- `die Apotheke`（藥局）
- `das Krankenhaus`（醫院）
- `das Hotel`（飯店）
- `die Touristeninformation`（遊客服務中心）
- `der Supermarkt`（超市）
- `der Ausgang / der Eingang`（出口 / 入口）

#### Scenario: 點擊地點選項組合完整問句
- **WHEN** 使用者點擊「地鐵站」
- **THEN** 顯示區 SHALL 呈現「請問地鐵站在哪？」與「Wo ist die U-Bahn-Station, bitte?」，並播放語音

---

### Requirement: 緊急求助類別包含高辨識度的緊急詞句
「緊急求助」類別 SHALL 包含以下詞句，以醒目紅色樣式呈現：
- `Hilfe!`（救命！）
- `Notruf: 110 Polizei / 112 Feuerwehr & Notarzt`（報警 / 消防救護）— 以說明卡片呈現，不播放語音
- `Ich bin verletzt.`（我受傷了。）
- `Ich wurde bestohlen.`（我的東西被偷了。）
- `Wo ist die nächste Polizeistation?`（最近的警察局在哪？）
- `Bitte rufen Sie die Polizei.`（請幫我報警。）
- `Ich brauche einen Dolmetscher.`（我需要口譯員。）

#### Scenario: 緊急類別以視覺紅色區分
- **WHEN** 頁面渲染完成
- **THEN** 緊急求助區塊 SHALL 使用紅色背景或邊框（`bg-red-50` 或 `border-red-400`），與其他類別明顯區分
