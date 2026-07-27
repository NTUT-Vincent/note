# 台股 V2 Baselines

V2 必須和固定 baseline 同場比較，不能只看自身命中率。

## B1 always_neutral
永遠預測震盪。

## B2 momentum_1d
依前一交易日方向延續。

## B3 mean_reversion_1d
依前一交易日方向反轉。

## B4 momentum_20d
依約 20 個交易日累積方向判斷。

## 驗證規則
- 市場：日報酬 > +0.4% = up；< -0.4% = down；其餘 flat。
- 個股：日報酬 > +0.8% = up；< -0.8% = down；其餘 flat。
- 所有 baseline 與 champion 使用相同 target date 與相同標的集合。
- baseline prediction 必須事前保存，禁止看到結果後重建。
- V2 未穩定勝過 baseline 前，結論固定為 `NO EVIDENCE OF EDGE`。

## 2026-07-24 → 2026-07-27 首批成熟結果

### Market
實際 TAIEX = `flat`（-0.05%）。

| Model | Prediction | Result |
|---|---|---|
| V2 champion | down | miss |
| always_neutral | flat | hit |
| momentum_1d | down | miss |
| mean_reversion_1d | up | miss |
| momentum_20d | down | miss |

### Stocks — same formal 3-stock set
實際方向：3231=`down`、2303=`down`、3481=`down`。

| Model | Hits | Samples | Accuracy |
|---|---:|---:|---:|
| V2 champion | 2 | 3 | 66.7% |
| always_neutral | 0 | 3 | 0.0% |
| momentum_1d | 2 | 3 | 66.7% |
| mean_reversion_1d | 1 | 3 | 33.3% |
| momentum_20d | 2 | 3 | 66.7% |

首批結果只顯示 V2 與最佳 baseline 打平，沒有 edge 證據。
