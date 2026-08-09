# Methods

## Task

AdaptMarket turns a dated company or market brief into concise analyst-style research. The target response links financial evidence to business performance, valuation, catalysts, and risks while separating:

- reported results from forecasts, guidance, and opinion;
- direct evidence from inference;
- material uncertainty from unsupported certainty.

The intended role is a first-pass research assistant. It is not a source of individualized investment recommendations or a substitute for primary-source review.

## Current AdaptMarket training run

| Parameter | Value |
| --- | --- |
| Track | Market Analysis & News — Equity Analysis |
| Base model | `mistralai/Mixtral-8x7B-Instruct-v0.1` |
| Training method | Supervised fine-tuning |
| Training type | Full fine-tune |
| Data format | Chat |
| Epochs | 1 |
| Batch size | Maximum available |
| Learning rate | `0.00001` |
| LoRA | Disabled |
| Scheduler | Cosine; minimum learning-rate ratio `0.1`; `0.5` cycles |
| Warmup ratio | `0.1` |
| Maximum gradient norm | `0.5` |
| Weight decay | `0` |
| Evaluations | 5 |
| Train on inputs | False |

The experiment changed the training method from LoRA to full fine-tuning. Its objective was to retain target-domain behavior while improving transfer to the broader Market Analysis evaluation.

## Predecessor methods

These configurations describe earlier public adapters, not the current AdaptMarket model.

| Stage | Base model | Type | Configuration |
| --- | --- | --- | --- |
| Attempt #1 | `meta-llama/Llama-3.3-70B-Instruct-Reference` | LoRA SFT | Rank 16, alpha 32, dropout 0.05, all-linear targets, 2 epochs, `1e-4` learning rate |
| Attempt #2 | `togethercomputer/Llama-4-Scout-17B-16E-Instruct_bnb_4bit` | LoRA SFT | Rank 32, alpha 64, dropout 0.05, attention projection targets, 2 epochs, 168 steps, `2e-5` peak learning rate |

Attempt #1 tested an evidence-grounded extraction and adaptation workflow. Attempt #2 broadened source and task coverage and combined three enhancement variants over the same source items. See [Experiment History](EXPERIMENT_HISTORY.md).

## Current corpus scope

The restricted AdaptMarket training material is designed to cover:

- company financial and operating performance;
- valuation assumptions and revisions;
- sector and industry developments;
- macroeconomic conditions;
- catalysts, risks, and outlooks.

The current corpus and derived examples are not distributed in this repository. Public predecessor datasets are indexed in [data/README.md](../data/README.md), but they must not be treated as the AdaptMarket corpus.

No claim is made that the current corpus is complete, representative of all markets, or suitable for public redistribution.

## Research direction

The long-term direction is thesis-conditioned event-impact analysis: evaluate a new event against the company's historical thesis, operating sensitivities, forecasts, valuation assumptions, catalysts, risks, peers, and sector context. See [ROADMAP.md](ROADMAP.md).
