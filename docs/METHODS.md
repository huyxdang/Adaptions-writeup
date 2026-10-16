# Methods

## Shared workflow

Early fixed templates asked every example for counterevidence and an invalidation condition even when the source contained neither. In a 50-row review, 45 rows failed that check. The final method therefore starts from a supported answer and derives only the task justified by the remaining evidence.

Both attempts use this answer-first extraction workflow to reduce conclusion leakage:

1. Identify the analyst judgment in the source report.
2. Remove that judgment and any direct answer leakage from the supplied evidence.
3. Rank the remaining evidence by relevance.
4. Derive only the analytical task supported by that evidence.
5. Use Adaptive Data to expand and restructure the resulting instruction-tuning examples.
6. Use AutoScientist to optimize and train a LoRA adapter and compare its responses with the corresponding base model.

The workflow is designed to create examples that require reconstruction of an analyst-style judgment from supplied evidence rather than copying a conclusion from the prompt.

![Document-to-prompt extraction workflow](../assets/extraction-doc-to-prompt.png)

## Attempt #1 — Proof of Concept

The first attempt focused on company-level equity research from roughly 1,500 Southeast Asian sell-side reports.

| Parameter | Value |
| --- | --- |
| Base model | `meta-llama/Llama-3.3-70B-Instruct-Reference` |
| Method | LoRA supervised fine-tuning |
| Adaptive Data output | 27,862 rows |
| Rows used for training | 27,405 |
| Rank / alpha / dropout | 16 / 32 / 0.05 |
| Target modules | All linear layers |
| Epochs / steps | 2 / 382 |
| Learning rate | `1e-4` |
| Loss | Completions only |
| Training experiment | `22ed78c2-6708-4e15-814f-b2bc73ca95af` |
| Fine-tune job | `140dbd16-fb1d-41da-ac02-b307e8d43024` |

## Attempt #2 — Scale up

The second attempt expanded the source corpus to about 7,000 institutional reports spanning macro outlooks, sector studies, fund reviews, fixed-income commentary, and company research. After testing three Adaptive Data recipes, the final run selected Dataset 2, the prompt-and-completion variant, and combined it with `market_analysis_XXL` from Attempt #1.

The final public finance dataset contains 34,640 samples, more than 50 times the original 589-row baseline. AutoScientist added 13,856 synthetic general-purpose examples to preserve broader capabilities, yielding a 48,496-example mixture before the training split. The development candidate pool must not be presented as the released dataset or as independent source records.

| Parameter | Value |
| --- | --- |
| Base model | `Llama-3.3-70B-Instruct` |
| Method | LoRA supervised fine-tuning |
| Finance dataset | 34,640 samples |
| Pre-split mixture | 48,496 examples |
| Rank | 16 |
| Epochs | 2 |
| Learning rate | `1e-4` |
| Run ID | `adaption_llama_3_3_70b_instru_final_final_8228cf21` |

Attempt #2 recorded 87:13 on-dataset and 74:27 Market Analysis preferences. These platform evaluations do not establish superiority over Attempt #1 without a head-to-head comparison on the same held-out prompts.

## Future research

The next research direction is not another reported training run. It extends this evidence-grounded methodology toward point-in-time global evidence, dynamic financial relationships, cross-asset transmission, multi-horizon impact, adaptive retrieval, and market-feedback evaluation. See [Roadmap](ROADMAP.md).
