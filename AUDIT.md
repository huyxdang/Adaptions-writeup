# Website audit: publicity, credibility, and skimmability

Date: 2026-08-10

## Executive verdict

The site has a strong technical core and a distinctive, restrained visual direction. Its best material is the answer-first extraction method, the clear two-attempt progression, the preference-versus-accuracy disclaimer, and the honest statement that Attempt #2 does not establish better generalization.

The page is not yet ready to do its full publicity job. Three independent reviews estimated that a skimming reader currently recovers about **65–70%** of the story, short of the 80% target. The evidence that makes Adaption Labs look effective appears too late, while several credibility gaps could distract a technical reader from otherwise strong results.

The recommended direction is an evidence-led customer case study:

> Reports contained analyst reasoning but no prompts. We reconstructed supportable prompts, used **Adaptive Data** to expand and structure the training data, and used **AutoScientist** to train adapters preferred over their base models. Attempt #1 provides the broader-category evidence; Attempt #2 shows that the workflow can operate at greater scale and breadth.

## Current scorecard

| Area | Score | Assessment |
|---|---:|---|
| Narrative structure | 7/10 | Clear two-attempt story; results synthesis arrives too late |
| Product publicity | 7/10 | Fair attribution; product outcomes are buried |
| Author credibility | 5/10 | Names are visible, but roles and complementary expertise are not |
| Evidence and trust | 6/10 | Good caveats; evaluation protocol and quality-score meaning are under-specified |
| Skimmability | 6/10 | Many figures, but the causal chain still requires paragraph reading |
| Visual design | 8/10 | Strong hero, typography, restraint, responsiveness, and motion |
| Resources and conversion | 6/10 | Models and datasets are linked; code, methodology, and a clear Adaption pathway are incomplete |
| SEO and social sharing | 4/10 | Canonical and Open Graph URLs use a preview deployment |
| Accessibility | 7/10 | Good foundations; several labels, captions, and hit targets are too small |
| Performance | 7/10 | Static and lazy-loaded; one figure is 1.5 MB and three font families are remote |

## P0: fix before the main publicity push

### 1. Put the proof immediately below the cover

Add a single, compact two-row overview. It should be the page's signature explanatory visual, not a collection of cards.

**Attempt #1 — Prove the method**

`~1,500 reports → 589 seed examples → Adaptive Data: 27,862 rows, 5.0 → 9.4, C → A → AutoScientist: 84:16 own-dataset preference, 77:23 Market Analysis category preference`

**Attempt #2 — Scale the workflow**

`~7,000 reports → Adaptive Data: 45,758 published rows (~15,250 unique generated items), 8.0 → 9.4, B → A → AutoScientist: 80:20 own-dataset preference; no category evaluation`

Add a one-line note: `Preference results are not accuracy scores.`

This visual should make the division of labor explicit:

- Keith and Huy supplied the domain problem, source material, extraction method, and seed data.
- **Adaptive Data** expanded and restructured the data.
- **AutoScientist** trained and evaluated the adapted models.

### 2. Correct Figure 5 before/after provenance

Figure 5 claims to show one completion before and after **Adaptive Data**, with the evidence and task unchanged. The displayed excerpts do not appear to describe the same facts:

- The "before" text discusses a BUY rating, mines, quartz, furniture exports, and a target price.
- The "after" text discusses a topping-out event, pre-sales, and revenue recognition.

Use an actual matched pair from one row, or relabel the visual as a representative format comparison. Do not claim content preservation without matched provenance and a stated verification method.

### 3. Add an evaluation-protocol disclosure

The page correctly states that preference is not accuracy, but it does not say enough about how the comparisons were produced. State every known detail and mark unavailable details as unavailable:

- Evaluator or judge
- Number of comparisons
- Prompt provenance
- Response-order randomization
- Tie handling
- Whether decoding settings matched
- Relationship between the reported evaluation and the local 73-row split

The known Attempt #1 split contamination must be disclosed. Describe 84:16 as an in-distribution diagnostic and 77:23 as broader Adaption category evidence. Avoid "external transfer" unless independence and split hygiene can be established.

### 4. Retain "Scaling 50x" as an editorial label

After review, the authors chose to retain **Attempt #2: Scaling 50x** as the simpler public-facing framing. The body still reports the exact counts—45,758 published rows and roughly 15,250 unique generated items—so readers can distinguish the editorial label from the underlying measurements. Do not replace the label with 25× or 77.7×.

### 5. Define the quality metric honestly

Call 5.0 → 9.4 and 8.0 → 9.4 the **Adaption platform quality score**. Explain what the score measures, who assigns it, and whether it is comparable between runs. If no public rubric exists, say so.

Do not let response length or the presence of headings stand in for quality. Explain that structure improved inspectability, then support task preservation separately.

### 6. Repair publicity metadata and primary links

- Change canonical, `og:url`, and all social-image URLs to `https://adaptions-writeup.vercel.app/`.
- Change `og:site_name` from Huy alone to `Keith Vo & Huy X. Dang` or a neutral project identity.
- Point "AutoScientist Challenge" to `https://adaptionlabs.ai/blog/autoscientist-challenge`, not the AutoScientist product announcement.
- Add a result to the Open Graph description.
- Create a dedicated 1200×630 social card containing the title, both authors, Adaption Labs, and one carefully scoped result such as `77:23 on Adaption's Market Analysis preference evaluation`.

## P1: make 80% skimming possible

### Preserve these strengths

