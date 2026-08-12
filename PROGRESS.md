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

## Task: Full website publicity and credibility audit

**Status:** complete
**Started:** 2026-08-10 09:31 +07

### Scope

- Audit the complete report across writing, evidence, structure, visual communication, skimmability, accessibility, and publicity value.
- Optimize the editorial recommendations for a dual goal: demonstrate that Adaption Labs' products worked while establishing Keith Vo and Huy X. Dang as credible finance practitioners.
- Preserve factual distinctions between dataset-specific preference results, category-level transfer evidence, source-document counts, and generated training-row counts.

### Plan

- Ground reviewers in the official positioning of Adaptive Data, AutoScientist, and the challenge.
- Run independent writing/credibility, visual/skimmability, and publicity/structure audits.
- Inspect the live rendered page and synthesize the findings into a prioritized improvement plan without editing the site.

### 2026-08-10 09:36 +07 - Audit context established

**Status:** in progress

**Completed**

- Reviewed the current article, project reference sheet, and official Adaption Labs product pages.
- Defined the central case-study claim: Adaptive Data increased dataset scale and measured quality; AutoScientist produced adapted models preferred over their base models on the reported evaluations.

**Evidence**

- Attempt #1 reports 589 seed rows, 27,862 adapted rows, quality 5.0 to 9.4, an 84-to-16 dataset preference result, and a 77-to-23 Market Analysis category result.
- Attempt #2 reports about 7,000 source reports, 45,758 combined rows, quality 8.0 to 9.4, and an 80-to-20 dataset-specific preference result, with no category-level result.
- Adaption Labs describes Adaptive Data as a way to optimize and expand datasets and AutoScientist as a system that co-optimizes data and training recipes.

**Decisions**

- Reviewers will treat the page as an evidence-led customer case study, not generic promotional copy.
- Recommendations must preserve the distinction between source reports, seed examples, generated rows, and preference win rates.

**Next**

- Collect three independent audit reports and inspect the rendered page for a final synthesis.

**Blockers**

- None

### 2026-08-10 10:02 +07 - Audit complete

**Status:** complete

**Completed**

- Collected independent writing/credibility, visual/skimmability, and publicity/structure reviews.
- Audited the rendered public page at desktop and mobile widths.
- Consolidated the findings and sequenced recommendations in `AUDIT.md`.

**Evidence**

- Reviewers independently estimated current skim comprehension at approximately 60–70%, below the 80% goal.
- Desktop and mobile renders had no horizontal overflow or console errors.
- Official Adaption sources confirmed the intended division of labor: Adaptive Data shapes the data, while AutoScientist automates and co-optimizes training.

**Decisions**

- Preserve the approved title, hero, typography, two-attempt structure, extraction explanation, and evaluation caveats.
- Prioritize credibility blockers before adding the new at-a-glance visual and responsive result graphics.

**Next**

- Implement the P0 items after user approval.

**Blockers**

- None

## Task: Apply approved credibility corrections

**Status:** complete
**Started:** 2026-08-10 09:47 +07

### Scope

- Retain “Scaling 50x” as the chosen public-facing framing.
- Replace the unsupported Figure 5 before/after comparison with a genuinely matched example.
- Replace “external transfer” with accurately scoped category-evaluation language.
- Attribute data-quality measurements as the Adaption platform quality score and separate them from preference evaluations.
- Repair canonical, social-preview, and challenge URLs.
- Label Keith Vo as Equity Research and Huy X. Dang as AI in Finance.
- Re-verify all four Hugging Face releases and capture the remaining audit work in a separate backlog.

### 2026-08-10 09:47 +07 - Corrections started

**Status:** in progress

**Completed**

- Split matched-pair tracing, Hugging Face verification, and wording/backlog review into independent read-only checks.
- Confirmed that the public-facing 50x label is an explicit editorial choice and will remain unchanged.

**Next**

- Apply the verified copy, metadata, author-role, and Figure 5 changes.
- Render and test the updated page at desktop and mobile widths.

**Blockers**

- Waiting for matched-pair provenance and independent Hugging Face verification.

### 2026-08-10 09:57 +07 - Corrections complete

**Status:** complete

**Completed**

