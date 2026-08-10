# Website improvement backlog

This file records the recommendations that remain after the approved credibility corrections from 2026-08-10. We will work through these one by one. “Scaling 50x” is an intentional public-facing editorial choice and is not a backlog item.

## P0 — Credibility and skim comprehension

- [ ] Add a compact two-row proof overview beneath the hero showing the full path from source reports through **Adaptive Data**, **AutoScientist**, and the scoped evaluation results.
- [ ] Add an evaluation-protocol disclosure covering the evaluator, comparison count, prompt provenance, order randomization, ties, decoding settings, and relationship to the local split. Mark unavailable details as unavailable.
- [ ] Disclose the known Attempt #1 split contamination and scope the 84:16 result as an in-distribution diagnostic.
- [ ] Add a dedicated 1200 × 630 social card featuring the title, both authors, Adaption Labs, and one carefully scoped result.
- [ ] Add a result-led Open Graph description.

## P1 — Make 80% skimming achievable

- [ ] Replace Figure 1 with a project-native workflow visual: report evidence + conclusion → remove conclusion → reconstruct supported prompt → **Adaptive Data** → **AutoScientist** → preference evaluation.
- [ ] Rebuild Figures 6, 9, and 10 as responsive native visuals while keeping the platform screenshots available as source evidence.
- [ ] Rewrite figure captions so the bold text states the takeaway rather than only the figure number.
- [ ] Add one shared-prompt base-versus-adapted model-response comparison, annotated against equity-research criteria.
- [ ] Add a “What each attempt established” conclusion before Acknowledgements.
- [ ] Separate operational measurements—source breadth, row count, and platform quality score—from model-evaluation evidence throughout the article.
- [ ] Strengthen Resources with the AdaptMarket repository, Challenge rules, public Adaption dataset pages, a methodology note, and a compact Adaption call-to-action block.

## P2 — Editorial, accessibility, and performance polish

- [ ] Replace “institutional-grade” with a precise source description such as “sell-side” or “institutional research reports.”
- [ ] Change “Southeast Asia’s listed companies” to “Southeast Asian listed companies.”
- [ ] Use `source reports`, `seed examples`, `generated variants`, `training rows`, and `unique generated items` consistently.
- [ ] Reconcile the subtitle’s “5,000+” with the article’s “about 7,000,” or explain the counting boundary.
- [ ] Explain why the base model changed between attempts and whether the team or **AutoScientist** selected it.
- [ ] Describe the 72% similarity threshold as a leakage-risk heuristic.
- [ ] Define “leakage groups” or replace it with a clearer term.
- [ ] Move dense LoRA and generation settings into expandable technical details.
- [ ] Increase mobile caption and resource text toward 14px and enlarge interactive hit targets.
- [ ] Add a table caption and keyboard accessibility to the horizontal-scroll table.
- [ ] Add print and full-page-capture CSS that forces animated figures visible.
- [ ] Compress `assets/extraction-doc-to-prompt.png` to AVIF or WebP.
- [ ] Add publication and modified dates, Article JSON-LD, `article:author` metadata, `robots.txt`, and a minimal sitemap.
