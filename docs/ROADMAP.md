# Future Improvement — From Financial Research Model to Global Market-System Intelligence

## Foundation

The completed work consists of two attempts:

- **Attempt #1 — Proof of Concept:** converted institutional equity-research reports into leakage-controlled training data and trained a Llama 3.3 70B LoRA adapter for reconstructing analyst judgments from supplied evidence.
- **Attempt #2 — Scaling 50×:** expanded source coverage to about 7,000 macro, sector, fund, fixed-income, and company reports. Three recipes produced 45,702 generated rows plus 56 rows in the Combine output, totaling 45,758; shared-source variants represent roughly 15,250 unique generated items. A Llama 4 Scout 17B LoRA adapter was trained on the combined dataset.

“Scaling 50×” is an editorial label; the exact report and row counts above are the authoritative scale measurements.

The completed work uses institutional research first for company-level supplied-evidence tasks, then for broader source coverage and a wider financial task taxonomy.

The next step is to scale both the **geographic universe** and the **structure of the reasoning problem**.

Instead of asking only:

> **What does this evidence imply for this company?**

we want the system to eventually answer:

> **What changed, which parts of the global financial system are exposed, through which transmission channels, over what horizon, and what evidence actually supports that conclusion?**

## Global financial evidence

A global version could combine equities, sovereign and corporate credit, rates, FX, commodities, real estate, central-bank research, regulatory filings, earnings calls, institutional research, and macroeconomic releases across major markets.

The objective is not simply to add more documents. Evidence must remain attributable, time-bounded, and suitable for testing transmission hypotheses across entities, markets, and asset classes.

## Point-in-time data discipline

Every training, retrieval, and evaluation case should preserve exactly what information was available at the decision timestamp. Later reports, revised data, subsequent market moves, and hindsight conclusions must not leak backward.

A point-in-time evidence record should preserve:

- source and publication timestamp;
- claim lineage and supporting passages;
- contradictions and revisions;
- market context available before the event;
- the exact evidence set used for each conclusion.

## Dynamic market relationships

Suppliers, customers, competitors, ownership, funds, industries, commodities, leadership, patents, and geographic exposures change over time. These relationships should be represented as time-varying links rather than static metadata or independent company observations.

A dynamic knowledge network could connect:

```text
Company → Business segment → Product → Commodity → Supplier → Customer
        → Competitor → Fund → Credit exposure → Geography → Macro factor
```

## Cross-sector and cross-asset transmission

The system should reason through first- and higher-order effects instead of stopping at the directly mentioned asset.

```text
Rate shock → Bond yields → Bank funding → Mortgage rates → Housing demand
           → Construction → Materials → Company earnings
```

Transmission analysis should cover equities, rates, FX, commodities, sovereign and corporate credit, real estate, and related sectors while accounting for contracts, inventory, hedging, pricing power, and pass-through capacity.

## Multi-horizon impact

The same event can have different signs at different horizons. Future analysis should distinguish:

- immediate market reaction;
- near-term operating or liquidity impact;
- medium-term earnings, thesis, and valuation transmission;
- longer-term structural change.

## Market-feedback evaluation

Model hypotheses could be compared with subsequently realized market behavior—not as unquestionable labels, but as noisy feedback about whether the model identified economically relevant relationships.

Evaluation should separate broad market, sector, factor, and company-specific movement where possible. It should test whether the evidence and transmission hypothesis were useful, not treat realized returns as a perfect answer key or present the system as an investment-return engine.

## Adaptive retrieval

Retrieval should learn which evidence sources are useful for different event types, entities, market regimes, and horizons while keeping historical evidence strictly point-in-time.

A future retrieval policy could adapt using:

- entity and relationship relevance;
- publication time and evidence freshness;
- market regime and event type;
- uncertainty and conflicting evidence;
- analytical horizon;
- subsequent feedback about source usefulness.

## Global transfer tests

Future evaluation should test whether financial reasoning learned from one geography or regime generalizes to unseen markets, industries, asset classes, languages, source types, and shocks instead of only testing interpolation within the original corpus.

## Research directions

Two complementary research directions provide useful blueprints. They are references for future design, not implemented components of this report.

### [FinRipple](https://arxiv.org/abs/2505.23826)

FinRipple argues that financial events should be modeled as shocks propagating through a dynamic network rather than as isolated company sentiment. Its framework constructs time-varying company relationships—including supply chains, fund holdings, leadership links, and patent relationships—and aligns predicted ripple effects with realized asset-pricing residuals.

That is close to the structural direction we want:

> **Event → Direct exposure → Related entities → Ripple effects → Market response**

### Point-in-Time Financial RAG with Market-Feedback Adaptive Retrieval

This complementary direction freezes the reader, retrieves only evidence available at the historical decision time, supplies pre-event market context, predicts residual impact over multiple horizons, and lets subsequently realized returns update an external source-memory system rather than continually fine-tuning the reader on noisy returns.

## Longer-term architecture

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

## Evaluation and release work

Before claiming that this future system exists or works:

1. define a point-in-time, release-eligible evidence corpus and source-rights record;
2. implement dynamic relationship and provenance tracking;
3. freeze evaluation definitions, horizons, baselines, and market-adjustment methods;
4. publish error analysis, uncertainty, and conflicting-evidence behavior;
5. run transfer tests across geographies, regimes, sectors, asset classes, and source types;
6. evaluate it as a research workflow rather than an autonomous investment engine.

## Long-term objective

The ambition is not simply to train on more financial documents.

**Attempt #1 used company-level supplied-evidence tasks. Attempt #2 broadened the source coverage and financial task taxonomy. The next step is to test how information propagates through the global financial system.**

Everything after Attempt #2 in this document is a future research direction, not a completed experiment, model, or evaluation result.
