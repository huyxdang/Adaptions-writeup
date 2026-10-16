# Results

## Reported evaluations

| Attempt | Base model | Method | Adaption platform quality score | On-dataset preference | Market Analysis preference | Public figure |
| --- | --- | --- | --- | --- | --- | --- |
| Attempt #1 | Llama 3.3 70B Instruct Reference | LoRA SFT | 5.0 to 9.4 | 84:16 | 77:23 | [Preference results](../assets/a1-winrates.png) |
| Attempt #2 | Llama 3.3 70B Instruct | LoRA SFT | Not reported for finalized dataset | 87:13 | 74:27 | [Preference results](../assets/a2-winrate.png) |

Each preference result is shown as **adapted:base**. The quality score describes the dataset, not model performance; Adaption does not publish its scoring rubric.

## Interpretation

### Attempt #1

The adapted model recorded an 84:16 in-distribution preference result and a 77:23 result on Adaption's broader Market Analysis category evaluation. The latter provides broader-category platform preference evidence, but independence from the local 73-row held-out split and complete split hygiene are not established in the public record. Neither result establishes accuracy, clean external transfer, or real-world investment performance.

### Attempt #2

The final adapted model recorded 87:13 on its dataset-specific preference evaluation and 74:27 on Adaption's separate Market Analysis evaluation. These are the platform-reported values, not normalized accuracy percentages. The final dataset contains 34,640 finance samples, expanded with 13,856 general-purpose examples into a 48,496-example pre-split mixture.

Attempt #2 broadened source and task coverage while retaining strong platform preference results. It is not proven superior overall to Attempt #1: the adapters were evaluated against their respective base models, not head-to-head on identical held-out prompts. The unpublished protocol and split-hygiene limitations still apply.

## Comparison limits

The two attempts are not a controlled leaderboard. Their data and training configurations differ, and neither evaluation directly compares the two adapters.

These metrics are platform-reported comparative preference rates. They are not investment return, alpha, price-target accuracy, trading performance, or a percentage of objectively correct answers.

This repository does not claim:

- independent human evaluation or statistical significance;
- complete reproduction of the reported runs from this repository alone;
- generalization outside the reported platform evaluations;
- replacement of analysts, primary-source review, or professional advice.

See [Experiment History](EXPERIMENT_HISTORY.md) and the [Figure Index](../results/FIGURE_INDEX.md).
