# Training a Finance Model with AutoScientist

![An iridescent liquid form transitioning from a precise pixel grid into computational particles](assets/adaptive-liquid-pixel.jpg)

> Two attempts in evidence-grounded equity and market research, followed by a roadmap toward global market-system intelligence.

This repository is the standalone public report and documentation archive for two AutoScientist experiments with Adaption Labs. It covers leakage-controlled source-data extraction, Adaptive Data, LoRA training, evaluation results, limitations, released artifacts, and future research directions.

Keith Vo contributed the equity-research workflow and domain framing; Huy X. Dang contributed the data and model-system work. Adaptive Data expanded and restructured the training data, while AutoScientist optimized, trained, and evaluated the LoRA adapters.

Live report: https://adaptions-writeup.vercel.app/

## Attempt #1 — Proof of Concept

**Provided evidence that institutional equity-research reports can be converted into leakage-controlled training data for reconstructing analyst judgments from supplied evidence rather than copying conclusions from the prompt.**

Starting from roughly 1,500 Southeast Asian sell-side reports, we curated 739 rows: 589 train, 77 validation, and 73 held out. Adaptive Data expanded the 589-row training baseline to 27,862 rows, of which 27,405 were reportedly used for training, and raised the Adaption platform quality score from 5.0 to 9.4. AutoScientist trained a Llama 3.3 70B LoRA adapter; the adapted model was preferred 84:16 in-distribution and 77:23 on Adaption's broader Market Analysis category evaluation.

The 77:23 figure is broader-category platform preference evidence. Independence from the local 73-row held-out split and complete split hygiene are not established in the public record.

![Attempt 1 quality panel showing original text at 5.0 and adaptive text at 9.4](assets/a1-quality.png)

![Attempt 1 preference results showing 84 to 16 on-dataset and 77 to 23 on Market Analysis](assets/a1-winrates.png)

## Attempt #2 — Scaling 50×

“Scaling 50×” is the chosen editorial label. The measured scale is roughly 1,500 to about 7,000 source reports and, for Attempt #2, 45,702 generated rows plus 56 rows in the Combine output, totaling 45,758.

**Expanded the source and task coverage from company-level equity research to macro, sector, fund, and fixed-income research.**

The broader taxonomy covers insufficient-evidence decisions, market-state interpretation, actual-versus-forward-looking separation, driver transmission, comparative analysis, and fund-and-benchmark analysis. Three Adaptive Data recipes over shared source items produced the 45,702 generated rows; the 45,758-row total represents roughly 15,250 unique generated items through multiple enhancement variants, not independent source records. The Adaption platform quality score increased from 8.0 to 9.4, and the resulting Llama 4 Scout 17B adaptation recorded an 80:20 in-distribution preference result. Attempt #2 therefore demonstrates **scale and breadth**, not better generalization than Attempt #1.

![Attempt 2 quality panel showing a move from grade B to grade A](assets/a2-adaptive-data.png)

![Attempt 2 preference result showing 80 to 20 on the combined dataset](assets/a2-winrate.png)

The attempts are not a controlled head-to-head benchmark. Their models, data, methods, and evaluation scopes differ. Attempt #1 includes a broader Market Analysis category result; Attempt #2 does not.

See [Experiment History](docs/EXPERIMENT_HISTORY.md), [Methods](docs/METHODS.md), and [Results](docs/RESULTS.md).

## Future Improvement — From Financial Research Model to Global Market-System Intelligence

The completed experiments use institutional research first for company-level supplied-evidence tasks, then for broader source coverage and a wider financial task taxonomy.

The next step is to scale both the **geographic universe** and the **structure of the reasoning problem**.

Instead of asking only:

> **What does this evidence imply for this company?**

we want the system to eventually answer:

> **What changed, which parts of the global financial system are exposed, through which transmission channels, over what horizon, and what evidence actually supports that conclusion?**

A global version could combine:

- **Global financial evidence:** equities, sovereign and corporate credit, rates, FX, commodities, real estate, central-bank research, regulatory filings, earnings calls, institutional research, and macroeconomic releases across major markets.
- **Point-in-time data discipline:** every training and evaluation case would preserve exactly what information was available at the decision timestamp, preventing future information or later analyst conclusions from leaking backward.
- **Dynamic market relationships:** represent suppliers, customers, competitors, ownership, funds, industries, commodities, and geographic exposures as changing relationships rather than assuming that companies are independent observations.
- **Cross-sector and cross-asset transmission:** reason through chains such as `rate shock → bond yields → bank funding → mortgage rates → housing demand → construction → materials → company earnings`, rather than stopping at the directly mentioned asset.
- **Multi-horizon impact:** distinguish the immediate market reaction from medium-term earnings transmission and longer-term structural impact; the same event may have different signs at different horizons.
- **Market-feedback evaluation:** compare model hypotheses with subsequently realized market behavior—not as unquestionable labels, but as noisy feedback about whether the model identified economically relevant relationships.
- **Adaptive retrieval:** continuously learn which evidence sources are useful for different event types, market regimes, and horizons while keeping historical evidence strictly point-in-time.
- **Global transfer tests:** evaluate whether financial reasoning learned from one geography or regime generalizes to unseen markets, industries, and shocks instead of only testing interpolation within the original corpus.

Two research directions provide useful blueprints for this next stage.

**[FinRipple](https://arxiv.org/abs/2505.23826)** argues that financial events should be modeled as shocks propagating through a dynamic network rather than as isolated company sentiment. Its framework constructs time-varying company relationships—including supply chains, fund holdings, leadership links, and patent relationships—and then aligns predicted ripple effects with realized asset-pricing residuals.

That is close to the structural direction we want:

> **Event → Direct exposure → Related entities → Ripple effects → Market response**

A second complementary direction is **Point-in-Time Financial RAG with Market-Feedback Adaptive Retrieval**. Instead of continually fine-tuning the reader on noisy realized returns, it freezes the LLM, retrieves only evidence available at the historical decision time, provides pre-event market context, predicts residual impact over multiple horizons, and lets subsequently realized returns update an external source-memory system.

This suggests a longer-term architecture for our work:

```text
Institutional Research Model
→ understands how professional analysts reason

+ Global Point-in-Time Evidence
→ knows what the market could actually have known at that moment

+ Dynamic Financial Relationships
→ knows which companies, sectors, and assets are connected

+ Cross-Asset Transmission Reasoning
→ understands how a shock can propagate through those connections

+ Market Feedback
→ learns which evidence and transmission hypotheses historically proved useful
```

The ambition is therefore not simply to train on more financial documents.

**Attempt #1 used company-level supplied-evidence tasks. Attempt #2 broadened the source coverage and financial task taxonomy. The next step is to test how information propagates through the global financial system.**

This section describes future research, not a completed model or evaluated experiment. See the full [Roadmap](docs/ROADMAP.md).

## Public artifacts

| Attempt | Dataset | LoRA adapter | Reported preference (adapted:base) |
| --- | --- | --- | --- |
| Attempt #1 | [Hugging Face](https://huggingface.co/datasets/huyxdang/adaption-equity-analysis-small) · [Kaggle](https://www.kaggle.com/datasets/huydang03/adaption-equity-analysis-small) | [Hugging Face](https://huggingface.co/huyxdang/adaption_vietnam_equity_research_note) · [Kaggle](https://www.kaggle.com/models/huydang03/adaption-vietnam-equity-research-note/PyTorch/lora) | 84:16 on-dataset; 77:23 Market Analysis |
| Attempt #2 | [Hugging Face](https://huggingface.co/datasets/huyxdang/adaption-market-analysis-final) · [Kaggle](https://www.kaggle.com/datasets/huydang03/adaption-market-analysis-final) | [Hugging Face](https://huggingface.co/huyxdang/adaption-market-analysis-final-model) · [Kaggle](https://www.kaggle.com/models/huydang03/adaption-market-analysis-final-model/PyTorch/lora) | 80:20 on-dataset; no category result |

The host pages govern artifact access and licensing.

## Repository layout

```text
.
├── assets/               # report figures and platform marks
├── data/                 # public dataset index and known caveats
├── docs/                 # history, methods, results, roadmap, and policy
├── model_card/           # released adapter index
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

## Availability and limitations

The externally hosted datasets and LoRA adapters are linked above. Raw source reports, the complete AutoScientist runtime, frozen evaluator configuration, and per-example evaluation outputs are not committed here.

The quality values are Adaption platform dataset-quality scores, not model evaluations, and Adaption does not publish the scoring rubric. The reported preference rates are platform-reported comparative metrics. Evaluator identity, comparison counts, exact prompts, response-order randomization, tie handling, matched decoding settings, and mapping to the local 73-row held-out split are not publicly available.

These metrics do not establish real-world financial performance, independent human validation, statistical significance, or generalization beyond the reported evaluations.

This project is for research and educational purposes. It is not financial, investment, tax, or legal advice and should not be used as the sole basis for investment decisions.
