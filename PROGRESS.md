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

**Status:** complete

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

## Task: Replace the extraction card with the generated diagram

**Status:** complete
**Started:** 2026-08-11 14:09 +07

### Scope

- Compare a responsive HTML concept with an ImageGen alternative for the report-to-training-pair explanation.
- Use the selected generated image without its title or footer caption.
- Preserve the published article's surrounding extraction narrative.

### 2026-08-11 14:51 +07 - Task complete

**Status:** complete

**Completed**

- Collected three independent comparisons of the HTML and generated alternatives.
- Cropped the generated image from 1536 by 1024 to 1536 by 680, removing only its title and footer caption.
- Replaced the four-step extraction card with the cropped diagram and removed its obsolete CSS.
- Added a controlled mobile bleed so the wide image remains more legible without horizontal scrolling.

**Evidence**

- New asset: `assets/extraction-report-to-training-pair.png`
- Desktop and 390px mobile renders were inspected in Playwright.
- `git diff --check` completed without errors.

**Decisions**

- Use the generated composition directly, as requested, rather than rebuilding it as HTML.
- Keep the image clickable at full resolution and retain descriptive alternative text.

**Next**

- None

**Blockers**

- The original Desktop worktree became inaccessible to the tool process, so the isolated change was applied and verified in a temporary clone of the same repository. The blocked local files were not modified.

## Task: Recommend the next Market Analysis training configuration

**Status:** complete
**Started:** 2026-08-11 19:56 +07

### Scope

- Diagnose the new Llama 4 Scout LoRA run from its dataset mixture, hyperparameters, and two preference win rates.
- Compare it with the known Attempt #1 and Attempt #2 evidence without treating preference scores as accuracy.
- Recommend one exact next configuration aimed at improving held-out Market Analysis transfer.

### Plan

- Verify the four dataset inputs and relevant model/training constraints.
- Separate data-mixture, optimization, and evaluation explanations for the transfer gap.
- Produce a prioritized next run plus a minimal ablation sequence and promotion criteria.

**Blockers**

- The exact Market Analysis evaluation sample size and per-task breakdown have not yet been provided.

### 2026-08-11 20:31 +07 - Training diagnosis complete

**Completed**

- Verified the public Attempt #1 and three Attempt #2 dataset mirrors and profiled all 73,564 exported rows.
- Compared row counts, prompt/response lengths, exact overlap, and the Attempt #2 task/asset taxonomy.
- Checked the current Llama 4 Scout LoRA recipe against the official Meta model card and Hugging Face TRL/PEFT guidance.
- Recommended a conservative next run and separated it from a later data-mixture ablation.

**Evidence**

- The current model already wins 82:18 on its own distribution but only 65:36 on the Market Analysis category, which points to a transfer gap rather than simple underfitting.
- The three new exports contain no exact training-input or output duplicates, but 67.1% of their rows are concentrated in insufficient-evidence and market-state tasks.
- The current run uses the upper end of the documented LoRA learning-rate range, three epochs, zero adapter dropout, rank 32, and broad attention/expert targeting.

**Decision**

- Hold the dataset and target modules fixed for the next run; reduce update pressure to rank 16, alpha 32, dropout 0.05, learning rate 1e-4, and two epochs, with ten evaluations.
- Evaluate on a source-grouped local Market Analysis set and require a transfer gain without a material collapse in on-dataset preference.

**Remaining uncertainty**

- Statistical significance cannot be assessed until the exact pairwise evaluation count and tie policy are known.

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

## Task: Render a 16:9 website showcase video

**Status:** in progress
**Started:** 2026-08-10 14:02 +07

### Scope

- Create a silent, 30-second, 16:9 HyperFrames video that presents the finance-model report as a website showcase.
- Use the report's existing cover, figures, and verified result language.
- Deliver a local MP4 and preserve a reproducible composition source.

### Plan

