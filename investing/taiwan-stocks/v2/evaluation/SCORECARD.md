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

## 累積績效

| Model | Matured Samples | 1D Direction | Relative Perf. | Interval Coverage | Status |
|---|---:|---:|---:|---:|---|
| V2 champion | 0 | N/A | N/A | N/A | NO EVIDENCE OF EDGE |
| always_neutral | 0 | N/A | N/A | N/A | baseline |
| momentum_1d | 0 | N/A | N/A | N/A | baseline |
| mean_reversion_1d | 0 | N/A | N/A | N/A | baseline |
| momentum_20d | 0 | N/A | N/A | N/A | baseline |

## Open Forecasts

- 2026-07-24 replay forecast targets the next Taiwan trading day (2026-07-27). It was actually executed/committed on 2026-07-25 before the target result, using a 2026-07-24 19:30 data cutoff.
- 2026-07-25 run = `NO_FORECAST`; no duplicate prediction was created for the same 7/27 target.

## Calibration
Probability calibration is disabled. Outputs use `raw_score`, not probability.
