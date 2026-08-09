# Roadmap

## Delivered foundation

The public record now covers three completed training experiments:

- Attempt #1 established the answer-first extraction workflow, expanded 589 training rows through Adaptive Data, and recorded both on-dataset and broader Market Analysis preference results.
- Attempt #2 scaled the source corpus and combined three enhancement variants into 45,758 rows, then trained and released a Llama 4 Scout LoRA adapter.
- AdaptMarket moved to full-model supervised fine-tuning of Mixtral 8x7B and recorded 85-to-15 on-dataset and 73-to-27 Market Analysis preference results.

The predecessor datasets and adapters are public. The current AdaptMarket corpus and model remain restricted pending release review. See [Experiment History](EXPERIMENT_HISTORY.md).

## 1. Expand the market-research corpus

Extend coverage across macroeconomics, monetary policy, industry supply and demand, commodities, input costs, interest rates, currencies, credit conditions, regulation, sector outlooks, company earnings, valuation, and timestamped market news.

Research material provides the underlying market structure, historical theses, sector frameworks, and company sensitivities. New events and news provide evidence that may confirm, weaken, or invalidate those views.

## 2. Build a market knowledge network

Connect fragmented company research into a shared representation:

```text
Company → Business segment → Product → Commodity → Supplier → Customer → Competitor → Industry → Macro factor
```

The objective is to reuse relevant context learned from one company when assessing another company or sector.

## 3. Model cross-sector spillovers

Evaluate direct and higher-order effects. An oil-price increase, for example, can raise upstream producer revenue, increase petrochemical feedstock costs, pressure transportation margins, and affect inflation and interest-rate expectations.

Impact depends on value-chain position, contracts, inventory, pricing power, hedging, and pass-through capacity.

## 4. Make event analysis thesis-conditioned

Assess new evidence against historical investment theses, revenue and cost sensitivities, earnings forecasts, management guidance, valuation assumptions, catalysts, risks, peers, and industry developments.

The intended output separately evaluates fundamental, thesis, valuation, market, and spillover impact, with confidence and material uncertainty.

## 5. Preserve point-in-time evidence

Link conclusions to timestamped evidence so the system can reconstruct what was known on a specific date. The target evidence graph joins claims, source documents, exposures, assumptions, market events, supporting evidence, conflicting evidence, and subsequent thesis revisions.

## Release and evaluation work

Before claiming reproducibility or production readiness:

1. clear a release-eligible current dataset and source-rights record;
2. freeze the evaluation definition and evaluator configuration;
3. publish base and adapted outputs, error analysis, and uncertainty reporting;
4. run independent human review across time periods, markets, and source types;
5. evaluate the system as a research workflow rather than an investment-return engine.

## Long-term objective

Build a thesis-conditioned market-intelligence engine that identifies what changed, who is exposed, how effects propagate through the value chain, which investment theses are affected, and whether the change is likely reflected in expectations or valuation.
