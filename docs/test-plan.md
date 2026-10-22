# Test and Evaluation Plan — draft

**No experimental metrics have been measured yet.**

## Model evaluation (Dulat)
- Baseline: a simple TF-IDF + Logistic Regression classifier, if data suitability permits.
- Compare against a second classical approach and/or multilingual transformer if feasible.
- Report precision, recall, F1, confusion matrix, class distribution, and test-set size.
- Maintain a held-out test set; prevent duplicated/near-duplicated messages crossing splits.
- Evaluate Russian and Kazakh subsets separately when sample counts permit meaningful conclusions.
- Record false positives and false negatives, domain drift and uncertainty.
- **Thresholds:** to be proposed and approved after data review.

## API tests (Nurbolat)
| ID | Test case | Expected result |
|---|---|---|
| API-01 | Non-empty valid input | Structured, schema-valid response |
| API-02 | Empty input | Validation failure with understandable error |
| API-03 | Excessively long input | Safe rejection using documented limit |
| API-04 | Model failure | Sanitized server error; no leak of text |
| API-05 | Sensitive-looking text | Raw input never appears in diagnostic logs |

## UI tests (Nurbolat)
| ID | Test case | Expected result |
|---|---|---|
| UI-01 | Enter text and tap Analyze | Loading state and eventual result/error |
| UI-02 | Empty text | Submission blocked or clear feedback |
| UI-03 | Network unavailable | Understandable message, user can retry |
| UI-04 | High-risk result | Visible caution and indicator(s) |
| UI-05 | Uncertain result | No misleading guarantee of safety |

## Performance and comparators
- Record end-to-end latency (median and p95) on specified device, server and network.
- Comparison: baseline model, not arbitrary unverified market claims.
- Store reproducible configuration and test commands once implementation exists.

## Acceptance
Requirements in `requirements.md` map to tests above and additional cases; test execution results: **pending implementation**.
