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

## Attempt #2 — Scale up

The final public finance dataset contains 34,640 samples, more than 50 times the original 589-row baseline.

- Hugging Face: [huyxdang/adaption-final-final](https://huggingface.co/datasets/huyxdang/adaption-final-final)
- Kaggle: [adaption-final-final](https://www.kaggle.com/datasets/huydang03/adaption-final-final)
- Composition: Dataset 2, the prompt-and-completion variant, combined with `market_analysis_XXL` from Attempt #1
- General-purpose replay: 13,856 synthetic examples added by AutoScientist
- Mixture before the training split: 48,496 examples

The earlier three-recipe candidate pool is not the released finance dataset. Generated variants should not be treated as independent source reports. No platform quality score for the finalized finance dataset is established by the current report.

## Use and licensing

The external host pages define each dataset's access and license terms. Public availability does not by itself provide the original source reports, complete source-rights record, frozen training runtime, or per-example evaluation outputs.

See [Reproduction](../docs/REPRODUCE.md) and [Public Release Policy](../docs/PUBLIC_RELEASE_POLICY.md).
