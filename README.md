# llm_fine_tune — Traditional Chinese (zh-TW) quality pilot

Extracted from [st101cc/llm_fine_tune](https://github.com/st101cc/llm_fine_tune) (source commit `f54ca85e94a070fd3e90f1542067bd6576a25c74`),
where it was removed from the main app. It holds the zh-TW / TAIDE dataset-quality pilot: dataset audit
for mainland terms, reviewed dataset versions, original-vs-reviewed QLoRA comparison, TaiwanChat
experiment, and the three-model judge panel.

The original operations guide is in [docs/quality-pilot-operations.md](docs/quality-pilot-operations.md).

## Contents

| Path | What |
|---|---|
| `trainer/quality_*.py` | Audit policy, store, models, GPU-budget pilot, training handoff, API routes |
| `trainer/comparison.py`, `comparison_job.py` | Original-vs-reviewed comparison |
| `trainer/judge_panel.py`, `panel_job.py` | Local judge panel |
| `trainer/taiwanchat_experiment.py` | TaiwanChat experiment |
| `public/quality.js`, `quality.css` | Browser UI pages |
| `quality-proxy.mjs` | Streaming export proxy for the Node server |
| `validation/taiwanchat-terms.json` | Approved mainland-to-Taiwan term list |

## Not a standalone app

These files were written against the main ForgeTune app and still import modules that stay there
(`advisor`, `benchmark`, `evaluator`, `graph`, `train`). To run them, copy them back into a
llm_fine_tune checkout at the source commit above and re-add the wiring that the removal commit deleted:
`install_quality_routes` in `trainer/app.py`, the quality branches in `trainer/app.py`, `graph.py` and
`train.py`, the `streamTrainer` route in `server.mjs`, and the nav links and routes in
`index.html` / `public/app.js`. `git show` on that removal commit in llm_fine_tune shows all of it.
