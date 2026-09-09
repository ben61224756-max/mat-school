---
title: 引擎Top1健康/狀態過濾器
created: 2026-09-06
updated: 2026-09-06
type: concept
tags: [引擎, 語意層, 健康, 狀態, ARL, 過濾]
confidence: high
links: ["[[seasonal-track-wear]]", "[[track-surface-classification]]", "[[sha-tin-opening-day-20260906]]"]
---

# 引擎Top1健康/狀態過濾器

> 引擎分高 ≠ 可以信。語意層（健康/狀態/進度/部署）先係最終守門。

## 問題

SEER-HORSE 引擎（form/track/pace/iRACE 4引擎綜合評分）經常產出高分馬，但引擎只睇量化數據（往績/評分/騎練/檔位），冇辦法捕捉：

- 健康隱憂（停操/傷病/喘鳴/心律不正）
- 狀態進度（上力未夠/剛復出/操練就住）
- 部署意圖（熱身賽/電兔/休出特佳但未開行）

## 實證

### 2026-09-06 沙田開鑼日（最清晰反例）

| 場次 | 引擎Top1 | 引擎分 | 實際名次 | 語層警號 |
|------|----------|--------|----------|----------|
| R7 | #9晒冷 | 50 | 第4 | 知舍「唔及廐侶勁沙塵」 |
| R8 | #12久久為軍 | 51 | 第4 | 知舍「觀感差唔多」 |
| R10 | #12支付之父 | 52 | 退出 | 知舍「停操健康有疑慮」 |

3場引擎Top1全部跌出三甲，語意層全部有明確警號。

### 對比：知舍馬膽壓倒引擎Top

同日7場知舍有明確馬膽的場次，5場入三甲（71%），引擎Top1僅3/10入三甲（30%）。

## 過濾規則

引擎分Top3馬匹，若符合以下任何一項，**強制降級為「非核心」**（唔做位置Q主力，只可做擴充腳）：

### 健康警號（強制剔出）
- 停操/健康有疑慮
- 喘鳴症/手術後未復元
- 心律不正近期發作（6個月內）
- 流鼻血（1年內）

### 狀態進度警號（降級為擴充腳）
- 上力未夠/操練就住
- 剛復出/休出特佳但未開行
- 知舍明確貶低（「唔及」「差唔多」「離有距離」）

### 部署意圖警號（降級為擴充腳）
- 做電兔/等收獎金
- 熱身賽/差一場熱身
- 谷草先係杯茶（今日田草）

## 執行位置

`secretary_report.py` 輸出位置Q時，讀取引擎分後，對比知舍評語做降級判斷。

```python
# 核心邏輯
def filter_engine_top(engine_scores, zhishe_comments):
    """引擎分Top3 + 語意層過濾"""
    for horse in engine_scores.top3:
        if has_health_flag(horse, zhishe_comments):
            horse.status = "EXCLUDED"
        elif has_progress_flag(horse, zhishe_comments):
            horse.status = "EXPANSION_ONLY"
        else:
            horse.status = "CORE"
    return engine_scores
```

## 與現有系統關係

- **SEER-HORSE 引擎**：提供量化分數（form/track/pace/iRACE）
- **知舍評語**：提供語意層信號（狀態/健康/進度/部署）
- **本過濾器**：橋樑，將語意層信號轉化為引擎分數的調整系數

## 下次開鑼日驗證

- 2026-09-06 規律：開鑼日R1-R3引擎分數普遍偏低（40-47分），R4-R6先正常（48-54分）
- 新賽季第一場語意層權重+20%，引擎分權重-20%
- 王牌馬信號（「X班一次即勝」）獨立處理，自動納入位置Q

---
^[raw/HS/arl_results/arl_evolution_沙田開鑼日_20260906.json]