- Retained the 50x section label and documented it as an intentional editorial choice.
- Replaced Figure 5 with excerpts from one verified PTB row whose original and enhanced completions share an identical prompt.
- Replaced “external transfer” with broader-category evaluation language and separated model preferences from dataset quality measurements.
- Labeled all 0–10 dataset scores as Adaption platform quality scores and disclosed that the rubric is not public.
- Repaired the production canonical, Open Graph, social-image, and Challenge links.
- Added Keith Vo’s Equity Research role and Huy X. Dang’s AI in Finance role to the byline, introduction, and footer.
- Created `NEXT_IMPROVEMENTS.md` for the unimplemented audit recommendations.
- Re-verified the two datasets and two models through their exact Hugging Face API endpoints.

**Evidence**

- All four Hugging Face API endpoints returned HTTP 200 after the network switched to the hotspot.
- The matched PTB row has stable identifier `MA2_3bddd9966556ba63efafe373`; its prompt hashes identically before and after adaptation, and `enhanced_prompt` is null.
- Playwright confirmed the production canonical and Open Graph URLs, both role labels, three instances of “Attempt #2: Scaling 50x,” two corrected Challenge links, and no obsolete preview URL.
- Desktop and 393px mobile renders have no horizontal overflow; Figure 5 reveals both columns; the browser console reported zero errors or warnings.
- `git diff --check` completed without whitespace errors.

**Next**

- Work through `NEXT_IMPROVEMENTS.md` one item at a time after prioritization.

**Blockers**

- None

## Task: Apply narrative feedback to the Adaption write-up

**Status:** complete
**Started:** 2026-08-10 11:10 +07

### Scope

- Preserve the existing introduction while adding an early, evidence-backed outcome.
- Move metric explanations beside the metrics they interpret.
- Explain AutoScientist through what it changed in the workflow before listing run settings.
- Frame Attempt #2 as the natural response to Attempt #1, with Sara Hooker's comments as confirmation.
- End the Attempt #2 results on the supported scale finding rather than the generalization limitation.

### 2026-08-10 11:13 +07 - Task complete

**Status:** complete

**Completed**

- Added one outcome sentence to the existing introduction without restructuring it.
- Split the original metric primer into two contextual notes beside the first quality and preference results.
- Reframed AutoScientist around the work it handled before retaining the exact training settings.
- Recast Attempt #2 as the response to Attempt #1's scale limitation, with Sara Hooker's comments as confirmation.
- Reordered the Attempt #2 conclusion so the limitation comes first and the supported scaling result lands last.
- Updated the acknowledgement to preserve the same causal attribution.

**Evidence**

- The source diff contains only the approved narrative changes.
- Playwright found all three revised narrative passages in the rendered article.
- Desktop at 1440px and mobile at 393px reported no horizontal overflow and zero console warnings or errors.
- Both metric notes remained within the mobile viewport.

**Decisions**

- Use “were preferred over” rather than “outperformed” to match the pairwise-evaluation evidence precisely.
- Preserve the article's title, section structure, figures, technical settings, and visual system.

**Next**

- None

**Blockers**

- None

## Task: Smooth the table-of-contents indicator

**Status:** complete
**Started:** 2026-08-10 11:31 +07

### Scope

- Replace per-link bullets with one indicator aligned to a shared outer rail.
- Animate the indicator smoothly between active sections and subsections.
- Preserve accurate active-section tracking and reduced-motion behavior.

### 2026-08-10 11:34 +07 - Task complete

**Status:** complete

**Completed**

- Replaced nested per-link bullets with one fixed-rail table-of-contents indicator.
- Added a 360ms eased vertical transition between active entries.
- Replaced the previous intersection observer with scroll-position tracking so the final Acknowledgements and Resources sections activate correctly.
- Preserved smooth anchor navigation and disabled motion when reduced motion is requested.

**Evidence**

- Playwright verified Introduction, Extraction, Attempt #2, Results, Acknowledgements, and Resources all activate the correct link.
- Every active state reported the same `-14.4px` indicator rail position and zero horizontal overflow.
- Visual inspection confirmed the indicator sits outside both section and subsection text.
- Reduced-motion emulation reduced the transition to `0.01ms` and disabled smooth page scrolling.
- The browser console reported zero errors or warnings.

**Decisions**

- Keep subsection text indented for hierarchy while decoupling the indicator from link indentation.
- Use one moving pseudo-element rather than rendering and fading separate bullets.

**Failures and recovery**

- The first multi-section Playwright selector check was malformed by shell interpretation and returned `zsh: no matches found: a[href=#]`; rerunning with string concatenation completed successfully and did not affect the page.

**Next**

- None

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
