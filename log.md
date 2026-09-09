# Wiki Log

> Chronological record of all wiki actions.
> Format: `## [YYYY-MM-DD] action | subject`

## [2026-09-06] comparison | 沙田開鑼日覆盤 2026-09-06
- Created: comparisons/sha-tin-opening-day-20260906.md
- 沙田馬場全10場終極分析賽後對答案（R1-R10）
- 位置Q 2/10命中（20%），頭馬6/10（60%），位置P 8/10（80%）
- 核心發現：引擎Top1入三甲3/10（30%）vs 知舍馬膽入三甲5/7（71%）
- 新概念誕生：引擎Top1健康/狀態過濾器（語意層守門）
- 引擎Top1健康/狀態過濾器：引擎分高唔等於健康/狀態好
- Created: concepts/engine-top1-health-filter.md
- Updated: index.md（Concepts加engine-top1-health-filter，Comparisons加sha-tin-opening-day-20260906，Total pages 49→50）

## [2026-09-05] comparison | 希啶馬場賽馬日終極分析 2026-09-05
- Created: comparisons/haydock-review-20260905.md
- 英國希啶馬場全 8 場終極分析（S1-1 至 S1-8）
- 天氣：軟地（Soft），預報微雨 16°C，BST 夏令時
- 位置Q 5/8 命中（62.5%），動態調整 2/3 有效（S1-6/S1-7 命中，S1-8 走寶 #9 單角赤麟 22倍）
- 關鍵教訓：膠沙0勝唔代表長途唔得（S1-4 #5風裡行）、初出冷門難預測、場地轉好前置馬反彈
- Updated: index.md（Total pages: 47→48）

## [2026-08-21] comparison | 約克賽馬日終極分析 2026-08-21
- Created: comparisons/york-racing-day-20260821.md
- 英國約克馬場全 7 場（S3-1 至 S3-7）終極分析
- 位置Q 每場 3-4 匹互串；讓賽場（S3-1/5/7）擴至 4 匹
- 天氣：好地，15:00 BST 落 1.2mm 毛毛雨（影響 S3-3/S3-4），陣風 22-35km/h
- 分析方式：PDF×7 + 名家專欄（魏崇達 + Ramsden/Hughes/Landi）+ TXT + Open-Meteo + llm-wiki 知識庫（8-19/8-20 同場覆盤）
- Updated: index.md（Comparisons 加條目，修正 york-ebor-20260819 行 `|||` 管道 bug，Total pages 44→45）

## [2026-08-20] create | 終極分析報告 2026-08-20 約克伊波賽期
- Created: ~/賽馬/20260820/終極分析_20260820_約克伊波賽期.md
- 英國約克馬場 York Racecourse，Ebor Festival 第二日
- 7 場越洋賽事（S2-1 至 S2-7），六源交叉驗證
- 天氣：好地，總雨量 0.9mm，陣風 30-35km/h
- 分析方式：PDF×7 + 跑道分析 + TXT（manus + 魏崇達 + 3馬評家 + qwen3.7 + DeepSeek v4）
- Updated: index.md（Comparisons 加條目）

## [2026-08-20] comparison | 約克伊波賽期（York Ebor Festival）終極分析覆盤 2026-08-19
- Created: comparisons/york-ebor-festival-review-20260819.md
- 英國約克馬場全 7 場終極分析覆盤
- 位置Q 71%命中率（12/17），S1-3 全中，S1-6/7 最差
- 關鍵教訓：讓制輕磅馬優勢（#17 山路實際 119磅）、檔位影響非絕對、六源交叉驗證有效性
- 觸發引擎融合：patch `overseas_engine_score.py` 加入「見習騎師減磅效應」同「連勝勢頭」概念
- Updated: index.md（Comparisons 加條目）

## [2026-08-16] concept | 互動式賽馬分析評分器 v2.0
- Created: concepts/horse-racing-analyzer-v2.md
- 大水牛用 v1.0 做分析後，修正雙重計分 bug + 加入騎練評分/跑法偏好/狀態標記
- 位置Q分析工具，用互動式 terminal 輸入，輸出排序結果
- Updated: index.md（Total pages 43 → 44，References 加條目）

## [2026-08-15] comparison | 海外賽馬日覆盤 — 無新比賽，skip
- 基準：上一次錄入 2026-08-13（覆蓋至 08-09 霍珀加滕+多維爾）
- 掃描 ~/HS/arl_results/arl_evolution_*賽馬日*.json：最新賽馬日仍為 20260809，08-09 之後無新海外賽馬日
- 無新比賽，唔開新檔，skip

