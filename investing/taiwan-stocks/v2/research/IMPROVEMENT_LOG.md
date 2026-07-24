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

## Weekly Review Log
尚未進行 weekly learning；兩輪 replay 不得用來調權重。
