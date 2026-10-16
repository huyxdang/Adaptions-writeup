# Released Adapter Index

This directory records the two publicly released LoRA adapters documented by the report.

| Attempt | Base model | Method | Public adapter | Evaluation scope |
| --- | --- | --- | --- | --- |
| Attempt #1 | `meta-llama/Llama-3.3-70B-Instruct-Reference` | LoRA SFT | [Hugging Face](https://huggingface.co/huyxdang/adaption_vietnam_equity_research_note) · [Kaggle](https://www.kaggle.com/models/huydang03/adaption-vietnam-equity-research-note/PyTorch/lora) | 84:16 in-distribution; 77:23 broader Market Analysis category |
| Attempt #2 | `Llama-3.3-70B-Instruct` | LoRA SFT | [Hugging Face](https://huggingface.co/huyxdang/adaption_final_final) | 87:13 in-distribution; 74:27 broader Market Analysis category |

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
| Rank | 16 |
| Epochs | 2 |
| Learning rate | `1e-4` |
| Run ID | `adaption_llama_3_3_70b_instru_final_final_8228cf21` |

## Use and limitations

The adapters are externally hosted, and their host pages define availability and licensing. Their outputs require primary-source verification and qualified human review. The reported evaluations do not establish real-world financial performance or generalization beyond their stated scope.

See [Experiment History](../docs/EXPERIMENT_HISTORY.md), [Methods](../docs/METHODS.md), and [Dataset Availability](../data/README.md).
