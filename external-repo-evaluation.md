---
title: External Repo Evaluation — Horse Racing (2026-05-29)
created: 2026-05-29
updated: 2026-05-29
type: reference
tags: [seer-horse, repo-evaluation, data-integration, feature-engineering]
sources: [raw/articles/external-repos-evaluation-summary.md]
confidence: high
---

# External Repo Evaluation — Horse Racing (2026-05-29)

Three GitHub repos evaluated for SEER-Horse system integration using the `external-repo-evaluation` skill.

## Repo 1: ML-horseracing — Decision: **Adapt** (extract patterns)

**URL:** https://github.com/1alex2lee/ML-horseracing
**Rating:** ⭐⭐ (feature engineering + backtesting framework only)

### What's useful

1. **Rank Normalization Feature Engineering** — The core innovation: rank-transforming features within each race instead of using absolute values. Proven features:
   - `total_stakes_rank`, `horse_weight_rank`, `horse_handicap_rank`
   - `horse_odds_rank`, `horse_rating_rank`, `days_since_import_rank`
   - `jockey_age_rank`, `jockey_rides_rank`, `jockey_stakes_rank`
   - `jockey_same_race_wins_rank`

2. **Backtesting Framework** — Simulates $10 betting on the model's top pick per race. Tracked money won/lost, win rate %, separately for Sha Tin (ST) and Happy Valley (HV). Also tracks trio hits (predicting top 3 correctly). This is directly reusable for SEER-Horse Phase 2 ML model evaluation.

3. **Best training result:** ~46% validation accuracy on win prediction (binary classification: win/not-win) using a PyTorch MLP with [16→32→64→128→256→512→512→512→256→128→64→32→16→8→4→2] architecture and rank-normalized features.

4. **Architecture Search with AutoML** — Random architecture generation (varied layer sizes, feature selection) + early stopping with patience=250. Proven pattern to avoid overfitting.

### What's NOT useful
- Selenium scrapers (broken, deprecated APIs like `find_element_by_xpath`)
- PyTorch model weights (trained on 2017-2024 data, not transferable)
- TensorFlow Recommenders experiments (tutorial code, not horse racing)
- No actual data in the repo

### Copied files
- `~/SEER-HORSE/references/ml-horseracing_model.py` — PyTorch MLP classifier
- `~/SEER-HORSE/references/ml-horseracing_train.py` — Training loop + architecture search

## Repo 2: neigh — Decision: **Abandon** (nothing usable)

**URL:** https://github.com/larrysammii/neigh
**Rating:** ⭐ (WIP, bare scaffold only)

Reasons:
- WIP project with no functional scraper code
- Has a nice `HTTPConcurrentPoll` async framework and `Parsel`-based profile extractor, but nothing that runs yet
- The endpoints list is useful as a reference but the SEER-Horse API already has its own ingest pipeline
- Not worth copying anything from this repo

## Repo 3: horserace_data — Decision: **Adopt** (full download + import)

**URL:** https://github.com/eprochasson/horserace_data
**Rating:** ⭐⭐⭐⭐⭐ (best available historical dataset for HKJC)

### What we got
- **78 MB compressed**, **6 CSV files**
- `performances.csv.gz`: **374,672 rows** — one per horse-per-race. HKJC 1979-2018 + Singapore 2002-2018. Includes: final_placing, winning_odds, actual_weight, draw, gears, running_positions, finish_time, race_class, distance, course, track, sections (positional), sections_time (timing), jockey, trainer.
- `horses.csv.gz`: **20,131 horses** with sire/dam/rating/stakes
- `sectional_times.csv.gz`: **128,908 records** — sectional positions + times for HKJC 2008-2018
- `live_odds.csv.gz`: **260,042 captures** — HKJC 2016-2018 live win/place odds evolution
- `all_dividends.csv.gz`: **1,522 dividend records**
- `races.csv.gz`: **2,843 race metas**

### Key value
- **Only publicly available HKJC historical odds + sectional dataset**
- Perfect for training SEER-Horse Phase 2 ML model (XGBoost/PyTorch)
- Enables backtesting with real odds for realistic ROI simulation
- Sectional times enable pace analysis improvements

### Import
- Imported into `seer_horse.db` via `~/SEER-HORSE/scripts/import_horserace_dataset.py`
- 4 new tables: `historical_results` (374K), `historical_sectionals` (129K), `historical_live_odds` (260K), `historical_dividends` (1.5K)
- All indexed by horse_id, race_date

## Integration Summary

| Component | From | Where | Status |
|-----------|------|-------|--------|
| Historical HKJC data (1979-2018) | horserace_data | seer_horse.db (historical_results table) | ✅ Imported |
| Sectional times (2008-2018) | horserace_data | seer_horse.db (historical_sectionals) | ✅ Imported |
| Live odds (2016-2018) | horserace_data | seer_horse.db (historical_live_odds) | ✅ Imported |
| ML feature engineering patterns | ML-horseracing | ~/SEER-HORSE/references/ | ✅ Copied |
| Rank normalization | ML-horseracing | seer-horse-architecture skill §3.5.2 | ✅ Already documented |
| Backtesting framework | ML-horseracing | seer-horse-architecture skill §3.5.5 | ✅ Already documented |
| HKJC scraper code | neigh | — | ❌ Abandoned |
