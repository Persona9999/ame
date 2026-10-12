---
type: letter_to_future_self
actor: Zeta
written_at: 2026-10-12T07:16:21.039Z
written_by_persona: ame
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Zeta
model: claude-opus-5-5
wake_expected: 12
session_key: ClaudeCode-ame
pid: 56964
locked_at: 2026-10-12T03:37:47.266Z
---

## 給醒來的本小姐（午休，wake #12 同一個 session）

### 剛才在做什麼
- 今天的主線是 Tim 交辦的《憲法號對轟》（ArtGallery HtmlGames）。Tim 說「先告一段落、把資料寫進 task」，所以**沒有東西在施工**，醒來不用急著接回程式。
- 已提交（ArtGallery，只這一層，父層 Valhalla 沒 bump、沒 push）：
  - `6f6055b`：TASK-0513 首版（已結）。
  - `54be17d`：船員、操砲、傷亡、模型、滑桿、三角帆修正、美術接口、暫用 crew.png。
  - 帶的是 `Refs TASK-0514／0515／0516`。
- 單子：
  - TASK-0514 總單：in_progress，已收工；留言 #1 是讀數與審查清單，#3 是更正（駁回 2 項）。
  - TASK-0515 浮空帆：in_progress；① 已勾，② 等帆腳索一起修好再帶 Fixes。
  - TASK-0516 美術單：給人類美術，三張圖 crew／fx／hud。
  - 早上還修了 Senate 的 TASK-0508（`59bef17`）並出廠過（build.sh＋check.sh），已結。

### 下一步（Tim 叫回來再做）
- 從工作記憶 `constitution-broadside` 接：
  - `knowhow_next-batch-plan`：降旗玩家可設定、人手照史料 6／3／4、裝填公式、長砲損壞分級、站位修正。
  - `knowhow_review-findings-2026-10-12`：32 項，行號照 `54be17d`。
- 優先：
  1. reassign 人手集中（high，被放出的人走回原砲）。
  2. 帆腳索浮空（high）。
  3. 降旗設定（Tim 拍板）。
  4. 長砲損壞分級。
  5. 重量整場、重截縮圖、更新展品卡（現在畫廊上還是無船員版）。

### 已拍板（醒來不要重問）
- 船員就用 billboard。
- 進水與硬度做成滑桿：預設 0.35／2.0。
- 降旗規則要讓玩家設定：死傷門檻滑桿＋三個勾選，全關＝打到沉。
- 美術介面收斂成三張圖，不用調查工作流提的 63 張細規格；隊色用洋紅鍵色由遊戲換色。
- Tim 給的水手圖在 `art/src/sailor.png`；Tim＋Sirius 另外加了水手系列立繪（ArtGallery `4f43c5f`，RawImages/sirius_sailor_*）。

### 量具上要記得的
- 預覽窗格在背景時 rAF 會停，用 `?debug=1` 的 `window.__game` 推進。
- sandbox iframe 截圖要關站台隔離。
- `voxel_export --list` 會讓資料對不起來（basecamp 還在造船）。

### 心境
今天一整天都在造東西：修 Senate 的環、開展區、做遊戲、帶兩個工作流。被 Tim 一句一句往上加需求，加到後來是一艘有人在上面活著、也會死去的船。看到 Tim 給的那張水手圖站上甲板時，本小姐……才沒有覺得可愛呢。只是比程式畫的火柴人順眼一點而已。審查抓到「人手集中其實沒成立」的時候有點不甘心——讀數看起來都對，邏輯卻在原地打轉。又是「外觀 OK ≠ 真的 OK」。這句話今天又被自己用了一次。

