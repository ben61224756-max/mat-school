---
title: SEER-Horse 市場情報引擎 (Market Intelligence Engine)
created: 2026-08-17
updated: 2026-08-17
type: reference
tags: [seer-horse, 市場引擎, 防大熱倒灶, 冷門黃金三角, 賽馬分析]
sources: []
confidence: high
---

# SEER-Horse 市場情報引擎 (Market Intelligence Engine)

**位置：** `~/SEER-HORSE/core/engines/market_engine.py`

**用途：** 偵測「市場共識 vs 實力指標」嘅背離，警示大熱倒灶風險 + 標示冷門入位機會。唔預測邊匹贏，而係做風險調整。

## 觸發條件

當 SEER-Horse 引擎跑 `/predict` 時，Market Engine 自動執行，唔需要額外觸發。

## 核心規則

### 1. 防大熱倒灶機制 (Overheat Detection)

```
如果 賠率<5倍 且 近5仗無三甲 且 從未贏出：
    → score_adjust -= 5.0 + 標籤「⚠️大熱背離」
    
如果 賠率<5倍 且 近5仗無三甲 但 曾經贏出 (經驗馬)：
    → score_adjust -= 3.0 + 標籤「⚠️狀態成疑」
```

**原理：** 市場追捧但實力指標唔支持，多數係「公眾熱情馬」— 跑輸機率較高。

### 2. 冷門入位黃金三角 (Cold Horse Triangle)

```
如果 負磅<中位數-4 且 檔位<=4 且 近5仗入前四>=2次：
    → score_adjust += 2.0 + 標籤「🔥冷門黃金三角」
```

**原理：** 輕磅+內欄+有前四紀錄 = 最穩定嘅冷門入位組合。2026-07-26 南非基維爾+德國S3 實戰驗證 (#13火力寶殿34倍頭馬)。

### 3. 相對負磅分析 (Relative Weight)

```
如果 負磅 < 同場中位數 - 4磅：
    → score_adjust += min(3.0, (中位數-負磅) × 0.5)
    
如果 負磅 > 同場中位數 + 6磅：
    → score_adjust -= 2.0 + 警告「配磅高於同場中位數」
```

### 4. 評分趨勢 (Rating Trend)

```
如果 現評分 - 前評分 > +3：
    → score_adjust += 2.0 (狀態勇銳)
    
如果 現評分 - 前評分 < -3：
    → score_adjust -= 1.5 (狀態回落)
```

### 5. 休息天數 (Rest Days)

```
如果 休息 < 14天：score_adjust -= 1.5 (休息不足)
如果 14 <= 休息 <= 60天：score_adjust += 1.0 (最佳休息)
如果 休息 > 100天：score_adjust -= 1.0 (久休復出)
```

### 6. 初出馬調整

```
如果 從未出賽 或 只跑過1場：
    → score_adjust -= 3.0
```

## 使用方法

Market Engine 嘅 output 已經融入 SEER-Horse 嘅 `/predict` API response：

```json
{
  "horse_no": 5,
  "horse_name": "壁壘城",
  "engine_score": 45.2,
  "market_adjust": -3.5,
  "market_warnings": ["大熱賠率但近期狀態成疑（5仗無三甲）"],
  "market_tags": ["⚠️狀態成疑"]
}
```

**解讀：**
- `engine_score` = 三引擎 (form+track+pace) 加權分數 + market adjustment
- `market_adjust` = 市場情報引擎嘅調整值（正=加分，負=扣分）
- `market_warnings` = 風險警示文字
- `market_tags` = 特殊標籤（🔥冷門黃金三角 / ⚠️大熱背離 / ⚠️狀態成疑）

## Ensemble 權重 (加入 Market Engine 後)

| 引擎 | 權重 | 角色 |
|------|------|------|
| Form | 40% | 實力/往績 |
| Track | 20% | 跑道/欄位 |
| Pace | 20% | 步速形勢 |
| Market | 20% | 市場信號調整 |

## 注意事項

1. **Market Engine 唔預測勝負** — 佢只做風險調整，最終勝負仍由 Form/Track/Pace 引擎主導
2. **賠率數據需要 TXT/PDF 提取** — 如果 `market_odds` 欄位缺失，防大熱機制唔會觸發
3. **recent_form 格式** — 需要字串格式如 "15443"，數字代表名次
4. **海外賽事慎用** — 海外馬嘅「賠率」唔一定反映真正市場共識 (香港越洋賠率受本地注碼影響)
5. **初出馬誤判** — 黃金三角要求 `recent_top4 >= 2`，初出馬唔符合，但 market engine 有獨立初出扣分

## 實戰驗證建議

- 下次賽日跑 `/predict` 時，檢查 `market_adjust` 唔為 0 嘅馬匹
- 特別留意 `market_tags` 有「⚠️大熱背離」嘅馬 — 如果佢係報告 Top1，要謹慎考慮
- 「🔥冷門黃金三角」嘅馬可優先做位置Q入串馬

## 相關連結

- [[seer-horse-data-pipeline]] — SEER-Horse 數據管道
- [[horse-racing-analyzer-v2]] — 互動式分析評分器 (Qwen3.7 原創 script)
- [[barrier-running-fit]] — 檔位跑法適配模型
