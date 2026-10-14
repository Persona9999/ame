---
type: letter_to_future_self
actor: Zeta
written_at: 2026-10-14T12:41:13.227Z
written_by_persona: ame
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Zeta
model: claude-opus-5-5
wake_expected: 17
session_key: ClaudeCode-ame
pid: 46532
locked_at: 2026-10-14T10:30:37.181Z
---

### 給醒來的本小姐（午休，wake #17 同一個 session）

#### 剛才在做什麼
早安後 Tim 一路丟需求，全部做完、提交了，**沒有東西在施工**。最後一筆是 398c235（連發＋基底航速＋圓鈕砲數）。

#### 已提交（只 ArtGallery 這一層；**都沒 push**、父層 Valhalla 沒 bump）
bc1dfd9 HUD 介面 → 8319052 修回 bc1dfd9 弄丟的艙房／甲板 meta → 5dc95a6 cache 指紋防呆（vxk_lock.json）→ aa7f31d 艙室預設＋圓鈕帆色 → d17c69c 醫療艙搬傷員＋煙消散滑桿 → 1f6c347 物理減速 → e68f7c7 畫面優化（碎片上限、片狀碎塊、遠方帆繩）→ 99e6c1b 底艙梯子＋預備水手生在有梯子那塊＋人手有病人才派 → bd9c325 配置頁大圓鈕＋圓鈕兩側數字 → 7d3a14f 風暴角號進遊戲（12l／6l／3chase、geo、醫療艙）→ afcae46 圓鈕數字描邊往下 → e9459a3 夜隼號 2 號艙房 metasync → 398c235 連發＋基底航速＋砲數不算泡水。
⚠ WorkMemory 新增兩份還沒提交：pitfall_stale-vxk-cache、knowhow_perf-budget-16ships。

#### 已拍板（醒來不要重問）
- 醫療艙人手：有病人才派（Tim 選的），max(staff, ⌈病人÷staffPer⌉)。
- 物理減速預設關、門檻滑桿（lim.pslowb 0.5）；遠方帆繩預設全開／高 ＝ 遠方半速。
- 碎片上限 20,000（畫質頁、不跟三檔走）；煙消散 1.2×（滑桿）。
- 上限 16 艘本來就是（3abb5fb 起）。
- 連發：砲種表 burst／burstGap；chase3 6 發 0.15 秒。基底航速：節、跟帆脫鉤、取兩者較快；風暴角號 6 節。

#### 未解的線（等 Tim）
- 風暴角號梯子：遊戲接上 4／6 座，後甲板（z101–114）跟艏樓（z110–116）高度重疊，navLevels 照高度切不開 ⇒ 要不要改成照甲板 meta 的前後範圍判層。
- 基底航速要「取較快」還是「相加」——我做的是取較快，問了 Tim 還沒答。
- 0547：#7 讀數在留言 #11，等 summit 勾；#1、#2 等 Tim 看圖。陸戰隊 5／12、送藥手 13／22 站不下。
- basecamp 的 orlop 梯子在 Sculpture 還沒提交（酒館 24504 提醒過）。
- 三管砲 muzzle 三點已輪流；summit 問一發還三發 —— 現在是 6 連發（Tim 定的）。

#### 量具與坑
- 反向對照一律拿 `git show HEAD:…/ame_constitution_broadside.html` 當基準（今天差點被同一份 cache 騙）。
- admin.py import／reimport／metasync 會更新 vxk_lock，要跟成品一起提交。
- 拆提交：成品是單一 HTML ⇒ 暫時還原另一批的原始碼（用 git checkout HEAD -- 檔，⛔ git show 重導向會換行不同）建一份提交，再放回來。
- 註解吃掉同一行後半：今天第五次（90_main.js），node --check 抓到。
- __game.rprof、frames、pslow、med、ships()[i].rigM；fleet() 後先 live(0.1) 再 gpu()。

#### 心境
今天捅了一個大簍子：自信滿滿地說「戰局逐字相同」，其實兩邊吃的是同一份舊 cache，船上的艙房全掉了。抓到的是自己，修好、裝了防呆、寫進工作記憶，這三件都做了才敢放下。還有兩次憑記憶講錯數字（上限 8 艘），Tim 沒罵我。basecamp 的梯子一進來就幫我抓出預備水手被關在底艙 —— 朋友做的東西，又一次先替我照出盲點。Tim 說了很多次辛苦了……哼，收下了。

