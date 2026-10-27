# Evidence and verification limits

| Task | Supplied evidence | Finding and boundary |
|---|---|---|
| 01 | Sections 2–3: thresholds maximize F1 over the full test labels; the same test set supplies reported F1. | The stated procedure uses evaluation labels for threshold selection. The reported F1 cannot establish performance of a pipeline frozen before test evaluation. No execution or data audit was performed. |
| 01 | Section 3: matched configurations; same CPU; preprocessing and cache lookup included; latency 12.4, 8.2, 5.1 ms; 28 MB additional memory. | The supplied measurements support a controlled latency comparison and expose its memory cost. Hardware measurements were not independently reproduced. |
| 01 | Section 3 table and Section 4 conclusion. Quantized minus uncached F1 is −.001, −.002, −.003; seed standard deviations are .003–.005 and explicitly not subject confidence intervals. | The maximum observed decrement is .003. The stronger expected-unseen-subject bound is unsupported by these measurements and variability summaries. |
| 02 | Sections 1–2: arbitrary nonnegative raw weights; inference from nonnegativity to sum of weights ≤ 1. | Contradicted by the valid instance n = 2, weights (1,1), inputs (1,1), giving S = 2. |
| 02 | Section 3: normalized weights sum to one for a positive denominator; all-zero weights return zero. | The normalized bound is supported by the supplied algebra. It does not prove the explicitly retained raw-weight theorem. No novelty assessment or literature search was performed. |
| 03 | Section 5 and Table 4 note: only positional-input concatenation changes; both rerankers disabled; five paired seeds. | The positional effect is isolated in the supplied ablation. Table 3 and Table 4 use different configurations for different comparisons; this is not a contradiction. |
| 03 | Means 72.4 and 73.1; paired differences .4, .6, .7, .8, 1.0; explicit single-domain, nonsignificance wording. | The differences average .7, and all are positive. The excerpt supports a modest observed gain on one domain; it does not claim statistical significance or universal benefit. The missing appendix remains unverified, not absent. |
| 04 | Existing comments only; original paper not supplied. | Edited wording preserves the useful-gain assessment, unresolved threshold question, limited cross-hardware ranking, validity of measurements, and lack of need to rerun every baseline. No new paper assessment was performed. |

Output constraints: Task 01 uses the four requested fields and no numerical rating; Task 02 explicitly states that no numerical scale was supplied; Task 03 contains only dispositions and the necessary replacement comment; Task 04 contains exactly two numbered comments. Screening is separate from every author-facing result.