## [2026-08-13] comparison | 海外賽馬日覆盤 2026-07-26 至 08-09
- Created: comparisons/overseas-race-days-review-2026-07-26-08-09.md
- 8 個賽日覆盤：基維爾+慕尼黑(07-26)/古活盃(07-28)/薩塞克斯(07-29)/蘭秀(07-30)/英皇佐治(07-31)/德法雙賽日(08-02)/識價盃(08-08)/霍珀加滕+多維爾(08-09)
- 沉澱 10 條跨賽日穩定規律（大熱過熱=死、膠沙縮程=寶藏、擴充級=頭馬寶藏、強共識揀第1選但第2/3選揀次強信號、TXT名家5位完整對齊、英國分級賽大熱僅G1+<2可靠等）
- Updated: index.md（Total pages 42 → 43，Comparisons 加條目）

## [2026-07-19] reference | 新賽季前途無量馬 Watchlist
- 大水牛盤點 2026-2027 新賽季具升班潛質嘅 11 匹焦點賽駒（來源：~/賽馬/2026-2027賽季 前途無量馬.txt）
- Created: references/promising-horse-watchlist-2026-27.md
  - A組（4匹已有 0607 沙田實戰記錄）：支付之父(L159)/歷勝(L199)/超輕鬆(L148)/喜慶寶(K583)
  - B組（7匹待首戰）：巴閉精(L040)/超和平(L226)/實力股(L411)/利高八斗(K542)/櫻花酒杯(L230)/堅先生(L232)/極上紗瓏(K585)
- Updated: index.md（Total pages 41 → 42，References 加條目）
- 9月新賽季開鑼後，相關馬首戰會自動加入 comparisons/ 並回鏈本 watchlist

## [2026-07-19] update | 前途無量馬 Watchlist 加表現觀察
- 來源名單更新：每匹加咗一句表現描述（原 "待首戰" 標註修正——已見試閘/預賽觀察）
- Updated: references/promising-horse-watchlist-2026-27.md
  - 全 11 匹加「表現觀察 + 初步跑法判斷」欄
  - 重點信號：極上紗瓏(K585)四戰四勝、實力股(L411)拋離5-6馬位、超和平(L226)一放到底
  - 場合（第五場/第九場）標為待核實，正式賽開鑼後以實際數據覆核跑法定位

## [2026-07-19] update | 前途無量馬 Watchlist 同步來源微調
- 來源名單再更新：用戶**刪除**實力股「第五場」、極上紗瓏「第九場」場合字眼（其餘9匹不變）
- Updated: references/promising-horse-watchlist-2026-27.md
  - 表內實力股(L411)/極上紗瓏(K585) 去掉場合指定，改以「直路」概括
  - 9月關注第3點註明場合字眼已刪除、評語無指定場次
  - updated bump 2026-07-19（同版日，第二度更新）

## [2026-06-07] comparison | 4日賽馬記錄補齊
- 一次過補齊之前未記錄嘅賽馬日
- Created: comparisons/sha-tin-review-20260531.md（沙田B欄日賽）
- Created: comparisons/happy-valley-review-20260603.md（跑馬地C欄夜賽）
- Created: comparisons/epsom-review-20260605.md（英國葉森第一日）
- Created: comparisons/epsom-sa-review-20260606.md（英國葉森+南非基維爾）
- Updated: index.md（總頁數 32→37）

## [2026-06-07] comparison | 沙田黃昏賽覆盤 2026-06-07
- 增加沙田賽馬實戰記錄，對之後再有馬出賽時參考
- Created: comparisons/sha-tin-dusk-review-20260607.md
- Updated: index.md

## [2026-05-27] create | 馬仔學堂 Wiki 初始化
- Domain: 香港賽馬知識庫 — 賽道物理、馬匹生物力學、練馬策略、投注數學
- 建立 SCHEMA.md, index.md, log.md
- 目錄結構: concepts/, references/, comparisons/, queries/, raw/articles/
- Pages created: 6

## [2026-05-27] review | 首次實戰覆盤 — 2026.5.27 跑馬地B欄夜賽
- Created: comparisons/first-live-review-20260527.md (9場賽後分析，2/9頭馬命中，5 lessons learnt)
- 更新 index.md — Total pages: 31 → 32, Comparisons 首頁

