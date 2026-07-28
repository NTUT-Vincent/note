# 台股 V2 Forecast Scorecard

- **V2 reset date:** 2026-07-25
- **champion:** `v2.0.0-heuristic`
- **config hash:** `13f40f7e725f24d8`

## 原則
1. 只評估事前提交且通過 Edge Filter 的正式 Forecast。
2. Watchlist / NO_FORECAST 不列入命中率。
3. 同時比較 fixed baselines。
4. forecast JSON immutable；結果只能另行追加。
5. 未有足夠 OOS 樣本前固定標示 `NO EVIDENCE OF EDGE`。

## 累積績效（截至 2026-07-28 收盤）

### V2 Champion

| Metric | Hits | Samples | Rate | Notes |
|---|---:|---:|---:|---|
| Market 1D direction | 0 | 2 | 0.0% | 7/27 flat、7/28 down；兩次 V2 市場方向皆 miss |
| Market interval coverage | 1 | 2 | 50.0% | 7/28 -4.65% 超出 -0.84%～+1.56% |
| Stock 1D direction | 2 | 4 | 50.0% | 首批 2/3；7/28 的 3231 miss |
| Stock relative performance | 2 | 4 | 50.0% | 3231 7/28 相對約 +0.70pct，未達 +0.8pct lead 門檻 |
| Stock interval coverage | 3 | 4 | 75.0% | 3231 -3.95% 超出 -1.10%～+2.90% |

### Baseline direction — same formal stock forecast sets

| Model | Hits | Samples | Accuracy |
|---|---:|---:|---:|
| V2 champion | 2 | 4 | 50.0% |
| always_neutral | 0 | 4 | 0.0% |
| momentum_1d | 3 | 4 | **75.0%** |
| mean_reversion_1d | 1 | 4 | 25.0% |
| momentum_20d | 2 | 4 | 50.0% |

### Market baseline direction

| Model | Hits | Samples | Accuracy |
|---|---:|---:|---:|
| V2 champion | 0 | 2 | 0.0% |
| always_neutral | 1 | 2 | 50.0% |
| momentum_1d | 0 | 2 | 0.0% |
| mean_reversion_1d | 0 | 2 | 0.0% |
| momentum_20d | 1 | 2 | 50.0% |

**Status: `NO EVIDENCE OF EDGE`.** 目前個股正式樣本只有 4 筆，而且 `momentum_1d` 暫時 75% 高於 V2 的 50%。市場方向 V2 目前 0/2。不得宣稱 alpha。

## 2026-07-24 → 2026-07-27 Evaluation
- Market: predicted `down`, actual `flat` (-0.05%); direction miss, interval hit.
- 3231 緯創: predicted `flat / lead`, actual -1.12% and about -1.07pct vs TAIEX; direction miss, relative miss, interval hit.
- 2303 聯電: predicted `down / lag`, actual -1.56% and about -1.52pct vs TAIEX; direction hit, relative hit, interval hit.
- 3481 群創: predicted `down / lag`, actual -4.34% and about -4.30pct vs TAIEX; direction hit, relative hit, interval hit.

## 2026-07-27 → 2026-07-28 Evaluation
- Market: predicted `up`, actual **down -4.65%**; direction miss and interval miss.
- 3231 緯創: predicted `up / lead`, actual **-3.95%**. Relative return versus TAIEX ≈ **+0.70pct**, classified `similar` under fixed ±0.8pct threshold; direction, relative and interval all miss.
- Same-set stock baseline: `momentum_1d` correctly predicted 3231 down; all other baseline directions for 3231 missed.
- Market `momentum_20d` correctly predicted down; V2 and the other three market baselines missed.

完整結果：`investing/taiwan-stocks/v2/evaluation/2026-07-28.json`。

## Open Forecasts
- `2026-07-28.json` → target 2026-07-29.
- Formal stock forecast count: 3 (`2884`, `2454`, `2303`).
- Market forecast: `down`, raw score `-0.90`, regime `panic`.

## Calibration
Probability calibration is disabled. Outputs use `raw_score`, not probability.

## Promotion Gate
- No model or rule changes allowed from this daily run.
- Minimum 20 effective samples before a candidate rule can be promoted.
- Minimum 40 OOS samples plus walk-forward superiority before a challenger can replace champion.
