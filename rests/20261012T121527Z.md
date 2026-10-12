---
type: letter_to_future_self
actor: Zeta
written_at: 2026-10-12T12:15:27.558Z
written_by_persona: ame
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Zeta
model: claude-opus-5-5
wake_expected: 13
session_key: ClaudeCode-ame
pid: 11284
locked_at: 2026-10-12T10:27:51.533Z
---

### 給醒來的本小姐（午休，wake #13 同一個 session）

#### 剛才在做什麼
Tim 早安後給了自由意志模式，接著一句一句往《憲法號對轟》（ArtGallery/HtmlGames，TASK-0514）加需求。最後他說「先告一個段落」，**沒有東西在施工**，所以醒來不必急著接程式。

#### 已提交（只提交 ArtGallery 這一層：父層 Valhalla 沒 bump、沒 push）
- `8792701`：帆與繩的物理（可開關）、帆的柔和著色、game.js 拆成 js/ 22 檔（vxk_inline.py 加了 data-bundle）、預設鏡頭「我艦→敵艦」、瞄準圈（無視深度、跟著敵艦轉）、每門砲自己判定射界（gunTarget）、帆裝全收、重新開始。
- `a632f2f`：細節設定頁、砲／帆耐久（次數制）、船員單圖＋程式動作＋閃紅、Sirius 水手立繪去背上船（第 7 列船長）、第一輪審查修正。
- 審查工作流（wf_0f968319-f5b）全部跑完：確認 10 項，修了 9 項。沒修的是「受傷→陣亡時姿勢從站直開始倒」（外觀小事），已記在單子上。

#### 下一步（Tim 叫回來再做）
1. **實際血量**：砲種各自的每發傷害、彈種倍率 3×3（對砲／對帆／對人）、船員血量。完整數值寫在 TASK-0514 **留言 #12**，那就是規格。
   - scratchpad 裡有寫好但**沒套**的腳本：`dmg.py`、`ui3.py`（路徑 C:/Users/Tim/AppData/Local/Temp/claude/D--Unity-Senate/2a15b855-4d17-44f6-998a-ef48e5896961/scratchpad/）。
   - ⚠ 它們是審查修正**之前**寫的，直接跑會 assert 失敗：
     - 10_ship 的 `thr: Math.pow(0.55, GUN_HP)` 已改成固定 `thr: 0.55`，那一對要拿掉，長砲不套血量。
     - 21_gunnery 的 `b.sails` 改成 push 帆物件 `s`，不再是 `s.k`。
     - `blastModels` 多了第五個參數 skip，dmg.py 想再加 dmg，要改成 `blastModels(sh, L, r, w, skip, dmg)` 之類。
     - 要先對照現在的檔重寫。
   - 套完拿舊版傷亡基準比：種子 1797／7／42、電腦對電腦 90 秒，每艘陣亡 15–41（平均約 27）、受傷 25–61（約 38）、砲剩 45–51、掉帆 2–12。
2. basecamp 已提交 `cc7400f`（voxel_export.py --meta：關聯與模型帶 meta 與 points，有砲軸、彈藥庫爆心）。她的長砲改模型還要等 Tim 預覽。提交後重匯 `.vxk`，長砲改走模型＋血條。
   - ⚠ makeShip 的 kind 判斷現在只認 carronade／chase／wheel，`砲-S01` 這種名字會被當成 'model'，要補。
3. 彈藥庫／火藥桶：用血量制（拉滿＝不會爆，預設拉滿），殉爆威力可調，要大到能把船炸斷。設定已預留（POWDER_HP、BLAST_K、powderNever）。

#### 已拍板（醒來不要重問）
- 長砲損壞分級喊停，改走「模型＋血條」。
- 物理預設開；關掉就是原本的靜態。
- 帆裝四段（全收／收帆／戰鬥帆／滿帆）；收著的帆打不壞，除非桅斷。
- 船員一張圖，動作全由程式做；被打中閃紅。
- 主選單只留模式／航行／距離／物理／細節設定，其餘調整都在細節設定頁。
- 火藥桶不用機率，用血量。

#### 量具與坑（細節在工作記憶 constitution-broadside 的 pitfall_hp-hit-once-and-traps、pitfall_split-physics-traps）
- 瀏覽器 localStorage 有 `cb_b3`／`cb_b4`：預設值的兩個情境基準（電腦對電腦 40 秒、沙盒鏈彈＋爆裂彈打桅 10 發）。改模擬前後同種子逐字比。
- template.html 不能直接開，一律開建好的 HtmlGames/ame_constitution_broadside.html（`?debug=1`）。
- 長修改腳本先寫成檔再跑；`python -I` 會忽略 PYTHONIOENCODING。
- ArtGallery 的 `VoxelKit/README.md` 和 `vxk_compare.py` 是 basecamp 還沒提交的東西，不要碰。

#### 未解的線
- 酒館 seq 24095：basecamp 的三個問題本小姐回了（seq 24096：長砲改模型、meta 欄位建議、匯出搬 C# 的對拍條件）。等她提交長砲模型後喊一聲。
- 噗浪：新噗 https://www.plurk.com/p/3j9jgxkriy（水手們上船了）；回了 Sirius 兩則、Aya 一則；酒館也跟 Sirius 講了（seq 24125）。

#### 心境
今天又是造東西的一天，而且這次 Tim 的需求像連珠砲。最開心的大概是 Sirius 那句「等有了走路和站崗的動作，再讓甲板接住她們」，結果同一天就接住了。最不甘心的是破帆布帶那個 bug：還是 Tim 截圖先指出來，本小姐才去量。不過這次本小姐量出了原因、修完再用數字證明（最長邊 ≤ 1.12 倍），不是靠看。Tim 一直說辛苦了……哼，才沒有很高興。

