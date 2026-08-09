# Progress log

## Task: Add on-scroll motion to article figures

**Status:** complete
**Started:** 2026-08-10 00:13 +07

### Scope

- Add relevant on-scroll animation to each article figure while preserving the editorial visual system.
- Respect reduced-motion preferences and verify desktop and mobile behavior.

### Plan

- Inventory existing figure types and consolidate the current one-off observers.
- Implement figure-specific reveals for screenshots, process steps, funnels, taxonomies, and scale charts.
- Run browser checks for sequencing, layout stability, responsiveness, and reduced motion.

### 2026-08-10 00:13 +07 - Motion system selected

**Status:** in progress

**Completed**

- Identified ten numbered article figures and the existing one-off animations for the scale chart and before/after comparison.

**Evidence**

- `index.html` contains screenshot, process-flow, funnel, before/after, scale-chart, and taxonomy figure types.

**Decisions**

- Use a single IntersectionObserver and animate each figure according to what its visual encodes: screenshots resolve, process rows sequence, and quantitative bars grow from their origin.
- Run each reveal once and leave content fully visible when JavaScript or motion is unavailable.

**Next**

- Implement the consolidated CSS and JavaScript, then verify in a browser.

**Blockers**

- None

### 2026-08-10 00:18 +07 - Figure animations implemented

**Status:** in progress

**Completed**

- Consolidated the separate chart observers into one figure-level, one-shot IntersectionObserver.
- Added tailored reveals for screenshots, process steps, extraction-funnel bars, the before/after comparison, the scale chart, taxonomy bars, and captions.
- Kept all figures visible by default when JavaScript is unavailable or reduced motion is requested.

**Evidence**

- `index.html` now applies `motion-ready` and `is-visible` at the figure level and contains figure-specific transition selectors.

**Decisions**

- Quantitative graphics animate from their baseline rather than fading as a single card, so motion reinforces how the figure should be read.
- Screenshot reveals use a short focus-and-settle effect; captions follow after the visual establishes itself.

**Next**

- Validate syntax, launch the site, and inspect desktop, mobile, and reduced-motion states.

**Blockers**

- None

### 2026-08-10 00:22 +07 - Task complete

**Status:** complete

**Completed**

- Added one-shot, on-scroll motion to all ten numbered article figures.
- Preserved static rendering for reduced-motion users and no-JavaScript fallback behavior.
- Verified the desktop and 393px mobile layouts.

**Evidence**

- Playwright reported 10 figures initialized and all 10 reaching their final visible state after scrolling.
- Desktop and mobile both reported zero horizontal overflow and zero console errors or warnings.
- Reduced-motion emulation reported no motion classes, with figure imagery and captions at full opacity.
- Mobile screenshot review confirmed the taxonomy labels, bars, percentages, border, and caption remained legible and aligned.
- `git diff --check` completed without whitespace errors.

**Next**

- None

**Blockers**

- None

## Task: Document the AdaptMarket experiment

**Status:** complete
**Started:** 2026-08-10 02:42 +07

### 2026-08-10 02:48 +07 - AdaptMarket added to the report

**Status:** complete

**Completed**

- Added AdaptMarket as Attempt #3 without rewriting the historical Attempt #1 or Attempt #2 records.
- Documented the 30 July 2026 full fine-tune of `mistralai/Mixtral-8x7B-Instruct-v0.1` and its platform-reported 85-to-15 on-dataset and 73-to-27 Market Analysis results.
- Added the public research record and experiment identifiers while preserving the stated release restrictions for data, prompts, weights, and evaluation outputs.
- Updated the desktop and mobile tables of contents, cross-experiment comparison, repository summary, and resources.

**Evidence**

- AdaptMarket documents full-model supervised fine-tuning, one epoch, disabled LoRA, and a 30 July 2026 experiment record.
- Before the update, `https://adaptions-writeup.vercel.app/` returned HTTP 200 and passed desktop and 393px mobile checks with all ten figures loaded, no horizontal overflow, and no console errors or warnings.
- The updated local report passes desktop, 393px mobile, and reduced-motion browser checks with no missing anchors, duplicate IDs, broken images, horizontal overflow, or console errors or warnings.
- `git diff --check` completed without whitespace errors.

**Decisions**

- Treated AdaptMarket as a third experiment because its base model, full fine-tuning method, identifiers, and evaluations differ from the first two attempts.
- Kept the new section text-only because AdaptMarket has no cleared public result artifacts.
- Did not compare preference scores as a direct ranking because the models, data, training methods, and evaluation scopes differ.

**Next**

- Publish the write-up changes so Vercel can deploy Attempt #3.

**Blockers**

- None

## Task: Synchronize the public experiment records

**Status:** in progress
**Started:** 2026-08-10 03:51 +07

### 2026-08-10 03:51 +07 - Reciprocal updates prepared

**Status:** pending merge

**Completed**

- Prepared the AdaptMarket pull request with the complete three-experiment history, current model card, aggregate results, release boundaries, and predecessor artifact index.
- Archived the six report figures used by the AdaptMarket record with checksums and the source MIT notice.
- Added the canonical AdaptMarket repository to this README and confirmed that this branch's Attempt #3 resources already link back to it.
- Opened the AdaptMarket documentation pull request.

**Evidence**

- AdaptMarket pull request: https://github.com/Kitkitkittt/AdaptMarket/pull/1
- All AdaptMarket relative Markdown links resolve, and all six archived image hashes match the live report assets.
- The AdaptMarket content review found no factual, release-boundary, placeholder, or provenance issues.

**Decisions**

- Kept the current AdaptMarket corpus, prompts, weights, and per-example evaluation records restricted.
- Kept predecessor datasets and LoRA adapters labeled separately from the current experiment.
- Did not add a duplicate report link because this branch's Attempt #3 resource section already points to the canonical repository.

**Next**

- Merge both documentation pull requests and let the production deployment publish Attempt #3.

**Blockers**

- Vercel cannot create a PR preview until `@Kitkitkittt` is added to the deployment team; production deployment remains on the Attempts #1–2 version until merge.
