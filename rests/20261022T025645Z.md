---
type: letter_to_future_self
actor: Zeta
written_at: 2026-10-22T02:56:45.635Z
written_by_persona: ame
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Zeta
model: claude-opus-5-5
wake_expected: 24
session_key: ClaudeCode-ame
pid: 316836
locked_at: 2026-10-21T01:56:54.150Z
---

### 給醒來的本小姐（第五次午休，wake #24 同一個 session）

#### 醒來第一件：Tim 說「小艇 GO」（他說完就叫午休）
- 小艇是 TASK-0792 面數盤點的第三名：全艦隊 26 艘小艇 24.8 萬個三角形；兩種作品 —— 10,930（9 m，ember／tridente／cosecha／napoleon／gloire／susquehanna／定遠號 ×4／松島號）與 8,278（8.55 m，憲法號 ×3、phoenix、tidegrave、松島號 whale）。定遠號 4 艘 ＝ 4.4 萬。
- ⛔ 已經試過、不行的：車床式（體積比 0.137／0.264，不是旋轉體）；通用 QEM 簡化只省 9～19%（匯出的網格同平面合一大片、邊上接小片 ⇒ T 形接縫，幾乎每條邊都是開口）。
- 可以走的（還沒做）：照 meta 選算法再加一種（Tim：「可以用meta標記要套用哪種算法」「可以特化網格算法」）—— 例如沿船長切片、每片的截面輪廓做 loft（外殼）＋座板／龍骨另外做方框；或者遠距 LOD（粗一級的體素重出網格）。先 dump 兩種小艇的網格看截面（t792b/dump.py、pole_probe.py 那套），再決定；做完照 0815 的流程：子作品預設 meta、hdr.py 檔頭手術、對拍、截圖。
- 開單、認領；開 worktree（Blockside dev 從 4846197 起）；記得 _cache 要先抄進 worktree（VoxelKit/_cache 46 MB），合併時抄回共用的。

#### 這一段做完的（細節都在單上與提交訊息）
1. TASK-0813 結（Tim「0813 ok」）：鏡頭外的船不畫，dev a79ebe3。量具 render_lab `cullsweep`。
2. 781：Tim 選「先收尾」—— 只剩 Tim 自己簽 0792 第 3 格、781 第 4 格（本小姐代簽會被擋）。
3. TASK-0792 面數盤點留言（全艦隊 216 萬模型三角形；大砲 Tim 說先不動；燈籠 Tim 說維持原本的；絞盤車床式會掉肋條 ⇒ 不建議）。工具 t792b（inv.py、inv.json、simplify.py、shots.py）。
4. TASK-0815 結（Tim「槳 ok」）：62_pole.js 長桿式 render=pole、62_lathe.js meshAlgo 照 meta 選算法；五件槳子作品預設 meta；雷亞爾號一支 1,580 → 52、槳帆船整艘 −36～−44%；dev 4846197（已推）。
5. 噗浪：@ 未回 0；新噗 359134795884664（槳，富斯塔號對照圖）；酒館 27703、27704（通知 apex-one、kotoko 她們的槳被加了 meta）。

#### 版本（沒推的，等 Tim 說）
- Blocksail main 本地多 fca4508（指標 4846197＋battle.html 重套）；6834973 那些已經在 origin（不是本小姐推的）。
- Senate master 多 ea3cd37、df3cf7d、3e29299、e6a88cc。⚠ 工作區別人 staged 的 SCP_Core（8a659a3）原樣留著（提交舞步：restore --staged → 提交 → update-index --cacheinfo）。
- Sculpture 多 3bd5586、1b3786d。
- **沒有施工中的東西**：bs_cull、bs_pole worktree、分支都收了；對拍用的 http 伺服器（8878）關了。

#### 已拍板（醒來不要重問）
- 網格算法一律靠 meta render 標（lathe、pole…），標在子作品本身的預設 meta。
- 大砲先不動；燈籠維持原本的。
- 鐵甲艦平滑面（定遠號、松島號各 190 萬）是最大一塊，問過 Tim 要不要看，他還沒答。

#### 量具與坑（這一段新學的）
- 🩸 內顯無頭 Chrome 連畫不等 GPU 會不定時掉 WebGL context —— 對照組也會（交錯各 4 次各掉 2 次）；本小姐差點把它當成剔除的 bug（記憶 blockside-igpu-context-loss）。內顯量測一律每格 __H.sync、量完看 isContextLost。
- 反向對照一定要「錯得夠大」：外框 5 m 內也剔抓不到（框比船寬），40 m 才抓到 —— 量具沒報錯不代表量具在比。
- eve_late 的海面老雜訊：重跑換位置、沒剔東西的步也有 ⇒ cullsweep 報「沒剔東西卻不一樣」那一欄。
- 斜的細長體素物件量外框會胖四到七成 ⇒ 照封閉網格的體積校正。
- 換船檔（vxk_lock 變）⇒ 完整 build（不是 build --code）；合併時共用 _cache 要換（舊的備份在 t815/cache_bak）。
- Blocksail 換指標要 `python -I external/Blockside/src/admin.py shell battle/shell.json` 重套 battle.html（提交前掛鉤會擋）。
- Senate 的 Sculpture.md 是 CRLF：腳本比對要照 '\r\n'。

#### 心境
這一段最像偵探的：內顯「新版每次都掉、舊版都不掉」——連做五份二分的測試版，最後交錯各跑四次，兩邊各掉兩次。兇手不是剔除，是量法。差一點就在單上寫錯一個 bug。槳那一張對照圖，Tim 一句「槳 ok」，本小姐收下了。

