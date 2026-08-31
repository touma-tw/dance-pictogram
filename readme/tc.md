# Dance Pictogram — 使用說明

跳舞時,影片旁邊會捲動一條動作提示,在每個動作發生的前一刻告訴你接下來要做什麼。
為 VRChat 的 [PyPyDance](https://pypydance.com/) 而做。

**語言:** [English](en.md) · 繁體中文 · [简体中文](sc.md) · [日本語](jp.md) · [한국어](ko.md)

---

## 1. 安裝

1. 到 [Releases](https://github.com/touma-tw/dance-pictogram/releases) 下載最新的
   `DancePictogram-x.y.z.zip`。
2. 解壓縮到任何地方,放桌面也可以。**不要放在 `C:\Program Files`**,程式會把歌曲資料寫在自己旁邊。
3. 執行 `DancePictogram.exe`。

不需要安裝程式、不需要帳號、不需要金鑰。要移除的話,直接刪掉整個資料夾。

## 2. 下載歌曲

程式本身不含歌曲資料。打開 **Songs** 分頁。

**最快的方式** — 按上方的下載包按鈕:

| 按鈕 | 內容 |
|---|---|
| **Pictogram** | 手繪人形加上動作箭頭。全部 598 首共 851 MB。 |
| **Real dancer** | 從影片中去背取出的真人舞者,疊上同樣的箭頭。1632 MB。 |
| **Everything** | 兩種都要。2244 MB。 |

然後按 **Download selected**。需要幾分鐘,期間可以繼續操作程式。

**只挑幾首** — 在搜尋框輸入後按 Enter,勾選想要的歌,再按 **Download selected**。
程式只會下載那幾首,不會抓整包。

搜尋支援一般關鍵字(曲名、歌手、曲風、編號),也可以組合條件:

```
twice                 任何符合「twice」的
artist:twice          只找這個歌手
mode:multi            有多位舞者可選的曲目
genre:kpop            依曲風
installed:no          還沒下載的
```

全部裝完之後,下載包按鈕會自動收起來。點標題列可以再打開。

## 3. 在 VR 裡設定

切到 **Overlay** 分頁,按下大大的 **Start**。接著在 VRChat 裡:

- **VR distance** — 提示條浮在多遠的地方。建議推到跟影片螢幕差不多的深度,這樣眼睛不用在兩者之間重新對焦。
- **VR scale** — 看起來多大,與距離無關。
- **Pin in room** — 把提示條固定在空間中,不再跟著頭轉。
- **Pictogram / Real** — 顯示哪一種圖。

另外在你**右手手背**上會浮著一個小面板。看著按鈕一會兒就會按下去 —— 因為 VRChat 佔用了控制器,
只能用視線操作。上面有 **PIN**(不用脫下頭盔就能重新擺放提示條)和 **STYLE**。

## 4. 跳舞的時候

程式會讀 VRChat 的日誌來判斷現在播的是哪一首,並且聽你的喇叭來判斷播到第幾秒。
你不需要告訴它任何事。

**多人舞曲**會一位教練一條軌道。開始時眼前會出現選擇畫面 —— 盯著你想跟的那位看兩秒即可。

**覺得時間差一點?** 調整 `config.toml` 裡的 `video_lag_sec`,或是直接告訴我們。
正值會讓提示晚一點出現,負值會早一點。需要預備動作的提示,早一點出來反而好跳。

## 5. 用 OBS 錄影

SteamVR 的 overlay 是疊在 VRChat 畫面之上的,所以 VRChat 自己的攝影機看不到這條提示。
請在 Overlay 分頁打開 **Spout → OBS**,然後在 OBS 新增 **Spout2 Capture** 來源,選擇
`DancePictogram`。把它疊在 VRChat 攝影機來源上方,並把合成模式設為 straight(非預乘)alpha。

## 6. 遇到問題

**提示條是空的。** 表示沒有音樂在播,或程式聽不到。請檢查 Overlay 分頁的音訊裝置 ——
應該選擇播放 VRChat 聲音的那個裝置的 **loopback(回放)**。

**顯示的是別首歌。** 程式讀 VRChat 日誌判斷曲目;如果 VRChat 沒開,它會退而用聲音辨識,
而聲音無法分辨那些用同一首音樂、但編舞不同的曲目。

**某一首的提示不準或時間不對。** 這確實會發生 —— 提示是自動產生的,遇到快速剪接、
動態模糊、或多位舞者交錯的影片,品質會比較差。請
[開一個 issue](https://github.com/touma-tw/dance-pictogram/issues) 並附上曲目編號。
重新產生的曲目會隨之後的批次更新,程式只會下載有變動的部分。

**更新。** 程式啟動時會檢查有沒有新增或修正過的曲目。Songs 分頁會顯示哪些有變動,
按 **Install everything missing** 即可。