- Create a dedicated HyperFrames composition and storyboard the report into a concise visual narrative.
- Render locally, inspect representative frames, and revise any readability or timing issues.
- Deliver the MP4 and source files.

### 2026-08-10 14:02 +07 - Environment and brief confirmed

**Status:** in progress

**Completed**

- Confirmed a silent 30-second 16:9 website showcase as the production brief.
- Confirmed local Node.js `v24.13.0` and FFmpeg `8.1.2`, which meet HyperFrames' published local-render requirements.

**Evidence**

- HyperFrames README documents HTML-to-MP4 rendering and its website showcase workflow.
- `node --version` and `ffmpeg -version` completed successfully in the report workspace.

**Decisions**

- Build a dedicated composition rather than attempting to record a scroll through the live article, so the output remains deterministic and readable at video pace.

**Next**

- Scaffold the composition and render a first pass.

**Blockers**

- None

## Task: Audit Attempt #1 and Attempt #2 organization

**Status:** complete
**Started:** 2026-08-10 16:35 +07

### Scope

- Collect independent feedback on the organization of paragraphs, figures, and subsections in both attempts.
- Preserve the existing article during the audit and avoid implementation changes.

### Plan

- Run isolated reviews of Attempt #1, Attempt #2, and the cross-attempt visual and narrative flow.
- Compare the reviews against the rendered source and synthesize the recurring issues into a prioritized recommendation.

### 2026-08-10 16:51 +07 - Independent organization audit complete

**Status:** complete

**Completed**

- Collected isolated structural reviews for Attempt #1, Attempt #2, and the cross-attempt narrative.
- Compared their findings and identified the recurring sequencing and hierarchy problems.
- Produced a reader-first reorganization that retains the current evidence and visuals.

**Evidence**

- All three reviews found that the macro story is credible but that claims, figures, interpretations, and caveats are too often separated.
- Attempt #1's principal issue is local sequencing around extraction, adaptation, and evaluation.
- Attempt #2's principal issue is an overloaded Data subsection and a late explanation of how its evaluation differs from Attempt #1.

**Decisions**

- Recommend reorganizing around claim -> evidence -> interpretation, with an explicit proof-to-scale bridge.
- Recommend removing or repurposing the redundant first extraction figure and adding lightweight internal labels within Attempt #2.

**Next**

- Await approval before reorganizing the article.

**Blockers**

- None

### 2026-08-10 16:52 +07 - Goal-centered organization implemented

**Status:** complete

**Completed**

- Reframed both attempts around the goal of producing useful first-draft equity research.
- Reordered Attempt #1 into complete claim, evidence, and interpretation units.
- Added internal hierarchy to Attempt #2 for source breadth, task breadth, and adaptation recipes.
- Moved evaluation scope and limitations next to the results they qualify.

**Evidence**

- Figure captions remain sequential from Figure 1 through Figure 10.
- `git diff --check` completed without whitespace errors.
- The article now lands on the remaining capability gap before transitioning into What's next.

**Decisions**

- Preserve the approved top-level TOC labels while using small fourth-level headings inside Attempt #2.
- Keep both extraction visuals, but separate them with the failure evidence and answer-first explanation.

**Next**

- Publish the reorganization.

**Blockers**

- The in-app browser does not permit direct `file://` navigation, so verification used source and structural checks rather than a fresh browser render.

## Task: Compare HTML and ImageGen extraction figures

**Status:** in progress
**Started:** 2026-08-11 14:09 +07

### Scope

- Create one deterministic HTML/CSS explanation and one ImageGen alternative for the report-to-training-pair method.
- Keep both alternatives isolated from the published article.
- Have independent reviewers compare immediate comprehension, methodological accuracy, visual fit, and responsive suitability.

### Plan

- Build both alternatives around the same core message and example.
- Render and inspect the HTML version and inspect the generated image.
- Collect blind comparative reviews and recommend the stronger production direction.

**Blockers**

- None

## Task: Publish the latest final-run results

**Status:** complete
**Started:** 2026-08-12 07:35 +07