- Keep the approved title and liquid-pixel hero.
- Keep the restrained typography and editorial layout.
- Keep the two-attempt organization and compact table of contents.
- Keep the preference-versus-accuracy disclaimer.
- Keep the honest Attempt #2 generalization caveat.
- Keep the answer-first extraction section; it is the strongest technical explanation.

### Make the authors' authority explicit

Under the byline and in the footer, state:

- **Keith Vo — Equity Research**
- **Huy X. Dang — AI in Finance**

Connect the roles to the work: Keith grounds the equity-research workflow; Huy grounds the data and model system.

### Replace Figure 1 with the actual end-to-end argument

The current generated illustration is attractive but generic. Replace it with a project-native flow:

`Report: evidence + conclusion → remove conclusion → reconstruct supported prompt → Adaptive Data → AutoScientist → preference evaluation`

This should be the one signature animation. It explains the system faster than prose and gives Adaption's products an accurate place in the workflow.

### Rebuild the most important screenshots as responsive native visuals

The official screenshots should remain available as source evidence, but the primary article visuals should be responsive HTML or SVG:

- Figure 6: large `16 → 84` and `23 → 77` panels; the current wide screenshot becomes illegible on mobile.
- Figure 9: a compact `8.0 → 9.4` and `B → A` comparison; the current screenshot contains excessive whitespace.
- Consider the same treatment for Figure 10's `20 → 80` result.

### Make captions carry conclusions

Bold the takeaway rather than only the figure number. Examples:

- **Adaptive Data expanded 589 seed examples to 27,862 rows and raised the platform quality score from 5.0 to 9.4.**
- **The adapted model was preferred 84:16 in-distribution and 77:23 on Adaption's broader Market Analysis category.**
- **More than one third of Attempt #2 teaches the model when not to conclude.**
- **Attempt #2 produced an 80:20 in-distribution preference; no category evaluation was produced.**

Do not delay captions after the animation; they are part of the skim layer.

### Add a real model-behavior comparison

Show one shared finance prompt with base and adapted responses, annotated against the equity-research criteria. The current page shows data transformation and aggregate win rates, but not the behavior readers ultimately care about.

### Add a conclusion before Acknowledgements

Use a compact "What each attempt established" comparison:

- **Attempt #1:** established the extraction/training method and produced broader-category evidence.
- **Attempt #2:** showed that the data and training workflow could operate across a much broader finance corpus.
- **Open test:** clean generalization and component-level causality remain unproven.

### Separate process measurements from evaluation evidence

Do not say the 80:20 result proves source breadth, row count, or B → A quality. Those are separate operational measurements. Present them in separate sentences and then state the scoped conclusion.

### Strengthen Resources

Add:

- AdaptMarket code repository
- Challenge rules
- Public Adaption dataset pages, if accessible to readers
- A concise provenance/methodology note
- A compact Adaption block: `Explore Adaptive Data · Train with AutoScientist · View the Challenge`

## P2: polish

- Replace "institutional-grade" with a precise description such as "sell-side" or "institutional research reports".
- Change "Southeast Asia's listed companies" to "Southeast Asian listed companies".
- Use `source reports`, `seed examples`, `generated variants`, `training rows`, and `unique generated items` consistently.
- Change the subtitle's `5,000+` to the article's more precise `about 7,000`, or explain the counting boundary.
- Explain why the base model changed between attempts and whether the team or **AutoScientist** chose it.
- Recast the 72% similarity threshold as a leakage-risk heuristic, not a universal definition of leakage.
- Define "leakage groups" or use a less alarming term.
- Move dense LoRA and generation details into an expandable technical-details section.
- Increase mobile caption and resource text toward 14px and enlarge interactive hit targets.
- Add a table caption and make the horizontal-scroll container keyboard-focusable.
- Add print/full-page-capture CSS that forces animated figures visible.
- Compress `assets/extraction-doc-to-prompt.png` from its current 1.5 MB, preferably to AVIF or WebP.
- Add publication/modified dates, Article JSON-LD, `article:author`, `robots.txt`, and a minimal sitemap.

## Recommended causal spine

1. **Missing prompts:** institutional reports contain evidence and conclusions, but not the instructions needed for supervised training.
2. **Reconstruct the task:** answer-first extraction removes the conclusion and asks only what the remaining evidence can support.
3. **Prove the workflow:** **Adaptive Data** expands and structures the seeds; **AutoScientist** trains the first adapter; the reported preferences favor the adapted model.
4. **Address the bottleneck:** narrow company coverage and too few seeds motivate more reports, macro context, and more generated variants.
5. **Test scale honestly:** Attempt #2 expands the workflow and preserves a strong in-distribution preference result, without establishing stronger generalization.

## Source context

- Adaption Labs: https://adaptionlabs.ai/
- Adaptive Data: https://adaptionlabs.ai/adaptive-data
- AutoScientist: https://adaptionlabs.ai/auto-scientist
- AutoScientist announcement: https://adaptionlabs.ai/blog/autoscientist
- AutoScientist Challenge: https://adaptionlabs.ai/blog/autoscientist-challenge

## Verification notes

- Reviewed the rendered public site at 1440px desktop and 393px mobile widths.
- No horizontal overflow or browser console errors were found.
- Figure animations completed correctly and reduced-motion handling is present.
- The main mobile problem is screenshot shrinkage, not CSS cropping.
- All four Kaggle artifact URLs returned HTTP 200 during this audit.
- Hugging Face artifact reachability could not be confirmed because connections to the Hugging Face domain were reset by the audit environment; this is not evidence that the links are broken.
