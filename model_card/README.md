# Released Adapter Index

This directory records the two publicly released LoRA adapters documented by the report.

| Attempt | Base model | Method | Public adapter | Evaluation scope |
| --- | --- | --- | --- | --- |
| Attempt #1 | `meta-llama/Llama-3.3-70B-Instruct-Reference` | LoRA SFT | [Hugging Face](https://huggingface.co/huyxdang/adaption_vietnam_equity_research_note) · [Kaggle](https://www.kaggle.com/models/huydang03/adaption-vietnam-equity-research-note/PyTorch/lora) | 84:16 in-distribution; 77:23 broader Market Analysis category |
| Attempt #2 | `togethercomputer/Llama-4-Scout-17B-16E-Instruct_bnb_4bit` | LoRA SFT | [Hugging Face](https://huggingface.co/huyxdang/adaption-market-analysis-final-model) · [Kaggle](https://www.kaggle.com/models/huydang03/adaption-market-analysis-final-model/PyTorch/lora) | 80:20 in-distribution; no category result |

Each preference result is shown as **adapted:base**. For Attempt #1, independence between the broader category evaluation and the local 73-row held-out split, as well as complete split hygiene, are not established in the public record.

## Attempt #1

| Field | Value |
| --- | --- |
| Rank / alpha / dropout | 16 / 32 / 0.05 |
| Target modules | All linear layers |
| Epochs | 2 |
| Learning rate | `1e-4` |
| Training experiment | `22ed78c2-6708-4e15-814f-b2bc73ca95af` |
| Fine-tune job | `140dbd16-fb1d-41da-ac02-b307e8d43024` |

## Attempt #2

| Field | Value |
| --- | --- |
| Rank / alpha / dropout | 32 / 64 / 0.05 |
| Target modules | `q_proj`, `k_proj`, `v_proj`, `o_proj` |
| Epochs / steps | 2 / 168 |
| Peak learning rate | `2e-5` |
| Run ID | `adaption_llama_4_scout_17b_16_final_cc7ddeac` |

## Use and limitations

The adapters are externally hosted, and their host pages define availability and licensing. Their outputs require primary-source verification and qualified human review. The reported evaluations do not establish real-world financial performance or generalization beyond their stated scope.

See [Experiment History](../docs/EXPERIMENT_HISTORY.md), [Methods](../docs/METHODS.md), and [Dataset Availability](../data/README.md).
