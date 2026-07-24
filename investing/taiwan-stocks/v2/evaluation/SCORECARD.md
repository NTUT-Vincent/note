# 台股 V2 Forecast Scorecard

- **V2 起始日：** 2026-07-25
- **第一個預計 inference 日：** 2026-07-27
- **目前 champion：** `v2.0.0-heuristic`
- **狀態：** 尚未累積 V2 out-of-sample 樣本。

## 原則

1. V2 只評估事前提交且通過 Edge Filter 的正式 Forecast；Watchlist / NO_FORECAST 不算命中或失準。
2. V1 SCORECARD 保留為歷史 baseline，不回頭重算來美化 V2。
3. 同時比較 `always_neutral`、`momentum_1d`、`mean_reversion_1d`、`momentum_20d`。
4. 沒有統計證據優於 baseline 時，結論必須為 `NO EVIDENCE OF EDGE`。
5. 原始 forecast JSON immutable，Evaluation 只能追加結果。

## 累積績效

| Model | Samples | 1D Direction | Relative Perf. | Interval Coverage | Notes |
|---|---:|---:|---:|---:|---|
| V2 champion | 0 | N/A | N/A | N/A | Waiting for OOS samples |
| always_neutral | 0 | N/A | N/A | N/A | baseline |
| momentum_1d | 0 | N/A | N/A | N/A | baseline |
| mean_reversion_1d | 0 | N/A | N/A | N/A | baseline |
| momentum_20d | 0 | N/A | N/A | N/A | baseline |

## Calibration

目前未啟用 probability calibration。正式輸出只能使用 `raw_score`，不得使用 `calibrated_probability`。

## Promotion Gate

Challenger 至少累積 40 個有效 out-of-sample 樣本並經 walk-forward 驗證，且相對 champion 與 baseline 有實質改善，才可升級。
