# Results

## Current AdaptMarket experiment

### Experiment record

| Field | Value |
| --- | --- |
| Date | 30 July 2026 |
| Track | Market Analysis & News — Equity Analysis |
| Training experiment | `e7becda4-f659-4704-b2f8-67f76a029e52` |
| Fine-tune job | `5b1fe1bb-c695-4bfd-bb05-eb24335634e0` |
| Base model | `mistralai/Mixtral-8x7B-Instruct-v0.1` |
| Training method | Full-model supervised fine-tuning |
| Data format | Chat |

### Platform-reported evaluation

| Evaluation | Base | AdaptMarket | Absolute change |
| --- | ---: | ---: | ---: |
| On-dataset preference | 15% | **85%** | **+70 percentage points** |
| Market Analysis preference | 27% | **73%** | **+46 percentage points** |

The result supports the experiment's narrow hypothesis: full fine-tuning can improve this task-specific evaluation while also improving performance on the broader platform Market Analysis evaluation. It does not establish robustness across markets, time periods, source types, research tasks, or real-world investment decisions.

No cleared per-example output, evaluator record, or result image exists for the current experiment.

## Historical result record

| Stage | Base model | Method | On-dataset preference | Market Analysis preference | Public result artifact |
| --- | --- | --- | --- | --- | --- |
| Attempt #1 | Llama 3.3 70B Instruct Reference | LoRA SFT | 84–16 | 77–23 | [Figure](../assets/a1-winrates.png) |
| Attempt #2 | Llama 4 Scout 17B 16E Instruct 4-bit | LoRA SFT | 80–20 | Not produced | [Figure](../assets/a2-winrate.png) |
| Attempt #3 — AdaptMarket | Mixtral 8x7B Instruct v0.1 | Full-model SFT | 85–15 | 73–27 | Aggregate record only |

These results are not a leaderboard. The models, data, methods, and evaluation scopes differ. Attempt #1 provides a broader category result, Attempt #2 tests data and workflow scaling on its own distribution, and AdaptMarket changes both the base model and fine-tuning method.

See [Experiment History](EXPERIMENT_HISTORY.md) and the [Figure Index](../results/FIGURE_INDEX.md).

## Reporting limits

These metrics are platform-reported comparative preference rates. They are not investment return, alpha, price-target accuracy, trading performance, or a percentage of objectively correct answers.

This repository does not claim:

- an independent human evaluation or statistical significance test;
- public reproduction of the current experiment from restricted training material;
- generalization outside the reported platform evaluations;
- replacement of analysts, primary-source review, or professional advice.

## Future evidence

A complete public AdaptMarket reproduction package would require a release-eligible dataset, frozen evaluation definition, base and adapted outputs, evaluator configuration, error analysis, and permission to publish every artifact. Those materials will be added only after release review.
