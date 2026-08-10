# Dataset Availability

No raw datasets or source reports are stored in this repository. The two documented training datasets are publicly hosted on Hugging Face and Kaggle.

## Attempt #1 — Proof of Concept

- Hugging Face: [huyxdang/adaption-equity-analysis-small](https://huggingface.co/datasets/huyxdang/adaption-equity-analysis-small)
- Kaggle: [adaption-equity-analysis-small](https://www.kaggle.com/datasets/huydang03/adaption-equity-analysis-small)
- Published size: 27,862 instruction-tuning rows
- Rows reported as used for LoRA training: 27,405
- Published scope: English prompt/completion pairs derived from Vietnamese equity-research material
- Adaption platform quality score: 5.0 to 9.4, grade C to A

The report records a 739-row curated corpus split into 589 train, 77 validation, and 73 held-out rows. The 589-row train split is the training baseline expanded by Adaptive Data. This repository does not assert that every curated split is separately published. Independence between the platform evaluations and the local 73-row held-out split, as well as complete split hygiene, are not established in the public record. Adaption does not publish the quality-score rubric.

## Attempt #2 — Scaling 50×

“Scaling 50×” is an editorial label. The measured Attempt #2 output is 45,702 generated rows plus 56 rows reported by the Combine output, totaling 45,758.

- Hugging Face: [huyxdang/adaption-market-analysis-final](https://huggingface.co/datasets/huyxdang/adaption-market-analysis-final)
- Kaggle: [adaption-market-analysis-final](https://www.kaggle.com/datasets/huydang03/adaption-market-analysis-final)
- Published size: 45,758 instruction-tuning rows
- Composition: 15,252 + 15,253 + 15,197 = 45,702 generated rows, plus 56 rows reported by the Combine output
- Adaption platform quality score: 8.0 to 9.4, grade B to A

The three generations cover the same underlying source items using three enhancement recipes. The public final dataset reports roughly 15,250 unique generated items represented through enhancement variants, not 45,758 independent source records. Adaption does not publish the quality-score rubric.

## Use and licensing

The external host pages define each dataset's access and license terms. Public availability does not by itself provide the original source reports, complete source-rights record, frozen training runtime, or per-example evaluation outputs.

See [Reproduction](../docs/REPRODUCE.md) and [Public Release Policy](../docs/PUBLIC_RELEASE_POLICY.md).