## [2026-05-27] ingest | 28個馬場常用專業術語
- Source: https://www.horsetrio.com/tips/28%E5%80%8B%E9%A6%AC%E5%A0%B4%E5%B8%B8%E7%94%A8%E5%B0%88%E6%A5%AD%E8%A1%93%E8%AA%9E
- Raw saved: raw/articles/28-racing-terms.md
- Updated: references/racing-terminology.md (加入28個術語表)
- 更新 index.md — Total pages: 30 → 31

## [2026-05-27] ingest | 15個賽馬數據專業術語
- Source: https://www.horsetrio.com/tips/15%E5%80%8B%E8%B3%BD%E9%A6%AC%E5%B0%88%E6%A5%AD%E8%A1%93%E8%AA%9E
- Raw saved: raw/articles/15-racing-terms.md
- Created: references/racing-terminology.md (賽馬專業術語速查 — 疊數/偏差/狀態評級)
- 更新 index.md — Total pages: 29 → 30

## [2026-05-27] ingest | 識馬學堂（六）馬匹的跑法與數理化
- Source: https://www.horsetrio.com/tips/%E8%AD%98%E9%A6%AC%E5%AD%B8%E5%A0%826
- Raw saved: raw/articles/running-style-quantified.md
- Created: concepts/running-style-quantified.md (跑法數理化分類 — 逃先差追公式、距離計分)
- Created: concepts/barrier-running-fit.md (檔位跑法適配模型)
- Created: references/racecourse-running-style-matrix.md (沙田&跑馬地跑法勝率矩陣)
- Created: references/going-track-index.md (度地儀指數完整分類)
- 更新 index.md — Total pages: 25 → 29
- 全套六篇識馬學堂已全部 ingest！ 🎉

## [2026-05-27] ingest | 識馬學堂（四）馬匹的裝備與訓練效益
- Source: https://www.horsetrio.com/tips/%E8%AD%98%E9%A6%AC%E5%AD%B8%E5%A0%82%EF%BC%88%E5%9B%9B%EF%BC%89%E9%A6%AC%E5%8C%B9%E7%9A%84%E8%A3%9D%E5%82%99%E8%88%87%E8%A8%93%E7%B7%B4%E6%95%88%E7%9B%8A
- Raw saved: raw/articles/equipment-and-training.md
- Created: concepts/equipment-biomechanics-blinkers.md (眼罩效應 — 視野限制公式、類型效益矩陣)
- Created: concepts/trial-work-dynamics.md (拍跳訓練動力學 — 競速激發曲線、效益分級)
- Created: concepts/morning-work-metabolic.md (晨操代謝監控 — 虛假狀態三徵、能量儲備判讀)
- Created: concepts/training-load-cycle.md (操課週期負荷理論 — 訓練適應曲線、課期黃金比例)
- Created: concepts/track-safety-cutting-rules.md (賽道安全切線規則 — 動態安全距離、騎師風險判斷)
- 更新 index.md — Total pages: 20 → 25

## [2026-05-27] ingest | 識馬學堂（三）馬匹的策略與步速整合
- Source: https://www.horsetrio.com/tips/%E8%AD%98%E9%A6%AC%E5%AD%B8%E5%A0%823
- Raw saved: raw/articles/pacing-and-tactics.md
- Created: concepts/drafting-fluid-dynamics.md (遮擋流體力學 — 風阻公式、遮擋效益)
- Created: concepts/pacing-energy-model.md (步速經濟學 — 熵值模型、三段式能量分配)
- Created: concepts/racing-style-genetics.md (跑法基因適配理論 — 血統矩陣、戰術變異)
- Created: concepts/outside-draw-compensation.md (外檔蝕位補償模型 — 蝕距換算、U型戰術)
- Created: references/tactic-six-dimension.md (T.A.C.T.I.C. 六維策略模型)
- 更新 index.md — Total pages: 14 → 20

## [2026-05-27] ingest | 識馬學堂（二）馬匹的試閘與穩定性評估
- Source: https://www.horsetrio.com/tips/%E8%AD%98%E9%A6%AC%E5%AD%B8%E5%A0%822
- Raw saved: raw/articles/trial-and-stability.md
- Created: concepts/trial-evaluation-rider.md (RIDER 動態評估模型 + T-TIME 締速校正)
- Created: concepts/horse-stability-model.md (生命周期曲線、狀態峰值預測、3D-SELECT)
- Created: concepts/horse-injury-diagnosis.md (傷病影響矩陣、隱性偵測、早期預警)
- 更新 index.md — Total pages: 11 → 14

