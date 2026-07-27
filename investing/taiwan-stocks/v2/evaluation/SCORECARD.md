# 台股 V2 Forecast Scorecard

- **V2 reset date:** 2026-07-25
- **first replay execution timestamp:** 2026-07-25T01:55:00+08:00
- **first replay data cutoff:** 2026-07-24T19:30:00+08:00
- **champion:** `v2.0.0-heuristic`
- **config hash:** `13f40f7e725f24d8`

## 原則
1. 只評估事前提交且通過 Edge Filter 的正式 Forecast。
2. Watchlist / NO_FORECAST 不列入命中率。
3. 同時比較 fixed baselines。
4. forecast JSON immutable；結果只能另行追加。
5. 未有足夠 OOS 樣本前固定標示 `NO EVIDENCE OF EDGE`。

## 累積績效（截至 2026-07-27 收盤）

### V2 Champion

| Metric | Hits | Samples | Rate | Notes |
|---|---:|---:|---:|---|
| Market 1D direction | 0 | 1 | 0.0% | 7/24 predicted down; 7/27 actual flat |
| Market interval coverage | 1 | 1 | 100.0% | actual -0.05% inside -2.78%～+1.50% |
| Stock 1D direction | 2 | 3 | 66.7% | 2303, 3481 hit; 3231 miss |
| Stock relative performance | 2 | 3 | 66.7% | 2303, 3481 hit; 3231 miss |
| Stock interval coverage | 3 | 3 | 100.0% | all three within deterministic intervals |

### Baseline direction — same 3-stock forecast set

| Model | Hits | Samples | Accuracy |
|---|---:|---:|---:|
| V2 champion | 2 | 3 | 66.7% |
| always_neutral | 0 | 3 | 0.0% |
| momentum_1d | 2 | 3 | 66.7% |
| mean_reversion_1d | 1 | 3 | 33.3% |
| momentum_20d | 2 | 3 | 66.7% |

**Status: `NO EVIDENCE OF EDGE`.** V2 只與最佳簡單 baseline 打平，且樣本僅 3 檔；不能宣稱 alpha。

## 2026-07-24 → 2026-07-27 Evaluation

- Market: predicted `down`, actual `flat` (-0.05%); direction miss, interval hit.
- 3231 緯創: predicted `flat / lead`, actual -1.12% and about -1.07pct vs TAIEX; direction miss, relative miss, interval hit.
- 2303 聯電: predicted `down / lag`, actual -1.56% and about -1.52pct vs TAIEX; direction hit, relative hit, interval hit.
- 3481 群創: predicted `down / lag`, actual -4.34% and about -4.30pct vs TAIEX; direction hit, relative hit, interval hit.

完整結果：`investing/taiwan-stocks/v2/evaluation/2026-07-27.json`。

## Open Forecasts

- `2026-07-27.json` → target 2026-07-28.
- Formal stock forecast count: 1 (`3231`).
- Market forecast: `up`, raw score `+0.45`.

## Calibration
Probability calibration is disabled. Outputs use `raw_score`, not probability.

## Promotion Gate
- No model or rule changes allowed from this daily run.
- Minimum 20 effective samples before a candidate rule can be promoted.
- Minimum 40 OOS samples plus walk-forward superiority before a challenger can replace champion.
