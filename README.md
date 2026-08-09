# Training a Finance Model with AutoScientist

Standalone technical write-up documenting three AutoScientist experiments in evidence-grounded equity and market research with Adaption Labs.

The report covers source-data extraction, Adaptive Data, AutoScientist training, evaluation results, limitations, and the public-release status of associated artifacts.

## Public records

- Production report, currently showing Attempts #1–2: https://adaptions-writeup.vercel.app/
- AdaptMarket repository: https://github.com/Kitkitkittt/AdaptMarket
- Pending AdaptMarket history update: https://github.com/Kitkitkittt/AdaptMarket/pull/1

This branch adds Attempt #3 to the report and links its resources to the AdaptMarket repository. The companion AdaptMarket pull request adds the model card, methods, aggregate results, release boundaries, and complete three-experiment history.

## Open locally

The site has no build step or runtime dependencies. From the repository root, run:

```bash
python3 -m http.server 8787
```

Then visit `http://127.0.0.1:8787/`.

## Repository layout

- `index.html`: the complete responsive report.
- `assets/`: the cover, favicon, and figures referenced by the report.
