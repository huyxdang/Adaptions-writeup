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
