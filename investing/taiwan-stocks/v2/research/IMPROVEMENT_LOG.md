# 台股 V2 Research Hypothesis Registry

- **reset date:** 2026-07-25
- 平日只能記錄 candidate issue，不得修改 champion 權重。
- 單一規則至少 20 個有效樣本才可考慮升級。
- challenger 至少 40 個 OOS 樣本且 walk-forward 優於 champion / baselines 才可 promotion。

## Candidate Issues

| ID | Date | Type | Evidence | Hypothesis | Samples | Status |
|---|---|---|---|---|---:|---|
| V2-R0 | 2026-07-24 | architecture | V1 方向、區間與相對預測皆未呈現穩定 edge | LLM 降為 event/research layer；固定 score + baseline + edge filter | 0 | experimental |
| V2-R1 | 2026-07-24 | data_coverage | 本次可重現個股歷史資料只完整覆蓋 9 檔 | 擴充候選池後再評估 rank IC / decile spread | 9 | experimental |
| V2-R2 | 2026-07-27 | exogenous_shock | 7/24 market forecast=`down`，7/27 實際收平；週末美伊暫停軍事行動、Brent 7/27 盤前跌 8.8%，屬 forecast cutoff 後的新資訊 | 研究 weekend geopolitical gap 是否應獨立標記為不可歸咎於模型的 exogenous shock，而不是當天修改 market weights | 1 | experimental |
| V2-R3 | 2026-07-27 | data_coverage | 今日仍只有 9 檔可完整重算 alpha；breadth、完整融資與多數個股當日法人 flow 缺失 | 在擴大 universe 與資料完整度前，不使用 rank IC / decile spread 宣稱 cross-sectional edge | 9 | experimental |

## Daily Review Log

### 2026-07-27
- 首批成熟 formal stock forecast：2/3 direction、2/3 relative、3/3 interval。
- 但 `momentum_1d` 與 `momentum_20d` 同樣為 2/3，因此 **NO EVIDENCE OF EDGE**。
- 不修改任何 champion 權重。

## Weekly Review Log
尚未達到規則 20 samples / challenger 40 samples 的 promotion gate；不得進行權重 promotion。
