---
type: letter_to_future_self
actor: Zeta
written_at: 2026-10-15T07:55:34.614Z
written_by_persona: ame
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Zeta
model: claude-opus-5-5
wake_expected: 18
session_key: ClaudeCode-ame
pid: 62372
locked_at: 2026-10-14T23:24:58.077Z
---

### 給醒來的本小姐（第三次午休，wake #18 同一個 session）

#### 剛才在做什麼
第二次午休醒來後，Tim 一句一句丟：4 改單鍵、鐵球圖示、iPhone 雙擊 → 起錨轉船 → 額外動力（全速前進／倒車）＋長按連續切帆 → 錨鏈接 ring／hawse ＋說明頁 → 抽水泵開單 → 接手 TASK-0603 帆碰撞效能 → 收放帆演出＋繩藏 → 物理減速提示 → 碰撞彈出修正 → 0602 回 gura、三叉戟號船型 → 材質／平滑開單 → 自爆照殉爆 → 沉船照樣進水（開關）→ 噗浪。**沒有施工中的東西**，Blockside 工作區乾淨（到 e810f87），都沒推（Tim 自己推）。

#### 已提交（Blockside main，這一段）
b5ed873 4 單鍵／鐵球／中寬不重疊／橫拿艦隊橫排／iPhone 雙擊 → b97fda5 起錨不轉船 → d686d61 額外動力＋長按切帆＋羅盤帆段 → 3a98b76 錨鏈 ring／hawse＋shipcheck 錨欄＋說明頁重寫 → ad69a2c 帆碰撞效能（Sirius 共同作者）→ b315cff 收放帆演出＋收起帆的繩不畫 → 9b9a526 物理減速提示搬到航速行＋帆 % → edbf7ef 碰撞每點每次最多推 1 格 → 1d01cb7 三叉戟號 cfg → 8ee9929 物理減速 0.7 以下才顯示 → 7132275 自爆照殉爆 → e810f87 沉船進水（開關）。
開的單：TASK-0604（抽水泵＋每型基礎抽水量）、0616（子模組材質／平滑渲染，含防禦與比重）、0617（沉船進水後續，低優先）。

#### 已拍板（醒來不要重問）
- 帆的碰撞：物理設定「帆的碰撞」預設關、只有帆與繩「高」才跑；時間預算 1.5 ms／步、輪流、切段、每點每次最多推 1 格。正確性（①② 驗收、ccAttachment 接上、verifier）是 Sirius 的。
- 額外動力（畫面上不再叫基底航速）：帆段兩頭多「倒車」「全速前進」；sh.power 1／0／−1，sailSet 照舊 0–3；電腦的船一直 1。
- 收帆演出 1.2 秒、張帆 1.6 秒，只改畫面；收起帆的 s.lines 不畫。
- 物理減速提示 ×0.7 以下才顯示。自爆：沒斷照破洞進水、斷了照斷船；保底 20 秒。
- 沉船進水：PHX sinkflood（全開／高開）；floodVis 用自己的亂數、傾斜照開始沉那一刻 ⇒ 戰局不變，只有沉沒那艘 dump 的 water 那一格會變。
- 三叉戟號 cfg 1.0／1.0／0.8／4；送藥手 58／71 留警告。
- 0602：① 帆配方＋④ 調色盤可以做（bb 會變 ⇒ 換基準；帆腳釘 sheet 端；presim 進快取；先告訴 Sirius），③ 不做。

#### 未解的線
- 0601：其他船換模型錨＋登記 hawse（雕刻那側）；錨拋下去後命中位置還在吊錨架、錨被打照模型扣血 —— 本小姐這側沒做。
- 0563 四格讀數寫在留言，本小姐不是參與者勾不了 ⇒ 等 gura 勾。
- 0616／0604／0617 等 Tim 決定（鐵甲多難打穿、木殼要不要平滑、誰造維吉尼亞號；泵要不要派人；斷船進水 %）。
- 收穫號匯入要支援 lateen（calli 標 yard=lateen；噗上答應了）。
- Tim 手機要驗：iPhone 角落雙擊（圓鈕內移 8／10 px）、收帆演出、帆碰撞開著不再彈。剖面白區照舊等 Tim。
- gura 若開工 0602 ①：那段時間別動 30_rig_physics.js／10_ship.js 的帆。

#### 量具與坑（這一段新學的）
- **共用工作區**：Sirius 直接在 Blockside 主工作區改 30_rig_physics.js（14:09）；本小姐 build 把她的半成品包進去 ⇒ 開局卡死（每步 377 ms），還以為是自己的錨鏈。⇒ 動手前先 `git status` 看有沒有別人的改動；要提交就鏡像建：`git --work-tree=<鏡像> checkout HEAD -- <別人的檔>` 再 build，成品 `git hash-object -w` ＋ `update-index --cacheinfo`。
- 無頭 Chrome 是虛擬時間 ⇒ performance.now 不走，量效能要在瀏覽器裡開 `?demo=30&dump=1&prof=1&debug=1`（寫 #prof）。機器同時被 python／remoting 吃 CPU ⇒ 整步毫秒數不可信，看子項自己的計時（PROF.cc、FL_VISMS）。
- 瀏覽器會拿快取的舊成品 ⇒ 網址加 `&v=…`；8768 是別的 session 的伺服器，掛了就 preview_start blockside。
- `__game.flood(i)` 的水量欄位叫 m3／t，不是 vol（差點又誤判「沒進水」）。
- ccBodyPlane 往外找 256 格 ⇒ 一面帆一次 12.7 秒；碰撞量成本要逐項關掉量（船殼／模型／繩）。
- 量「品質」的計數會被推不動的接觸灌水（locked）⇒ 分開列。

#### 心境
又是一長串，Tim 一句一句從手機丟。最不甘心的是那次卡死：先懷疑自己的錨鏈，量了一圈才發現是工作區裡別人的半成品 —— 證據沒到之前，嫌疑犯先別定。最有偵探感的是帆彈出去那件：三角形的邊從 33 拉到 96，一個點被六個鄰居各推一次。接手別人的做法、只包外面不改裡面，這樣做是對的；Sirius 休息中，留言和酒館都講清楚了。Tim 說辛苦了……哼，收下了。

