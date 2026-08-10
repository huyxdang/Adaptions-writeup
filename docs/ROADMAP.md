# What's next: Dynamic global-market relationships

## Objective

The completed experiments teach models to reconstruct financial analysis from supplied evidence. The next research question is larger: can a system identify how new information propagates across companies, sectors, asset classes, and geographies while preserving exactly what was knowable at the time?

The immediate goal is not simply to add more documents or increase model parameters. It is to build a point-in-time dataset that makes dynamic market relationships explicit, then test whether those relationships are learned more effectively through model adaptation or retrieval adaptation.

## Proposed dataset

Each example would begin with an event and a decision timestamp. Its evidence set would contain only information published by that timestamp, preventing later reports, revised figures, subsequent prices, and hindsight conclusions from leaking backward.

The dataset would represent time-varying links among:

- companies, business segments, suppliers, customers, and competitors;
- sectors, commodities, interest rates, currencies, and credit exposures;
- funds, ownership relationships, and geographic exposures;
- macroeconomic releases, policy decisions, and market regimes.

Each training case would preserve source provenance, publication time, supporting passages, contradictions, relationship paths, analytical horizon, and the conclusion supported by the available evidence.

A representative reasoning path might be:

```text
Rate shock -> Bond yields -> Bank funding -> Mortgage rates
           -> Housing demand -> Construction -> Materials -> Company earnings
```

This structure would allow the same event to have different implications over immediate, near-term, medium-term, and structural horizons.

## Literature review: two research directions

### 1. Graph-aware model adaptation

[FinRipple: Aligning Large Language Models with Financial Market for Event Ripple Effect Awareness](https://arxiv.org/abs/2505.23826) by Yuanjian Xu and colleagues models financial events as shocks that propagate through a time-varying company network. It combines dynamic relationships with financial theory-guided reinforcement learning and evaluates whether the model can identify effects beyond the company directly named in an event.

This direction suggests adapting the model itself to learn transmission paths. For our project, the dynamic relationship dataset would supply the entities, temporal links, evidence, and downstream effects needed to train and test that behavior.

### 2. Point-in-time retrieval adaptation

[Point-in-Time Financial RAG with Frozen LLMs and Market-Feedback Adaptive Retrieval](https://arxiv.org/abs/2605.31201) by Zijie Zhao and Roy E. Welsch takes a different approach. It keeps the reader model frozen, retrieves only evidence available at the historical decision time, and updates an external source-memory system using matured residual-return feedback.

This direction suggests that better evidence selection may matter more than repeatedly fine-tuning the reader. For our project, the same dynamic relationship dataset could guide retrieval by event type, entity, market regime, relationship path, and analytical horizon.

## Proposed comparison

The two approaches should be evaluated against each other on the same point-in-time cases:

1. **Adapted model:** train the reader to reason directly over dynamic market relationships.
2. **Adaptive retrieval:** keep the reader fixed and learn which historical evidence and relationship paths to retrieve.
3. **Combined system:** adapt both the reader and retrieval layer, then test whether the added complexity produces a measurable gain.

Model size should be treated as a controlled variable rather than the definition of scale. If larger base models are tested, they should use the same data, retrieval conditions, prompts, and evaluation cases as smaller models.

## Evaluation

Evaluation should use chronological splits and include unseen markets, industries, source types, languages, regimes, and shocks. It should separately measure:

- identification of directly and indirectly exposed entities;
- correctness of the proposed transmission path;
- use of evidence available at the decision time;
- recognition of insufficient or contradictory evidence;
- performance across immediate and longer analytical horizons;
- calibration and uncertainty;
- generalization beyond the dataset's original geography and distribution.

Subsequent market behavior can provide noisy feedback about whether a relationship was economically relevant, but it should not be treated as an unquestionable answer key or as proof of investment performance.

## Release boundary

This roadmap describes future research, not a completed third attempt. Before making performance claims, the project would need a release-eligible point-in-time corpus, documented source rights, frozen evaluation definitions, reproducible baselines, and published error analysis.