### 2026-08-12 07:40 +07 - Latest evaluation published

**Status:** complete

**Completed**

- Replaced the older Attempt #2 Llama 4 result with the final Llama 3.3 70B LoRA run.
- Documented the 48,496-row training mixture, rank-16 recipe, and new 87-to-13 dataset and 74-to-27 Market Analysis preference results.
- Replaced the result screenshot and updated the Attempt #2 run ID.
- Added a restrained comparison explaining that the new run retained strong Market Analysis performance but is not proven superior to Attempt #1 overall.

**Evidence**

- Desktop and 393px Playwright checks loaded the 1600-by-1162 result asset, found the updated Figure 7 caption, and reported zero horizontal overflow.
- `git diff --check` completed without whitespace errors.

**Next**

- None

**Blockers**

- None

## Task: Align Attempt #2 with the finalized release

**Status:** complete
**Started:** 2026-08-12 08:20 +07

### Scope

- Separate the development candidate pool from the finalized finance dataset and training mixture.
- Update the scale figure, evaluation context, run metadata, and public artifact links.
- Preserve the article's existing restrained technical tone and visual system.

### Decisions

- Describe 45,758 rows as the three-recipe candidate pool, not the final dataset.
- Describe 34,640 as the released finance dataset, 48,496 as the pre-split mixture after general-purpose replay, and 48,127 as the rows used for training.
- Retain the candidate-pool taxonomy and quality figures as development history, with explicit captions.

**Next**

- Verify desktop and mobile rendering, then commit and publish.

**Blockers**

- None

### 2026-08-12 11:50 +07 - Finalized Attempt #2 narrative verified

**Status:** complete

**Completed**

- Reframed 45,758 rows as the development candidate pool rather than the final dataset.
- Updated the scale figure to show 589 baseline rows, 27,862 Attempt #1 adapted rows, 34,640 finalized finance samples, and the 48,496-example pre-split mixture.
- Added the exact 48,127-row training count and preserved the final 87-to-13 and 74-to-27 preference results.
- Scoped the taxonomy and quality figures to recipe development.
- Replaced the stale Attempt #2 artifact links and ambiguous run metadata with the finalized dataset, weights, job ID, and experiment ID.

**Evidence**

- Desktop and 393px browser checks reported zero page overflow and zero console warnings or errors.
- The four-stage scale figure, candidate-pool table, and compact Resources block were visually inspected at mobile width.
- The deployed artifact URLs were verified as public before being added.
- `git diff --check` completed without errors.

**Next**

- Commit and push the verified update.

**Blockers**

- None

## Task: Remove stale Attempt #2 development artifacts

**Status:** complete
**Started:** 2026-08-12 12:06 +07

### Scope

- Audit every Attempt #2 statement, diagram, table, screenshot, caption, and resource against the finalized run.
- Remove development-candidate artifacts that compete with or contradict the final dataset and evaluation story.
- Preserve the established editorial tone and minimalist Be Vietnam Pro visual system.

### 2026-08-12 12:06 +07 - Publication inconsistency confirmed

**Status:** in progress

**Completed**

- Confirmed that the published section still gave the abandoned 45,758-row candidate pool a taxonomy figure, comparison table, quality screenshot, and several paragraphs.
- Confirmed that the prior scale graphic included the 27,862-row Attempt #1 adapted set, obscuring the final Attempt #2 lineage.

**Decisions**

- Make the final run the only primary visual story in Attempt #2.
- Reduce development recipe history to the single fact needed to explain why Dataset 2 was selected.

### 2026-08-12 12:22 +07 - Final-run narrative rebuilt

**Status:** in progress

**Completed**

- Removed the 45,758-row candidate-pool taxonomy, Dataset 1-3 table, 8.0-to-9.4 screenshot, and all related prose.
- Replaced the misleading growth chart with the finalized composition: 34,640 finance samples plus 13,856 general-purpose examples equals a 48,496-example pre-split mixture, with 48,127 examples trained.
- Renumbered the final evaluation screenshot to Figure 5 and retained the verified 87-to-13 and 74-to-27 results.
- Corrected the closing description from a "small model" to an adapted model.

