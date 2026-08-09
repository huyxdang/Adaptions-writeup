# Data Availability

No current AdaptMarket source documents, training rows, evaluation rows, prompts, or derived records are stored in this directory.

## Current experiment

| Item | Status |
| --- | --- |
| AdaptMarket training corpus | Restricted; not released |
| AdaptMarket training examples | Restricted; not released |
| AdaptMarket evaluation examples and outputs | Restricted; not released |
| Source-rights and provenance record | Not published |

The current full fine-tune cannot be reproduced from this repository.

## Public predecessor datasets

These externally hosted datasets document earlier experiments. They are not the current AdaptMarket corpus.

### Attempt #1 — Proof of Concept

- Hugging Face: [huyxdang/adaption-equity-analysis-small](https://huggingface.co/datasets/huyxdang/adaption-equity-analysis-small)
- Kaggle: [adaption-equity-analysis-small](https://www.kaggle.com/datasets/huydang03/adaption-equity-analysis-small)
- Published size: 27,862 instruction-tuning rows
- Rows reported as used for LoRA training: 27,405
- Published scope: English prompt/completion pairs derived from Vietnamese equity-research material
- Platform quality: 5.0 to 9.4, grade C to A

The report records a 739-row curated baseline split into 589 train, 77 validation, and 73 held-out rows. This repository does not assert that every baseline split is separately published.

### Attempt #2 — Scaling 50x

- Hugging Face: [huyxdang/adaption-market-analysis-final](https://huggingface.co/datasets/huyxdang/adaption-market-analysis-final)
- Kaggle: [adaption-market-analysis-final](https://www.kaggle.com/datasets/huydang03/adaption-market-analysis-final)
- Published size: 45,758 instruction-tuning rows
- Composition: 15,252 + 15,253 + 15,197 generated rows, plus 56 rows reported by the Combine output
- Platform quality: 8.0 to 9.4, grade B to A

The three generations cover the same underlying source items using different enhancement recipes. The public final dataset reports roughly 15,250 unique source items, not 45,758 independent source records. It also reports 56 null `enhanced_completion` values that must be filtered before training on that field.

## Use and licensing

The external host pages define each predecessor dataset's access and license terms. Public predecessor data does not establish the provenance, redistribution rights, or reproducibility of the restricted AdaptMarket corpus.

See [Reproduction and Data Availability](../docs/REPRODUCE.md) and [Public Release Policy](../docs/PUBLIC_RELEASE_POLICY.md).
