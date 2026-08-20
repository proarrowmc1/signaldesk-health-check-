# AI_NOTE

## Did I use AI?
Yes — an AI coding assistant, the way I'd use one on a real task: to move fast on
boilerplate and to pressure-test my thinking, while keeping the judgment calls
mine.

## Where AI helped
- **Scaffolding.** Drafting the pandas cleaning steps (dedup, `str.title()` casing
  normalization, `pd.to_numeric(errors="coerce")` for the `n/a` cell) and the
  report-rendering strings. Mechanical code I know how to write but didn't want to
  hand-type under the time limit.
- **Sanity-checking my framing.** I used it as a second pair of eyes on *whether*
  rate-based metrics + a spike exclusion were the right call, and to make sure I
  wasn't missing a planted issue in the data.

## What I decided myself (not the AI)
- **The scope.** Answering "can we trust this week's numbers?" instead of building
  a dashboard was my call — the packet explicitly warns against a big BI project.
- **Excluding the demo spike and refusing to judge the Aug-7 policy change.** These
  are the two most important judgment calls in the exercise. An AI left alone will
  happily average everything and hand you a confident verdict; I chose to exclude
  the spike from trends and to explicitly *not* conclude on one partial day of data.
- **Distrusting `median_confidence`.** Treating model-reported confidence as the
  least trustworthy signal was a deliberate decision, reinforced by the packet.

## What I independently verified (required)
I did not take the tool's headline number on faith. I **re-computed the Lead-summary
acceptance rate by hand**, summing the funnel across the week with both demo rows
removed: 450 sessions → 350 completed → 273 accepted = **78%**, matching the tool's
output exactly. I also confirmed the row counts reconcile (41 raw → 40 after
dropping the duplicate → 39 used after excluding the demo spike). This is why I
trust the acceptance figures the report prints.

## Where I'd be cautious trusting AI further
On the borderline calls — e.g., the spike threshold (2.5× typical) and the
low-volume caveat — an assistant will pick a number and sound sure. I kept those
thresholds visible and documented so a human can argue with them, rather than
burying them.