## [2026-05-27] ingest | 識馬學堂（一）馬匹的生理與外觀解析
- Source: https://www.horsetrio.com/tips/%E8%AD%98%E9%A6%AC%E5%AD%B8%E5%A0%821
- Raw saved: raw/articles/horse-physiology.md
- Created: concepts/horse-respiratory.md (呼吸道力學 — 喘鳴症、氧代謝衰減模型)
- Created: concepts/horse-injury-biomechanics.md (運動損傷與步態診斷)
- Created: concepts/neck-biomechanics.md (頸項生物力學 — 雞公頸指標)
- Created: references/bio-scan-diagnosis.md (Bio-SCAN 四維診斷法)
- 更新 index.md — Total pages: 5 → 11

## [2026-05-27] ingest | 識馬學堂（五）馬場的跑道與速度數學
- Source: https://www.horsetrio.com/tips/%E8%AD%98%E9%A6%AC%E5%AD%B8%E5%A0%825
- Raw saved: raw/articles/track-and-speed-math.md
- Created: concepts/track-surface-classification.md (場地狀況分類)
- Created: concepts/track-physics.md (跑道物理學 — 彎道離心力、草紋滲透、耗損)
- Created: concepts/lane-advantage-matrix.md (欄位優勢矩陣 — C+3/B/A 勝率數據)
- Created: concepts/rain-race-model.md (雨戰模型 — 沙田雨量與勝率關係)
- Created: concepts/seasonal-track-wear.md (季末跑道耗損週期 — 草皮疲勞指數)
- Created: references/dts-triangle-strategy.md (D.T.S. 三角策略 — 投注應用框架)
## [2026-06-24] ingest | 跑馬地夜賽 2026-06-24
- Source: 馬會排位PDF (20260624跑馬地2.pdf) + 知舍貼士 (20260624.txt)
- Created: comparisons/happy-valley-20260624.md (跑馬地A欄夜賽 — 九場賽事記錄)
- 更新 index.md — Total pages: 39 → 40
## [2026-08-22] ingest | 澳洲蘭域賽馬日終極分析 2026-08-22
- Source: HKJC越洋特刊 PDF ×8 (S4-1至S4-8) + TXT貼士 + Open-Meteo天氣
- Created: comparisons/randwick-analysis-20260822.md (蘭域全8場終極分析 — S4-1至S4-8)
- 膠沙縮程排查：全日零發現，其他AI標記嘅馬(換崗儀式/萌芽期/最堅鑽/驍將星)經PDF核對全部否認
- 位置Q每場3匹互串；全日最穩S4-6#8意飛地；焦點S4-7雲絲仙子錦標秋暉vs紅妝力證
- 更新 index.md — Total pages: 45 → 46

## 2026-08-22 — 約克S5覆盤 + 漏選六特徵
- Created: comparisons/york-s5-postmortem-20260822.md (四場postmortem Q1/4頭馬3/4 + 漏選六特徵F1-F6)
- 核心發現：六條遺漏特徵入面四條屬提取/流程層唔係判斷力問題——PDF白紙黑字但冇抽出嚟
- F4莫雅空降讓賽/F5 Wathnan大馬主/F6直路檔位豁免係新增判斷規則
- 已patch skill horse-race-day-field-extraction（提取checklist）
- Updated index.md — Total pages: 46 → 47

## [2026-09-06] comparison | 巴登巴登+巴黎隆尚覆盤 S4-1 + S5-1至S5-4
- Created: comparisons/baden-baden-s4-s5-20260906.md
- 德國巴登巴登 S4-1 Baden大賽 G1 2400m + 法國巴黎隆尚 S5-1至S5-4 全5場終極分析賽後對答案
- 位置Q 4/5 (80%)，頭馬 1/5 (20%)，三重彩 0/1
- S5-3 尼爾錦標：頭馬+位置Q全中（#1 風雲天 Track分93壓倒性）
- S5-4 福伊錦標：三重彩走漏#2 驁霸（用戶3注都冇包#2，#2跑第3）
- S4-1 #1 遠飛標槍 評分[121]最高但只得第4，#4 精誠所至 跑出頭馬
- 更新 index.md — Total pages: 50 → 51（Comparisons +1）
