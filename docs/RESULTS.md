# Results

## Reported evaluations

| Attempt | Base model | Method | Adaption platform quality score | On-dataset preference | Market Analysis preference | Public figure |
| --- | --- | --- | --- | --- | --- | --- |
| Attempt #1 | Llama 3.3 70B Instruct Reference | LoRA SFT | 5.0 to 9.4 | 84:16 | 77:23 | [Preference results](../assets/a1-winrates.png) |
| Attempt #2 | Llama 4 Scout 17B 16E Instruct 4-bit | LoRA SFT | 8.0 to 9.4 | 80:20 | Not produced | [Preference result](../assets/a2-winrate.png) |

Each preference result is shown as **adapted:base**. The quality score describes the dataset, not model performance; Adaption does not publish its scoring rubric.

## Interpretation

### Attempt #1

The adapted model recorded an 84:16 in-distribution preference result and a 77:23 result on Adaption's broader Market Analysis category evaluation. The latter provides broader-category platform preference evidence, but independence from the local 73-row held-out split and complete split hygiene are not established in the public record. Neither result establishes accuracy, clean external transfer, or real-world investment performance.

### Attempt #2

The adapted model won 80:20 on its dataset-specific preference evaluation. This demonstrates that the workflow scaled to broader source coverage, 45,758 rows, and a wider task taxonomy while retaining a large preference margin on its own distribution.

Attempt #2 has no category-level Market Analysis result. It therefore demonstrates **scale and breadth**, not better generalization than Attempt #1.

## Comparison limits

The two attempts are not a controlled leaderboard. Their base models, data, training configurations, and evaluation scopes differ.

These metrics are platform-reported comparative preference rates. They are not investment return, alpha, price-target accuracy, trading performance, or a percentage of objectively correct answers.

This repository does not claim:

- independent human evaluation or statistical significance;
- complete reproduction of the reported runs from this repository alone;
- generalization outside the reported platform evaluations;
- replacement of analysts, primary-source review, or professional advice.

See [Experiment History](EXPERIMENT_HISTORY.md) and the [Figure Index](../results/FIGURE_INDEX.md).
