# Wiki Schema — 馬仔學堂

## Domain
香港賽馬知識庫 — 涵蓋賽道物理學、馬匹生物力學、練馬策略、投注數學、血統分析等。由 HorseTrio 嘅「識馬學堂」系列文章為基礎，持續擴展。

## Conventions
- File names: lowercase, hyphens, no spaces (e.g., `track-physics.md`)
- Every wiki page starts with YAML frontmatter (see below)
- Use `[[wikilinks]]` to link between pages (minimum 2 outbound links per page)
- When updating a page, always bump the `updated` date
- Every new page must be added to `index.md` under the correct section
- Every action must be appended to `log.md`
- **Provenance markers:** `^[raw/articles/source-file.md]` at end of paragraphs for synthesised claims
- **語言:** 粵語/中文為主，專有名詞保留英文

## Frontmatter
```yaml
---
title: Page Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
type: entity | concept | comparison | query | summary
tags: [from taxonomy below]
sources: [raw/articles/source-name.md]
confidence: high | medium | low
---
```

### raw/ Frontmatter
```yaml
---
source_url: https://example.com/article
ingested: YYYY-MM-DD
sha256: <hex digest>
---
```

## Tag Taxonomy
- **Track:** 跑道, 場地狀況, 草紋, 欄位, 彎道, 直路
- **Physics:** 流體力學, 離心力, 摩擦力, 速度, 能量消耗
- **Weather:** 雨戰, 好地, 濕滑, 硬地
- **Horse:** 跑法, 血統, 體高, 步頻, 重心
- **Strategy:** 投注, 派彩, 三重彩, 位置, 檔位
- **Racecourse:** 跑馬地, 沙田, 彎道半徑, 排水
- **Season:** 季初, 季中, 季末, 耗損週期
- **Data:** 實測數據, 雷達圖, 紅外線監測, 激光測距
- **Equestrian:** 蹄鐵, 草種, 養護, 抓地力

## Page Thresholds
- **Create a page** when a concept appears in a source or is central to the domain
- **Add to existing page** when new info builds on existing content
- **DON'T create** for passing mentions or minor details
- **Split** when a page exceeds ~200 lines

## Entity Pages
One page per notable entity (馬匹、騎師、練馬師).

## Concept Pages
One page per concept (跑道物理、欄位優勢、雨戰模型等).

## Comparison Pages
Side-by-side analyses (e.g. 跑馬地 vs 沙田).

## Reference Pages
Lookup tables, formula sheets, quick-reference data.

## Update Policy
- Newer sources generally supersede older ones
- If contradictory, note both positions with dates and sources
- Mark in frontmatter: `contradictions: [page-name]`