**Next**

- Remove obsolete assets and verify desktop and mobile output.

**Blockers**

- None

### 2026-08-12 12:30 +07 - Corrected publication verified

**Status:** complete

**Completed**

- Deleted the obsolete Attempt #2 quality screenshot asset and all styles used only by the removed charts and table.
- Fixed the mobile mixture equation so its arithmetic operators remain legible.

**Evidence**

- Desktop and 393px browser checks found no horizontal overflow and no console errors or warnings.
- Browser text inspection found none of the stale 45,758-row candidate-pool labels or old Figure 6/7 captions.
- The final result asset rendered at its expected 1600-by-1162 resolution with the 87-to-13 and 74-to-27 caption.
- All asset references resolve locally, and `git diff --check` completed without errors.

**Next**

- Commit and push the corrected publication.

**Blockers**

- None

## Task: Crop the final Attempt #2 result figure

**Status:** complete
**Started:** 2026-08-12 12:42 +07

### 2026-08-12 12:45 +07 - Result screenshot cropped

**Status:** complete

**Completed**

- Cropped the existing Attempt #2 screenshot so it begins at “Training Winrates” and retains the complete two-chart result area below.
- Updated the intrinsic image dimensions in the article from 1600 by 1162 to 1600 by 602.

**Evidence**

- The final asset was inspected at original resolution and contains only the verified 87-to-13 and 74-to-27 evaluation panel.
- The crop is a deterministic extraction from the original screenshot; no retained pixels were redrawn or restyled.
- Desktop and 393px browser checks loaded the 1600-by-602 asset with zero horizontal overflow and zero console errors or warnings.

**Next**

- Commit and push.

**Blockers**

- None

## Task: Correct release identifiers

**Status:** complete
**Started:** 2026-08-12 13:35 +07

### 2026-08-12 13:38 +07 - Resource identifiers corrected

**Status:** complete

**Completed**

- Renamed “Run ID” to “Model ID” in the Resources section.
- Replaced Attempt #2’s internal Job and Experiment identifiers with the submitted Model ID and Dataset ID.
- Updated the copy-button values and accessibility labels to match the visible identifiers.

**Evidence**

- Attempt #2 now displays Model ID `adaption_llama_3_3_70b_instru_final_final_8228cf21` and Dataset ID `3038bafd-a898-4712-9020-2357cd5b8855`.

**Next**

- Verify, commit, and push.

**Blockers**

- None

## 2026-10-16 — Reconcile PR #1 with finalized main

- Merged `main` at `a313bcda93e224720bc426489ce2d6d4b42d1c51` into the existing author branch, preserving exactly two completed attempts with Attempt #2 latest.
- The finalized Attempt #2 record supersedes the earlier candidate-pool and Llama 4 Scout descriptions above: 34,640 finance samples plus 13,856 general-purpose examples form a 48,496-example pre-split mixture; the rank-16 Llama 3.3 70B adapter trained for two epochs at `1e-4` and recorded 87:13 on-dataset and 74:27 Market Analysis preferences.
- Preserved main's generated extraction diagram, cropped final figure, release identifiers, linked service rows, navigation, accessibility, and figure motion. Updated the companion dataset, model, result, and figure records to match those source changes.
- Retained the platform-quality versus model-evaluation distinction, unpublished preference-protocol and split-hygiene limits, and explicitly aspirational roadmap. Historical entries above describe their then-current records, not additional completed attempts.
- No tests, build, lint, formatter, preview, or static verification command was run during reconciliation. Final bounded verification is delegated; the existing finite contract is `git diff --check a313bcda93e224720bc426489ce2d6d4b42d1c51 <final-sha>`.
- Vercel deployment access remains outside this source-only reconciliation; a blocked deployment is not evidence of a static build failure.
