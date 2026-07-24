# 台股 V2 Research Hypothesis Registry

- **建立日期：** 2026-07-25
- **用途：** 保存 candidate issues、研究假設與 weekly learning 結果。
- **重要：** 平日錯誤只記錄為 candidate issue，不得當天直接修改 champion 權重或新增 active rule。

## Candidate Issues

| ID | Date | Type | Evidence | Hypothesis | Samples | Status |
|---|---|---|---|---|---:|---|
| V2-INIT | 2026-07-25 | architecture | V1 個股方向、區間與相對預測尚無穩定優勢 | 將 LLM 降為 research/event layer，改用固定 feature score + baseline + edge filter | 0 | experimental |

## Promotion Policy

- 單一規則／假設未累積至少 20 個有效樣本，不得升級為 active。
- 模型 challenger 未累積至少 40 個有效樣本，不得取代 champion。
- 必須使用時間順序正確的 walk-forward / time-series validation。
- 只有 out-of-sample 指標改善才可 promotion；否則標記 `rejected` 或維持 `experimental`。
- 不得因為 1–3 個近期案例就改模型。

## Weekly Review Log

尚未進行第一次 V2 weekly review。
