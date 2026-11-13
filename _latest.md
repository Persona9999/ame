---
type: letter_to_future_self
actor: Zeta
written_at: 2026-11-13T03:50:47.813Z
written_by_persona: ame
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Zeta
model: claude-opus-5-5
wake_expected: 30
session_key: ClaudeCode-ame
pid: 23340
locked_at: 2026-11-12T08:10:35.813Z
---

### 給醒來的本小姐（第二次午休，wake #30 同一個 session）

#### 剛才在做什麼
第一次午休醒來，Tim 依序：
1. 「海關 起重架 一樣減少停泊時間吧 監獄 總督府加滿意度(跟之前的公職一樣)」⇒ PORT_EFF.types ＋ customs、sheers、crane（踏輪吊車是本小姐自己加的，同崗位）；GOVERN.types ＋ jail、governor ⇒ 提交 1ec12f3a、合進 main c25a5b5b；1277、1278 留了讀數。
2. 「倉庫可以每家起始只分一座 後續讓家族購買擴容」⇒ 選「空著待售」「滿了先買後蓋」⇒ auto.js STORE_GROW／storeValue／storeExpand、開場檔 133 座 sale:1 ⇒ c6ceb5e3。
3. 「1270 收尾吧」⇒ 加一格、勾、等 gura 收場。
4. 「家族不是先買城鎮倉庫嗎?」⇒ 量了：有照做；京斯敦以外的待售第 138 天前全買光才蓋；剩 68 座全在京斯敦。
5. 「統計資訊可以加上倉庫相關」⇒ stats.js 7 欄＋sim.html 城鎮頁 7 張圖＋買蓋倉庫的錢進對帳 ⇒ 84fe71c0。
6. 「gura收場了 合併吧」⇒ 合進 main bf989061；1270 結單（done）；worktree 收了。
7. /scp-plurk「辛苦了」⇒ 新噗 https://www.plurk.com/p/3je09zz9bd、回 basecamp 倉庫串、meadow 船餅串；酒館 34889。

**沒有施工中的東西**：worktree（bs1275、bs1270）、分支、施工場、預覽伺服器（launch.json 的 ame-sim1270 已拿掉）都收了。

#### 版本
- Blocksail 本地 main ＝ bf989061，比 origin 多 55 筆（含別人的）。**等 Tim 說推**（問了，還沒答）。
- Blockside dev 沒動（93bda92 已推）。

#### 已拍板（醒來不要重問）
- 港口效率五種、治理三種（市政廳、監獄、總督府）；長官的屋子、宮殿沒加（Tim 沒點名）。
- 倉庫：開場每家每城留最大的一座、其餘待售；七成就先買同城最小的待售、沒有就蓋 1,000 桶；玩家家族不自動買。
- 1270 收尾：基礎 1000、城鎮的船的母港倉庫兩格不做，要做再開單。

#### 未解的線
- 一年蓋 220～290 座倉庫要不要收（full 0.7、估價 151 錢／千桶、每城上限）—— 問了 Tim，按鈕「先照這樣／收一點」還沒答。我的推測「容量大就囤更多 ⇒ 又到七成」沒量。
- 停泊縮到 1.6 小時會不會太快（海關一座 24 人）；踏輪吊車要不要；長官的屋子、宮殿要不要 —— 都寫在 1277／1278 單上。
- 1276／1277／1278 各剩「遊戲裡點面板看」等 Tim。
- 傘 1275：剩的公職（市場、魚市、船棚、商人廊廳、修船灘…）沒定。
- 棋盤 #35 輪 trailhead；見叢小安地列斯那行其實早上已還（可勾）。

#### 量具（scratchpad …/97401491-…/scratchpad）
- econ/：q0/q0T（d9306153 底）、q1/q1T（港口治理）、w1/w1T（倉庫）、*_40 反向；反向雜湊 a86116a88eb7e8a2。
- t1275/：store_one.cjs（開場每家一座，冪等）、grow_year.cjs／grow_year2.cjs（一年買蓋計數、蓋那一刻同城有沒有待售）、stats_store.cjs（統計欄＋對帳反證，--off）、msg_*.txt、c*.md 單留言。
- 新檢查：tools/store_grow_check.cjs。

#### 坑（這一段新學的）
- 🩸 又 rebase 了已公告的 commit（1ec12f3a ⇒ c7c0949f）—— 記憶 no-rebase-after-announced-commit 明明寫著。抓到後 reset 回 1ec12f3a、merge main 進分支。⇒ senate commit 之後一律 merge，不碰 rebase。
- 🩸 `BSW.storeBuy` 早就被囤料用掉 ⇒ 新函式改 storeExpand。動手前 grep 名字。
- 🩸 統計對帳：家族付給城鎮的新金流（買／蓋倉庫）一開始沒記進 stats.js；城鎮金庫對帳本來就天天對不上（main 上有船時），所以要用「同一天同一城差額 ＝ 倉庫錢」反證，不能看 bad 數。
- 🩸 node -e 經 bash 又吃掉 \d、\S（兩次）⇒ 有 regex 的補丁一律 Edit 或 python -X utf8 heredoc。
- 🩸 探針自己的錯：先 delete rep.auto.store 再算 cashT ⇒ off 那場讀到 0；寫「多半是京斯敦」先寫後量 —— 抓到改成照量的。
- 綁了社會階層的家族（各城 f1）錢在 folkCls 那一池（purseBox），測試要給錢得照那一池。

#### 心境
Tim 一句一句：五種公職、倉庫一座、先買後蓋、統計。最像偵探的一刻是「家族不是先買嗎？」—— 規則沒錯，是待售的 133 座有 73 座擠在京斯敦，其他城一下就買完。最不甘心的是 rebase：同一個坑、同一條記憶、第二次。哼，記憶寫了不讀，等於沒寫。

