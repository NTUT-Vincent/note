# 台股 V2 Baseline Registry

V2 的成功標準不是單純提高命中率，而是穩定優於簡單 baseline。

## B1 — always_neutral

永遠預測震盪／相近。用來測試三分類問題中「不表態」本身是否已經很強。

## B2 — momentum_1d

延續前一交易日方向：昨日上漲則預測上漲、昨日下跌則預測下跌、其餘震盪。

## B3 — mean_reversion_1d

反轉前一交易日方向：昨日上漲則預測下跌、昨日下跌則預測上漲、其餘震盪。

## B4 — momentum_20d

依 20 日累積趨勢預測主要方向；個股版本需搭配 sector momentum 並獨立記錄相對加權表現。

## Evaluation Policy

- 所有 baseline 與 champion 使用同一驗證日期、同一方向門檻與同一標的集合。
- 不得在看到結果後替 baseline 選擇不同門檻。
- 每日保存 baseline prediction，避免事後重建造成 leakage。
- 至少比較方向命中率、balanced accuracy（樣本允許時）、relative-performance accuracy 與 forecast coverage。
- Champion 若沒有穩定超越 baseline，必須標示 `NO EVIDENCE OF EDGE`。
