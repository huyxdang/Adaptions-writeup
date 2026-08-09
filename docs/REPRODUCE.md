# Reproduction and Data Availability

## Current AdaptMarket experiment

This repository does not contain the current experiment's source documents, training examples, evaluation examples, model weights, prompts, credentials, private infrastructure, or unpublished outputs.

The current full fine-tune cannot be reproduced from this public repository.

### What can be checked

The public record includes:

- the base model and training configuration;
- the experiment and fine-tune job identifiers;
- platform-reported base and adapted preference rates;
- methodology, limitations, and planned research direction.

### What full reproduction requires

1. A release-eligible dataset and source-rights record.
2. A frozen evaluation definition and evaluator configuration.
3. Base and adapted outputs for the reported evaluation.
4. Error analysis, uncertainty reporting, and release hashes.
5. Clearance to publish every included artifact.

## Predecessor experiments

Attempts #1 and #2 have externally released datasets and LoRA adapters. Their links are catalogued in [data/README.md](../data/README.md) and [model_card/README.md](../model_card/README.md).

Those releases support partial inspection and reuse under their host-page terms, but they do not provide complete reproduction of every reported result. Exact source-document provenance, the full AutoScientist runtime, frozen evaluator configuration, and all per-example evaluation outputs are not published here.

The predecessor releases also do not reproduce AdaptMarket: the current experiment uses a different base model and full-model fine-tuning.

## Figures

The figures in `assets/` support the public report in `index.html`. They document predecessor workflow and aggregate results; they are not new evaluation evidence and do not contain the current restricted corpus.

Artifacts for the current experiment will be linked only after the conditions above are met.
