# Progress log

## Task: Add on-scroll motion to article figures

**Status:** complete
**Started:** 2026-08-10 00:13 +07

### Scope

- Add relevant on-scroll animation to each article figure while preserving the editorial visual system.
- Respect reduced-motion preferences and verify desktop and mobile behavior.

### 2026-08-10 00:22 +07 - Task complete

**Completed**

- Added one-shot, on-scroll motion to all ten numbered article figures.
- Preserved static rendering for reduced-motion users and no-JavaScript fallback behavior.
- Verified the desktop and 393px mobile layouts.

**Evidence**

- Playwright reported 10 figures initialized and all 10 reaching their final visible state after scrolling.
- Desktop and mobile both reported zero horizontal overflow and zero console errors or warnings.
- Reduced-motion emulation reported no motion classes, with figure imagery and captions at full opacity.
- `git diff --check` completed without whitespace errors.

## Task: Correct the experiment record and add future improvements

**Status:** complete
**Started:** 2026-08-10 11:01 +07

### 2026-08-10 11:01 +07 - Two-attempt record restored

**Completed**

- Corrected the public record to two completed attempts, with Attempt #2 as the latest experiment.
- Removed all obsolete model, method, result, identifier, artifact, and release claims outside the corrected two-attempt record.
- Preserved the verified Attempt #1 and Attempt #2 facts, figures, public datasets, LoRA adapters, and run identifiers.
- Replaced the obsolete section with a future-improvement roadmap toward global market-system intelligence.
- Added point-in-time evidence, dynamic relationships, cross-sector and cross-asset transmission, multi-horizon impact, market-feedback evaluation, adaptive retrieval, and global transfer testing as future directions.
- Recorded FinRipple and Point-in-Time Financial RAG with Market-Feedback Adaptive Retrieval as research blueprints, not implemented components.

**Decisions**

- Treat only completed and evidenced training runs as numbered attempts.
- Keep future work explicitly aspirational and separate from reported evaluation results.
- Keep Attempt #2's 80:20 result framed as evidence of scale and breadth, not superior generalization to Attempt #1.

### 2026-08-10 14:20 +07 - Live report synthesis and final verification

**Completed**

- Rebased the corrected narrative on the latest live-report structure and preserved its verified extraction provenance, product-role wording, author roles, navigation, accessibility, figures, and on-scroll motion.
- Added the failed fixed-template review, answer-first derivation, leakage controls, Attempt #1 training details, Attempt #2 task shares, exact row arithmetic, and shared-source grouping caveat.
- Distinguished Adaption platform dataset-quality scores from model evaluations and disclosed the unpublished scoring rubric and preference-protocol limits.
- Qualified Attempt #1's broader-category result because independence from the local held-out split and complete split hygiene are not established publicly.
- Added the full aspirational Future Improvement section to the report and linked the verified FinRipple source.

**Verification**

- `git diff --check` passed.
- The repository-wide forbidden-term scan passed.
- All Markdown-local links resolved.
- HTML parsing found no duplicate IDs, missing anchors, or missing local assets.
- Figure checksums remained unchanged.
- Playwright with installed Edge returned HTTP 200 on desktop, 393px mobile, and reduced-motion contexts.
- Browser checks found zero horizontal overflow, zero broken images, zero console errors or warnings, all 10 figures reaching their visible state, and no motion classes under reduced motion.
- Desktop and mobile screenshots were generated in the temporary validation directory; this interface could not visually inspect the image attachments.
- `pytest -q` found no tests in this standalone static-report repository.

**Next**

- Publish the corrected two-attempt report and future-improvement roadmap.

**Blockers**

- None
