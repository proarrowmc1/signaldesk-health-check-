# SignalDesk — Weekly Health Check

**Track A (Fictional Domain Packet)**

## What this is
A small, reusable tool a SignalDesk teammate runs on the weekly usage export to
get an honest read in seconds: **what's working, what's suspicious, and what to
look at next** — without trusting a bad average. It ships as a script so it can be
re-run weekly; the notebook shows the reasoning.

```bash
python signaldesk_health_check.py                 # bundled sample
python signaldesk_health_check.py next_export.csv  # any weekly export
```

## Audience
A product/ops teammate who owns SignalDesk and needs a next decision — not an
analyst. Output is plain language, no BI stack.

## The one angle
*Can we trust this week's numbers, and did a change help or hurt?* I did not try
to answer every question in the packet — the tool picks the highest-value read.

## Data
`sample-data/product_usage_events.csv` — the fictional challenge export (41 rows,
3 workflows, Aug 1–7 2026). No private data.

## Assumptions & judgment calls
- `acceptance_rate` and `completion_rate` are the trusted signals. `median_confidence`
  is model self-reported (not correctness) — reported, never used for a verdict.
- All metrics are **rates, not raw counts** (workflows differ ~10× in volume).
- The demo-account spike (>2.5× typical volume) is **excluded from trends**.

## Issues found (all reported, none silently cleaned)
Duplicate export row; team casing (`product`/`Product`); `n/a` in a numeric column;
missing values; a demo-account traffic spike.

## What I did NOT conclude
The Aug-7 Support policy change *looks* bad, but it's one partial day. The tool
flags it and says **collect 3–5 more days, then re-run** rather than calling it.

## Next steps
Fix the export at source; collect more post-change data; read Feedback-clustering
outputs by hand while volume is low.
