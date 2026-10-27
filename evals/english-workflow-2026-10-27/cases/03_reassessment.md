# Task 03

Reassess the two draft criticisms below against the supplied material. Return only the disposition of each criticism and any necessary revised author-facing comment, at most 150 English words total. Treat the material as a supplied excerpt, not a complete paper. Any material-screening notice belongs separately.

## Draft criticisms
1. “The effect of the positional input is not isolated because Table 3 enables both the positional input and a reranker.”
2. “The reported .7-point improvement is statistically significant and establishes a benefit on every target domain.”

## Supplied excerpt
Section 4: Table 3 compares the full system with the old baseline, changing the decoder and enabling the reranker together. This is a system comparison, not a component ablation.
Section 5: Table 4 specifically evaluates the positional input. Both rows use the same initialization, decoder, training schedule, five paired seeds, and disabled reranker. Only concatenation of the static positional input changes. Mean score is 72.4 without that input and 73.1 with it on the one evaluated target domain. The paired per-seed differences are .4, .6, .7, .8, and 1.0 points. We describe the finding as evidence of a modest gain on this domain, without making a significance claim or a guarantee for other domains.
Table 4 note: The main Table 3 variant has reranking enabled; the Table 4 ablation variants both disable it. The appendix explores three additional positional encodings, but the appendix was not supplied for this exercise.
