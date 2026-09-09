---
title: SEER-Horse Data Pipeline & Historical Dataset
created: 2026-05-29
updated: 2026-05-29
type: reference
tags: [seer-horse, data-pipeline, database, historical-data]
sources: []
confidence: high
---

# SEER-Horse Data Pipeline & Historical Dataset

## Database Tables

### Core Prediction Tables (from PDF parsing)
| Table | Rows | Purpose |
|-------|------|---------|
| race_meetings | variable | Per day + venue |
| races | variable | Per race within a meeting |
| horses | 12,945 | HKJC horse profiles (from PDF) |
| runners | variable | Per horse-per-race entries |
| results | variable | Race results |
| predictions | variable | Engine predictions |
| weather | variable | Open-Meteo weather |
| jockeys | variable | Jockey profiles |
| trainers | variable | Trainer profiles |

### Historical Tables (from horserace_dataset import)
| Table | Rows | Source | Coverage |
|-------|------|--------|----------|
| historical_results | 374,672 | performances.csv.gz | HKJC 1979-2018 + SGTC 2002-2018 |
| historical_sectionals | 128,908 | sectional_times.csv.gz | HKJC 2008-2018 |
| historical_live_odds | 260,042 | live_odds.csv.gz | HKJC 2016-2018 |
| historical_dividends | 1,522 | all_dividends.csv.gz | HKJC 2016-2018 |

## Import Script

```bash
cd ~/SEER-HORSE
PYTHONPATH="$PWD" python3 scripts/import_horserace_dataset.py
```

Location: `~/SEER-HORSE/scripts/import_horserace_dataset.py`
Data: `~/SEER-HORSE/data/horserace_dataset/` (6 gzip CSV files, 78MB total)

## Key Fields in historical_results

- `horse_id` — Brand number (e.g., L247, K066) or SGTC numeric ID
- `race_date` — Date of race
- `race_country` — HK or SG
- `final_placing` — 1st, 2nd, 3rd, etc.
- `winning_odds` — Final dividend odds
- `actual_weight` — Carry weight
- `draw` — Barrier position
- `gears` — Equipment (e.g., B, TT, H)
- `distance` — Race distance in meters
- `course` — Course code
- `track` — Turf/AllWeather
- `race_location` — sha tin / happy valley / S (Singapore)
- `sections` + `sections_time` — JSON positional/timing data
- `jockey_name`, `trainer_name`
- `going` — G/GF/GY/Y/S/H

## Planned Data Pipeline (Phase 2)

```
horserace_dataset (historical)
       ↓
historical_results table
       ↓
Feature Engineering (rank normalization per race)
       ↓
XGBoost / PyTorch MLP training
       ↓
Backtesting with real odds (ROI simulation)
       ↓
Ensemble with Form/Track/Pace engines
       ↓
Production predictions via API
```
