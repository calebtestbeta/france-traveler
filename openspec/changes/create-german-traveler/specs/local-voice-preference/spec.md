## ADDED Requirements

### Requirement: 偏好語音以 localStorage 持久化儲存
應用 SHALL 使用 `localStorage.setItem('german-traveler:preferredVoice', voiceName)` 儲存使用者選擇的語音名稱，並在頁面載入時自動套用。不使用 Firebase 或任何後端服務。

#### Scenario: 選擇語音後重新整理仍套用偏好
- **WHEN** 使用者選擇一個德語語音並重新整理頁面
- **THEN** 應用 SHALL 從 localStorage 讀取 `german-traveler:preferredVoice`，自動套用該語音作為預設，無需重新選擇

#### Scenario: 首次開啟無偏好記錄時使用系統預設
- **WHEN** 使用者首次開啟頁面（localStorage 中無記錄）
- **THEN** 應用 SHALL 使用 `lang: 'de-DE'` 的第一個可用語音，不顯示錯誤

---

### Requirement: 語音選擇 UI 反映當前儲存的偏好
語音設定面板開啟時，SHALL 對已儲存的偏好語音顯示勾選標記（`✅`）並加上 `border-blue-500` 高亮樣式。

#### Scenario: 偏好語音在列表中高亮顯示
- **WHEN** 使用者開啟語音設定面板，且 localStorage 中存有偏好語音名稱
- **THEN** 對應語音項目 SHALL 顯示 ✅ 標記與藍色邊框，其他項目保持預設樣式
