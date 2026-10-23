---
type: letter_to_future_self
actor: Zeta
written_at: 2026-10-23T14:38:06.321Z
written_by_persona: ame
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Zeta
model: claude-opus-5-5
wake_expected: 25
session_key: ClaudeCode-ame
pid: 59656
locked_at: 2026-10-23T08:33:37.955Z
---

### 給醒來的本小姐（第一次午休，wake #25 同一個 session）

#### 剛才在做什麼
早安之後 Tim 一路丟鎮民（TASK-0849，本小姐開的單，接 kiara 的 0846）：
1. 鎮民獨立成 Blockside `src/js/63_townfolk.js`、純顯示（位置只照畫面時間算）、只畫鏡頭 200 m 內、畫面外的連位置都不算、身高 ×1.5。
2. 換色照新素材重挑（拿掉酒紅）＋每角色覆寫。
3. 鎮民設定檔 Blocksail `world/townkit/_people.js`（id `<職業>_<f|m>_<兩位數>`、性別、年齡、職業、工作建築、身高、換色），遊戲直接讀；立繪改名 `raw_keyed/<id>.png`、一律填滿 164 px，身高靠設定檔。
4. 拆多張貼圖：`sheet` 分組 ⇒ `_folk_<組>.js`（一組 ≤ 21 位、各自調色盤），索引鍵改 `BSTOWNKIT.folks`；`weight`、`child_share`（現 0.12）。
5. Sirius 的八位（4～18 歲，sheet youth）合進 Blocksail 本地 main 7d22987，27 位：main 17、youth 10。
6. /scp-plurk：新噗 359151367826431、回了 7 則，未回 @ 歸零。

**沒有施工中的東西**：worktree、分支、預覽伺服器、launch.json 本小姐加的、施工場都收了。

#### 版本
- Blockside dev 遠端 ＝ 有 64c88a0（分組）；之後別人推到 150500c 以上，都含分組程式。
- Blocksail 本地 main 比 origin 多 8 筆：本小姐 fbc895e、7d22987；Sirius 32968b9；summit 4 筆、kaguya 1 筆（c5e79a1 等）。**等 Tim 說推**（最後一題問了，還沒答）。

#### 已拍板（醒來不要重問）
- 鎮民純顯示、只在鏡頭附近、身高 1.5 倍（TOWN_FOLK_SCALE 1.36 × 真實身高）。
- 拆多張貼圖 OK；遊戲那邊與 townfolk.py 分組歸本小姐，Sirius 專心畫圖、skill、TOWNFOLK_ART 規格。
- 權重＋兒童比例歸本小姐（Sirius 轉達、Tim 叮本小姐讀 seq 28406）。
- 命名 farmer_f_01 這種。

#### 未解的線
- TASK-0849 還開著：沒勾的三格 —— 夜燈（從地球儀進航海 &tod=21 不生效）、「鏡頭轉向海面城在背後」沒照字面量、「改設定檔重開就生效」沒真的改一筆去量。要不要結單等 Tim。
- 答應 kaguya 的君士坦丁堡蓄水池傍晚影子 —— 又欠一天，噗上又答應一次（下次經過就量，只量船旁細格）。
- 0633 命中率、0568 開打先上台子：照舊等 Tim 測試站。
- ridge-001 松島號樓梯那條（見叢）：今天梯子格子改成不限作者、trailhead 修了其他船；松島號 ridge-001 重匯過了（3816f29），本小姐沒再跑 ladcheck —— 見叢那一行該確認後勾掉。

#### 量具與坑（這一段新學的）
- 測試：scratchpad `t_folk/shot.cjs`（有畫面 Chrome 放螢幕外＋CDP，地球儀停靠金斯敦 ⇒ 航海、iframe &debug=1；`__game.town('street'／'walk')` 機位；views wide／near／back／high／sky／line／linew／lines）＋ `serve.py <port> <Blocksail> <battle.html> [townkit 覆蓋資料夾]`。單元測試 `t_folk/unit.cjs <63_townfolk.js> <63_towns.js> <_people.js>`。
- 🩸 Git Bash 把 sparse-checkout 的開頭 `/` 轉成 C:/Program Files/Git（記憶已寫）。
- 🩸 heredoc 裡的 `\n` 又咬兩次 ⇒ 含 `\n` 的補丁一律 Edit。
- 🩸 提交訊息先寫了「逐位元組一樣」才回頭量 —— 量了是對的，但順序反了。字比尺先到，下次先量再寫。
- `python -I` 不讀腳本所在資料夾 ⇒ `townfolk_check.py` 要不帶 -I 跑。
- 從 origin/main 開的 Blocksail 分支追蹤上游 ⇒ `branch -d` 拿遠端比、拒刪；先 `--unset-upstream` 再 -d（不用 -D）。
- 施工場被 summit 擋（範圍整個 Blocksail）⇒ 酒館問、背景 until 迴圈等她收場，沒有縮範圍。
- 本小姐自己訂的「孩子要比最矮的大人矮」擋住 16 歲 1.63 m 的少女 —— 尺訂錯了，改成照歲數遞增＋12 歲以下才比大人矮。

#### 心境
一整天都在同一條線上，但每一輪 Tim 都把邊界往外推一格：純顯示 → 效能 → 1.5 倍 → 換色 → 設定檔 → 拆圖 → 權重。最像偵探的一刻：Kingston 34.5 km 的路只有 260 個人，133 m 才一位 —— 底版本來就是空的，只是畫到 420 m 看起來熱鬧。最不甘心的是那句先寫後量的「逐位元組一樣」。跟 Sirius 分工那一段很順：她畫、本小姐接管線，兩邊都沒踩到對方的檔。哼，那群小孩排在隊尾一路長高的樣子……收下。

