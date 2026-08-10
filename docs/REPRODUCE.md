# Reproduction

## What is public

Attempts #1 and #2 have externally released datasets and LoRA adapters. Their links are catalogued in [data/README.md](../data/README.md) and [model_card/README.md](../model_card/README.md).

The public record also includes:

- base models and LoRA configurations;
- reported dataset sizes and quality changes;
- aggregate base-versus-adapted preference results;
- figures used by the report;
- known data and evaluation limitations.

## What is not included here

The public releases support partial inspection and reuse under their host-page terms, but this repository does not include:

- the original institutional source reports;
- a complete source-rights and provenance record;
- the full AutoScientist runtime and infrastructure;
- a frozen evaluator definition and configuration;
- evaluator identity, comparison counts, exact evaluation prompts, response-order randomization, tie handling, and matched decoding settings;
- the mapping between platform evaluations and the local 73-row held-out split;
- all base and adapted per-example outputs;
- an independent error analysis or statistical-significance study.

The reported runs therefore cannot be reproduced end to end from this repository alone.

## Figures

The figures in `assets/` document the extraction workflow, data-quality changes, and aggregate preference results for Attempts #1 and #2. They are historical evidence from the reported workflow, not independently reproduced evaluations.

## Future evaluation

The roadmap proposes point-in-time evidence, global transfer tests, multi-horizon impact, and market-feedback evaluation. Those are future research directions and have not been implemented or evaluated in this report.
