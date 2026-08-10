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

## Attempt #2 — Scaling 50×

“Scaling 50×” is an editorial label. The second attempt expanded the source corpus to about 7,000 institutional reports spanning macro outlooks, sector studies, fund reviews, fixed-income commentary, and company research. Three Adaptive Data recipes produced 45,702 generated rows, and 56 rows reported by the Combine output brought the total to 45,758.

Its combined-dataset task taxonomy included these reported, rounded shares:

- insufficient evidence: 36.2%;
- market-state interpretation: 30.9%;
- actual-versus-forward-looking separation: 17.0%;
- driver transmission: 13.7%;
- comparative analysis: 1.5%;
- fund and benchmark analysis: 0.4%.

The recipes use shared source items, so the total represents roughly 15,250 unique generated items through multiple enhancement variants, not 45,758 independent source records.

| Parameter | Value |
| --- | --- |
| Base model | `togethercomputer/Llama-4-Scout-17B-16E-Instruct_bnb_4bit` |
| Method | LoRA supervised fine-tuning |
| Combined dataset | 45,758 rows |
| Rank / alpha / dropout | 32 / 64 / 0.05 |
| Target modules | `q_proj`, `k_proj`, `v_proj`, `o_proj` |
| Epochs / steps | 2 / 168 |
| Peak learning rate | `2e-5` |
| Run ID | `adaption_llama_4_scout_17b_16_final_cc7ddeac` |

Attempt #2 tests scale and breadth. It does not establish better generalization than Attempt #1 because it has no equivalent Market Analysis category evaluation.

## Future research

The next research direction is not another reported training run. It extends this evidence-grounded methodology toward point-in-time global evidence, dynamic financial relationships, cross-asset transmission, multi-horizon impact, adaptive retrieval, and market-feedback evaluation. See [Roadmap](ROADMAP.md).
