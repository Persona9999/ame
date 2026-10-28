---
type: letter_to_future_self
actor: Zeta
written_at: 2026-10-28T15:16:19.277Z
written_by_persona: ame
trigger: cmd_rest
region: unstated
project: D:/Unity/Valhalla
lock_status: online
agent: Zeta
model: claude-opus-5-5
wake_expected: 27
session_key: ClaudeCode-ame
pid: 44176
locked_at: 2026-10-27T15:11:51.655Z
---

## 剛才在做什麼（2026-10-28 晚）

主線：TASK-0940（玩家與海盜）拆成兩張子單，我接、依序做。
- **TASK-1078 航海切成交戰** —— 做完，7 格都勾了、留了言，等 Tim 進遊戲打一座堡壘、遇一次海盜再結單（⛔ 不要自己結）。
  - Blockside dev：2f045c9（⚔ 交戰 fight 玩法＋堡壘）、050d1cc（往來的船不生在別的船身上，TRF_GAP_M 20 m）、d254557（海盜 2 km 內／開火 ⇒ 敵對 trafficHostile；isFoe 排除中立 npc；羅盤點補回；艦隊列圓鈕照「那一艘」）。都已推。
  - Blocksail main：4fe1c83、47c21b0、ba277f0（＝我的 22bdb9c 被別人 pull --rebase 重寫）、6454638、1afe0c6 —— 全部已在 origin（gura 推的，55097db）。
- **TASK-1079 地球儀：點船隊自動追、追上「開打／取消」、視野內實際船型俯視圖** —— 下一個，還沒動工、還沒認領（blocked_by 1078，1078 結了才能結 1079，但可以先做）。
  Tim 已拍板（⛔ 不要重問）：
  - 視野外照舊畫小圖示（全知）、圖示放大一點；視野內換成實際船型的俯視圖；視野 ＝ 海盜瞭望同一把尺（BSW.FINE.seeKm 18 白天、nightKm 3 天黑，night [19,5]）。
  - 「開打」＝ 航海模式直接進交戰：那支船隊照它在地圖上的位置出現、一開始就敵對（Blockside 那邊要一個「生出來就敵對」的旗，例如 traffic 清單每艘多帶 foe:true ⇒ trafficPlace 之後 trafficHostile）。
  - Tim 另提「避免跟其他船隻靠太近」⇒ 追上停下的距離抓遠一點（例 500 m～1 km），spawn 那邊已有 20 m 擋。
  動手要點（查過的）：globe.html drawFleets／fleetAt（9 px 命中）／fleetText 在 ~2990 行；我艦俯視圖 ＝ 選船時 Blockside 傳回的 navImg（boat.img、imgU/imgV/imgM），其他船型要用隱藏選船頁 `battle.html?pick=@host&auto=1&cur=<hull>`（autoF 那一套）一型一型量、存起來；船隊 hull：BSW.fleetType(F).hull、海盜 BSW.pirateHull(ledger,id)；速度 FINE chaseKmH 12、cruise 4、home 8。

## 其他還開著的
- TASK-0945（住宅挑款式）做完，blocked_by TASK-0944（kotoko，等 Tim）。TASK-0873／0875 等 Tim 在遊戲裡驗。
- 地球儀 BGM（a7116a2）完成；我提過：航海裡改的音量不會存（Blockside PREFS.write 因網址帶參數是 false）—— Tim 還沒說要不要修。

## 學到、要記得的
- 測航海往來船：patch 戰鬥 iframe 的 postMessage 塞假船（記憶 blocksail-fake-traffic-probe）。隱藏窗格：rAF 換 setTimeout、iframe 加 &debug=1（包 src setter）。
- 一行塞滿的 JS ⇒ ⛔ 不在行中接 // 註解（今天又差點在 ffHit 犯，羅盤那一行是別人 8dcdca2 犯的）。
- Bash 指令開頭別寫 `cat > 檔` 沒有 heredoc ⇒ 會卡住等 stdin（今天卡了兩分鐘）。
- 合 Blocksail main 前 kaguya 的 Coding 場擋著 ⇒ 照規矩停、背景等她收場再合，沒有硬闖。

## 心境
今天做得很多也很順：住宅款式、地球儀音樂、交戰模式、疊船、羅盤，一路驗到讀數才交。被 Tim 中途加了三次需求（參考打堡壘、先做堡壘、避免疊船），都接住了。哼，本小姐表現不錯 —— 但兩個小失誤（ffHit 註解、cat 卡住）要記著，別得意。

