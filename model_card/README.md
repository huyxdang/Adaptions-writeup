# AdaptMarket Model Card

## Model details

| Field | Value |
| --- | --- |
| Name | AdaptMarket |
| Base model | `mistralai/Mixtral-8x7B-Instruct-v0.1` |
| Task | Evidence-grounded equity and market analysis from dated briefs |
| Training method | Full-model supervised fine-tuning through AutoScientist |
| Data format | Chat |
| Epochs | 1 |
| Learning rate | `0.00001` |
| LoRA | Disabled |
| Training experiment | `e7becda4-f659-4704-b2f8-67f76a029e52` |
| Fine-tune job | `5b1fe1bb-c695-4bfd-bb05-eb24335634e0` |
| Release status | Documentation only; weights not released |

## Intended use

AdaptMarket is intended as a first-pass research assistant that:

- separates reported observations from guidance, forecasts, and opinion;
- links supplied evidence to operating performance, valuation, catalysts, and risks;
- preserves counterevidence and identifies insufficient evidence;
- produces concise analyst-style synthesis for human review.

It is not intended to provide individualized advice, execute trades, replace primary-source review, or make autonomous investment decisions.

## Evaluation

| Evaluation | Base | AdaptMarket |
| --- | ---: | ---: |
| On-dataset preference | 15% | **85%** |
| Market Analysis preference | 27% | **73%** |

These are platform-reported pairwise preference rates, not accuracy, financial return, or independent human-validation measures. Per-example outputs and evaluator records are not published.

## Data

The current training and evaluation material is restricted and not distributed. The released predecessor datasets in [data/README.md](../data/README.md) do not reproduce this model.

## Limitations

- Generalization beyond the reported evaluations is unverified.
- Results do not establish robustness across markets, time periods, source types, or real-world decisions.
- The model may inherit factual, reasoning, and safety limitations from its base model and training material.
- Outputs require primary-source verification and qualified human review.

## Availability

No AdaptMarket weights, merged model, adapter, inference endpoint, or access credential is published here.

## Public predecessor adapters

These are historical LoRA releases, not AdaptMarket weights.

| Stage | Base model | Adapter | Evaluation scope |
| --- | --- | --- | --- |
| Attempt #1 | `meta-llama/Llama-3.3-70B-Instruct-Reference` | [Hugging Face](https://huggingface.co/huyxdang/adaption_vietnam_equity_research_note) · [Kaggle](https://www.kaggle.com/models/huydang03/adaption-vietnam-equity-research-note/PyTorch/lora) | 84–16 on-dataset; 77–23 Market Analysis |
| Attempt #2 | `togethercomputer/Llama-4-Scout-17B-16E-Instruct_bnb_4bit` | [Hugging Face](https://huggingface.co/huyxdang/adaption-market-analysis-final-model) · [Kaggle](https://www.kaggle.com/models/huydang03/adaption-market-analysis-final-model/PyTorch/lora) | 80–20 on-dataset; no category result |

See [Experiment History](../docs/EXPERIMENT_HISTORY.md) for method and data context.
