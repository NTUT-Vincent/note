# 台股 V2 Research Hypothesis Registry

- **reset date:** 2026-07-25
- 平日只能記錄 candidate issue，不得修改 champion 權重。
- 單一規則至少 20 個有效樣本才可考慮升級。
- challenger 至少 40 個 OOS 樣本且 walk-forward 優於 champion / baselines 才可 promotion。

## Candidate Issues

| ID | Date | Type | Evidence | Hypothesis | Samples | Status |
|---|---|---|---|---|---:|---|
| V2-R0 | 2026-07-24 | architecture | V1 方向、區間與相對預測皆未呈現穩定 edge | LLM 降為 event/research layer；固定 score + baseline + edge filter | 0 | experimental |
| V2-R1 | 2026-07-24 | data_coverage | 可重現個股歷史資料目前只完整覆蓋 9 檔 | 擴充候選池後再評估 rank IC / decile spread | 9 | experimental |
| V2-R2 | 2026-07-27 | exogenous_shock | 7/24 market forecast=`down`，7/27 實際收平；週末美伊暫停軍事行動、Brent 大跌 | 研究 weekend geopolitical gap 是否應獨立標記為 exogenous shock | 1 | experimental |
| V2-R3 | 2026-07-27 | data_coverage | 仍只有 9 檔可完整重算 alpha；breadth、融資與多數個股當日法人 flow 不完整 | 擴大 universe 與資料完整度前，不使用 rank IC / decile spread 宣稱 edge | 9 | experimental |
| V2-R4 | 2026-07-28 | regime_error | 7/27 `mixed/+0.45/up` 在隔日遭遇全球半導體 selloff，TAIEX -4.65%、SOX 前夜 -2.23%，亞洲晶片股同步重挫 | 檢驗 global-tech feature 是否需要用「收盤後至開盤前最新半導體訊號」建立獨立 overnight shock flag，而非提高既有權重 | 1 | experimental |
| V2-R5 | 2026-07-28 | event_error | 緯創 event_half_life 仍有效但 7/28 -3.95%，未達預測 lead 門檻；公司事件被 sector crash 壓過 | 檢驗高 impact company event 在 `panic` semiconductor regime 下是否應只支持 relative score、不支持 absolute direction | 1 | experimental |
| V2-R6 | 2026-07-28 | volatility_error | 市場實際 -4.65% 與緯創 -3.95% 皆超出 7/27 deterministic interval | 檢驗 regime transition 時 interval half-width 是否需由「前日波動 + overnight shock proxy」共同決定 | 2 | experimental |

## Daily Review Log

### 2026-07-27
- 首批成熟 formal stock forecast：2/3 direction、2/3 relative、3/3 interval。
- 但 `momentum_1d` 與 `momentum_20d` 同樣為 2/3，因此 **NO EVIDENCE OF EDGE**。
- 不修改任何 champion 權重。

### 2026-07-28
- V2 market：0/1 direction、0/1 interval。
- V2 formal stock：3231 direction / relative / interval 全數 miss。
- 累積 formal stock direction：2/4 = 50%；`momentum_1d` 同集合 3/4 = 75%。
- 市場累積方向 0/2；目前 V2 未優於 baseline。
- 新增 V2-R4～R6 只作 candidate issues，**不修改 champion config**。

## Weekly Review Log
尚未達到規則 20 samples / challenger 40 samples 的 promotion gate；不得進行權重 promotion。
