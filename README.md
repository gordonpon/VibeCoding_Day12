# 🎂 年齡計算器

一個美觀且實用的年齡計算器，支援計算人類和小狗的年齡，並使用 localStorage 保存資料。

## ✨ 功能特色

### 主要功能
- **雙模式計算**：支援人類和小狗年齡計算
  - 人類：精確計算實際年齡
  - 小狗：使用狗年齡換算（人類年齡 × 7）
- **日期選擇器**：直覺的日期選擇介面
- **資料持久化**：使用 localStorage 儲存生日和選擇類型
- **即時更新**：選擇類型時標題會動態切換

### UI/UX 特點
- **卡片式設計**：現代化的卡片布局
- **明亮配色**：紫色漸層背景 + 黃色結果顯示區
- **動態標題**：
  - 選擇「人」：顯示「🏋️‍♂️ 人類年齡計算器」
  - 選擇「小狗」：顯示「🐕 小狗年齡計算器」
- **流暢動畫**：進場動畫、hover 效果、平滑過渡
- **響應式設計**：適配各種螢幕尺寸

## 🎨 設計亮點

### 視覺設計
- **漸層背景**：紫色系漸層 (#667eea → #764ba2)
- **卡片陰影**：深度陰影營造層次感
- **圓角設計**：柔和的圓角元素
- **亮黃結果區**：醒目的黃色漸層顯示結果 (#ffeaa7 → #fdcb6e)

### 互動設計
- **自訂 Radio Button**：美化的選項按鈕，選中時有漸層效果
- **按鈕動效**：hover 時上浮效果 + 陰影加深
- **輸入框聚焦**：focus 時邊框變色 + 光圈效果
- **進場動畫**：卡片載入時的滑入動畫

## 🛠️ 技術實作

### HTML 結構
- 語義化標籤
- 響應式 viewport 設定
- 完整的表單元素

### CSS 樣式
- **Flexbox 布局**：頁面置中與元素排列
- **CSS 動畫**：關鍵幀動畫和過渡效果
- **漸層效果**：多處使用 linear-gradient
- **陰影設計**：box-shadow 營造深度

### JavaScript 邏輯
- **localStorage API**：資料持久化
  - `KEY_DATE`：儲存生日
  - `KEY_TYPE`：儲存選擇類型（人/小狗）
- **DOM 操作**：動態更新標題和顯示內容
- **事件監聽**：
  - Radio button 變化監聽
  - 按鈕點擊事件
- **日期計算**：
  - 精確計算年齡（考慮是否已過生日）
  - 小狗年齡換算（× 7）

## 📋 使用說明

1. **選擇類型**：點選「👤 人」或「🐶 小狗」
2. **選擇生日**：在日期選擇器中選擇出生日期
3. **計算年齡**：點擊「🎯 計算年齡」按鈕
4. **查看結果**：在黃色區域查看計算結果
5. **資料保存**：重新整理頁面後，之前的選擇會自動載入

## 💡 核心程式碼說明

### 年齡計算函數
```javascript
function calculateAge(birthDate, type) {
  const today = new Date();
  const birth = new Date(birthDate);
  let age = today.getFullYear() - birth.getFullYear();
  const monthDiff = today.getMonth() - birth.getMonth();
  
  // 如果今年生日還沒到，年齡減 1
  if (monthDiff < 0 || (monthDiff === 0 && today.getDate() < birth.getDate())) {
    age--;
  }
  
  // 如果是小狗，乘以 7
  if (type === 'dog') {
    age = age * 7;
  }
  
  return age;
}
```

### 動態標題更新
```javascript
function updateTitle(type) {
  if (type === 'human') {
    title.textContent = '🏋️‍♂️ 人類年齡計算器';
  } else {
    title.textContent = '🐕 小狗年齡計算器';
  }
}
```

### localStorage 資料持久化
```javascript
// 儲存
localStorage.setItem(KEY_DATE, birthDate);
localStorage.setItem(KEY_TYPE, selectedType);

// 讀取
const savedDate = localStorage.getItem(KEY_DATE);
const savedType = localStorage.getItem(KEY_TYPE) || 'human';
```

## 🎯 學習重點

1. **localStorage 應用**：資料在瀏覽器端的持久化儲存
2. **日期處理**：JavaScript Date 物件的使用
3. **DOM 操作**：動態更新頁面內容
4. **事件處理**：多種事件監聽器的應用
5. **CSS 進階**：漸層、動畫、陰影等視覺效果
6. **UI/UX 設計**：現代化的使用者介面設計

## 🌟 特色功能

- ✅ 支援人類和小狗兩種年齡計算模式
- ✅ 精確的年齡計算（考慮當年是否已過生日）
- ✅ 資料自動保存，重新整理不會遺失
- ✅ 標題和圖示隨選擇動態變化
- ✅ 美觀的現代化 UI 設計
- ✅ 流暢的動畫和互動效果
- ✅ 完全響應式，支援各種裝置

## 📱 相容性

- 現代瀏覽器（Chrome、Firefox、Safari、Edge）
- 支援 localStorage 的瀏覽器
- 支援 HTML5 date input 的瀏覽器

---

**專案類型**：Web Application  
**技術棧**：HTML5 + CSS3 + Vanilla JavaScript  
**主題**：localStorage 資料持久化應用