# Experiment History

This record covers the two AutoScientist attempts documented by the public report.

The 0–10 data-quality values below are Adaption platform quality scores; Adaption does not publish their scoring rubric. The evaluation results are platform-reported pairwise preference rates shown as **adapted:base**: the share of comparisons in which a judge preferred the adapted model's response over the base model's response. Neither metric is an accuracy or investment-performance score.

## Attempt #1 — Proof of Concept

**Provided evidence that institutional equity-research reports can be converted into leakage-controlled training data for reconstructing analyst judgments from supplied evidence rather than copying conclusions from the prompt.**

### Data

The project began with roughly 1,500 Southeast Asian institutional sell-side reports. An answer-first extraction workflow identified analyst judgments, removed judgment leakage from the supplied evidence, ranked the remaining evidence, and derived only the analytical task supported by the source.

![Document-to-prompt extraction workflow](../assets/extraction-doc-to-prompt.png)

The curated corpus contained 739 rows:

| Split | Rows |
| --- | ---: |
| Train | 589 |
| Validation | 77 |
| Held out | 73 |

Adaptive Data expanded the 589-row training baseline to 27,862 rows, of which 27,405 were reported as used for training. The Adaption platform quality score increased from 5.0 to 9.4, moving from grade C to grade A.

![Attempt 1 quality result](../assets/a1-quality.png)

### Model

| Field | Value |
| --- | --- |
| Base model | `meta-llama/Llama-3.3-70B-Instruct-Reference` |
| Method | LoRA supervised fine-tuning |
| Rank / alpha / dropout | 16 / 32 / 0.05 |
| Target modules | All linear layers |
| Epochs / steps | 2 / 382 |
| Learning rate | `1e-4` |
| Loss | Completions only |
| Training experiment | `22ed78c2-6708-4e15-814f-b2bc73ca95af` |
| Fine-tune job | `140dbd16-fb1d-41da-ac02-b307e8d43024` |

### Results

| Evaluation | Adapted | Base |
| --- | ---: | ---: |
| On-dataset preference | **84%** | 16% |
| Market Analysis preference | **77%** | 23% |

![Attempt 1 preference results](../assets/a1-winrates.png)

The 84:16 result is an in-distribution diagnostic. Adaption, rather than the project team, constructed the broader Market Analysis category evaluation, so its 77:23 result provides broader-category evidence. Independence from the local 73-row held-out split and complete split hygiene are not established in the public record; neither result establishes accuracy or real-world performance.

### Public releases

- Dataset: [Hugging Face](https://huggingface.co/datasets/huyxdang/adaption-equity-analysis-small) · [Kaggle](https://www.kaggle.com/datasets/huydang03/adaption-equity-analysis-small)
- LoRA adapter: [Hugging Face](https://huggingface.co/huyxdang/adaption_vietnam_equity_research_note) · [Kaggle](https://www.kaggle.com/models/huydang03/adaption-vietnam-equity-research-note/PyTorch/lora)

## Attempt #2 — Scaling 50×

**Expanded source and task coverage from company-level equity research to macro, sector, fund, and fixed-income research.**

“Scaling 50×” is an editorial label. The measured change is from roughly 1,500 to about 7,000 source reports; three recipes produced 45,702 generated rows, and 56 rows in the Combine output brought the total to 45,758.

### Data

The source corpus expanded from roughly 1,500 to about 7,000 institutional reports. The combined-dataset taxonomy reported these rounded shares: insufficient evidence (36.2%), market-state interpretation (30.9%), actual-versus-forward-looking separation (17.0%), driver transmission (13.7%), comparative analysis (1.5%), and fund and benchmark analysis (0.4%).

Adaptive Data ran three recipes over the same source corpus, then combined their outputs:

| Generation | Rows | Recipe | Quality |
| --- | ---: | --- | --- |
| Dataset 1 | 15,252 | Completion rewritten | 7.0 to 9.2 |
| Dataset 2 | 15,253 | Prompt and completion with response constraints | 7.0 to 9.5 |
| Dataset 3 | 15,197 | Independent variant of the constrained recipe | 7.0 to 9.5 |
| Combined | **45,758** | 45,702 generated rows plus 56 | Adaption platform score: 8.0 to 9.4 |

The generations share the same underlying source items. The combined row count represents roughly 15,250 unique generated items through multiple enhancement variants, not 45,758 independent source records.

![Attempt 2 quality result](../assets/a2-adaptive-data.png)

### Model

| Field | Value |
| --- | --- |
| Base model | `togethercomputer/Llama-4-Scout-17B-16E-Instruct_bnb_4bit` |
| Method | LoRA supervised fine-tuning |
| Rank / alpha / dropout | 32 / 64 / 0.05 |
| Target modules | `q_proj`, `k_proj`, `v_proj`, `o_proj` |
| Epochs / steps | 2 / 168 |
| Peak learning rate | `2e-5` |
| Run ID | `adaption_llama_4_scout_17b_16_final_cc7ddeac` |

### Results

| Evaluation | Adapted | Base |
| --- | ---: | ---: |
| On-dataset preference | **80%** | 20% |
| Market Analysis preference | Not produced | Not produced |

![Attempt 2 preference result](../assets/a2-winrate.png)

Attempt #2 demonstrated scale and breadth while retaining a large preference margin on its own distribution. Without a category-level result, it did not establish broader transfer or better generalization than Attempt #1.

### Public releases

- Dataset: [Hugging Face](https://huggingface.co/datasets/huyxdang/adaption-market-analysis-final) · [Kaggle](https://www.kaggle.com/datasets/huydang03/adaption-market-analysis-final)
- LoRA adapter: [Hugging Face](https://huggingface.co/huyxdang/adaption-market-analysis-final-model) · [Kaggle](https://www.kaggle.com/models/huydang03/adaption-market-analysis-final-model/PyTorch/lora)

## Reading progress across attempts

| Question | Evidence |
| --- | --- |
| Can leakage-controlled financial evidence support analyst-style responses on a broader Adaption category evaluation? | Attempt #1 recorded a 77:23 Market Analysis preference result; clean external transfer is not established. |
| Can the same workflow scale to broader sources and tasks? | Attempt #2 reached 45,758 rows and an 80:20 on-dataset result. |

The scores must not be ranked as though they came from one controlled benchmark. The models, datasets, configurations, and evaluation scopes changed between attempts.

**Attempt #1 used company-level supplied-evidence tasks. Attempt #2 broadened the source coverage and financial task taxonomy. The next step is to test how information propagates through the global financial system.**

See [Future Improvement Roadmap](ROADMAP.md).
