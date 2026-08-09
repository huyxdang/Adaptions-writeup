# Training a Finance Model with AutoScientist

![An iridescent liquid form transitioning from a precise pixel grid into computational particles](assets/adaptive-liquid-pixel.jpg)

> Three experiments in evidence-grounded equity and market research with Adaption Labs.

This repository is the standalone public report and documentation archive for two released LoRA experiments and the current AdaptMarket full-fine-tuning experiment. It covers source-data extraction, Adaptive Data, AutoScientist training, evaluation results, limitations, and artifact release status.

Live report: https://adaptions-writeup.vercel.app/

The current AdaptMarket corpus, prompts, weights, and per-example evaluation outputs remain restricted. Public predecessor datasets and adapters are linked separately below.

## Current result

| Evaluation | Base | AdaptMarket | Change |
| --- | ---: | ---: | ---: |
| On-dataset preference | 15% | **85%** | **+70 percentage points** |
| Market Analysis preference | 27% | **73%** | **+46 percentage points** |

These are platform-reported pairwise preference rates, not accuracy, investment-return, or trading-performance measures.

## Experiment timeline

| Stage | Base model | Method | Public data scale | Reported preference result | Status |
| --- | --- | --- | ---: | --- | --- |
| Attempt #1 — Proof of Concept | `meta-llama/Llama-3.3-70B-Instruct-Reference` | LoRA SFT | 27,862 adapted rows | 84–16 on-dataset; 77–23 Market Analysis | Dataset and adapter released |
| Attempt #2 — Scaling 50x | `togethercomputer/Llama-4-Scout-17B-16E-Instruct_bnb_4bit` | LoRA SFT | 45,758 combined rows | 80–20 on-dataset; no category result | Dataset and adapter released |
| Attempt #3 — AdaptMarket | `mistralai/Mixtral-8x7B-Instruct-v0.1` | Full-model SFT | Restricted | 85–15 on-dataset; 73–27 Market Analysis | Documentation released |

The experiments are not direct head-to-head comparisons. Their models, data, training methods, and evaluation scopes differ. See [Experiment History](docs/EXPERIMENT_HISTORY.md).

## Progress record

### Attempt #1 — quality and transfer

Adaptive Data expanded the 589-row training split to 27,862 rows; 27,405 rows were used for LoRA training. Platform quality moved from 5.0 to 9.4, and the adapted model recorded both a dataset-specific and broader Market Analysis preference result.

![Attempt 1 quality panel showing original text at 5.0 and adaptive text at 9.4](assets/a1-quality.png)

![Attempt 1 preference results showing 84 to 16 on-dataset and 77 to 23 on Market Analysis](assets/a1-winrates.png)

### Attempt #2 — data scaling

The source corpus expanded from roughly 1,500 to about 7,000 institutional reports. Three Adaptive Data generations over the same source corpus were combined into 45,758 rows. Quality moved from 8.0 to 9.4, and the adapted model recorded an 80-to-20 dataset-specific preference result.

![Attempt 2 quality panel showing a move from grade B to grade A](assets/a2-adaptive-data.png)

![Attempt 2 preference result showing 80 to 20 on the combined dataset](assets/a2-winrate.png)

### Attempt #3 — full fine-tuning

| Field | Value |
| --- | --- |
| Date | 30 July 2026 |
| Track | Market Analysis & News — Equity Analysis |
| Base model | `mistralai/Mixtral-8x7B-Instruct-v0.1` |
| Method | Full-model supervised fine-tuning through AutoScientist |
| Data format | Chat |
| Epochs | 1 |
| Learning rate | `0.00001` |
| LoRA | Disabled |
| Training experiment | `e7becda4-f659-4704-b2f8-67f76a029e52` |
| Fine-tune job | `5b1fe1bb-c695-4bfd-bb05-eb24335634e0` |

No cleared result image exists for Attempt #3. Its public evidence is the experiment record and platform-reported aggregate metrics in [Results](docs/RESULTS.md).

## What AdaptMarket does

Given a dated company or market brief, the model is intended to:

- separate reported facts from guidance, forecasts, and opinion;
- connect evidence to business performance and valuation;
- surface catalysts, risks, uncertainty, and missing evidence;
- produce a concise first-pass research view rather than generic sentiment or a buy/sell instruction.

[Methods](docs/METHODS.md) · [Results](docs/RESULTS.md) · [Model card](model_card/README.md) · [Roadmap](docs/ROADMAP.md)

## Public artifact index

### Attempt #3 — AdaptMarket

| Artifact | Status |
| --- | --- |
| Research record | This repository |
| Dataset | Restricted; not released |
| Model weights | Restricted; not released |
| Prompts and evaluation outputs | Restricted; not released |
| Interactive arena | Not released |

### Released predecessor experiments

| Stage | Dataset | Adapter |
| --- | --- | --- |
| Attempt #1 | [Hugging Face](https://huggingface.co/datasets/huyxdang/adaption-equity-analysis-small) · [Kaggle](https://www.kaggle.com/datasets/huydang03/adaption-equity-analysis-small) | [Hugging Face](https://huggingface.co/huyxdang/adaption_vietnam_equity_research_note) · [Kaggle](https://www.kaggle.com/models/huydang03/adaption-vietnam-equity-research-note/PyTorch/lora) |
| Attempt #2 | [Hugging Face](https://huggingface.co/datasets/huyxdang/adaption-market-analysis-final) · [Kaggle](https://www.kaggle.com/datasets/huydang03/adaption-market-analysis-final) | [Hugging Face](https://huggingface.co/huyxdang/adaption-market-analysis-final-model) · [Kaggle](https://www.kaggle.com/models/huydang03/adaption-market-analysis-final-model/PyTorch/lora) |

These predecessor releases are not the AdaptMarket dataset or model. Their host pages govern access and licensing.

## Repository layout

```text
.
├── assets/               # report figures, marks, and figure manifest
├── data/                 # data availability and predecessor dataset index
├── docs/                 # experiment history, methods, results, and policy
├── model_card/           # current model card and predecessor adapter index
├── results/              # aggregate result and figure records
├── index.html            # complete responsive report
├── PROGRESS.md           # implementation and verification log
└── README.md
```

## Open locally

The site has no build step or runtime dependencies. From the repository root, run:

```bash
python3 -m http.server 8787
```

Then visit `http://127.0.0.1:8787/`.

## Data availability

No current AdaptMarket training or evaluation data is included. The underlying material and derived records remain restricted. Any future release requires provenance, licensing, redistribution, privacy, security, leakage, and reproducibility review. See [Data Availability](data/README.md).

## Limitations

The reported preference rates do not establish real-world financial performance, independent human validation, statistical significance, or generalization beyond the reported platform evaluations.

This project is a research prototype. It is not financial, investment, tax, or legal advice and should not be used as the sole basis for investment decisions.
