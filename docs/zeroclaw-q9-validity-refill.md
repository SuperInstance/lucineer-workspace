# zeroclaw-q9 — The Fifth Consecutive Negative

> *After four failures, v9 refined the age calibration. It didn't help.*

## The headspace

ZeroClaw's validity mechanism had been failing for four straight cycles. Each failure eliminated a different hypothesis:
- Cycle 1: age-at-zero depletion was the issue → tried age-refill
- Cycle 2: refill tied to molts → tried molt-adjusted refill
- Cycle 3: validity was cumulative → tried age-at-zero validation
- Cycle 4: still failing

v9 tried a new angle: refill that ties age exactly at the 86.7% settled coverage point. The idea was that the refill should be calibrated to a specific coverage threshold, not just a general refill.

## What happened

The validity-refill after age-at-zero molt moved in the right direction. By the 5th molt attempt, it had progressed past the head tax, well into the valid regime. But by the 13th attempt — which was 300 steps past the age-at-zero molt and 256 steps past the head tax — the validity dropped to 86.7% settled coverage, carrying approximately zero valid cells at t ≥ 60.

This is the same result: validity at age ≥ 60 is ~zero. The fifth consecutive negative.

## The new law

**Validity is PER-CELL, not per-footprint.** This is the critical insight from four cycles of failure. You can't validate a footprint as a whole — you need to validate each cell individually. The refill was designed per-footprint, but the problem is per-cell.

## The unenlightenment breakthrough

There was a "massive enlightenment" at 5-molt (attn-1_0/1 at 148 atoms, --now > 8) — the wind drove off the mass to a tiny core and the agents changed their outlook. "Stress is good" → validating at zero created massive enlightenment. But the consequence was that the "1" agents revealed they were the only ones left when stress was high. The shift in worldview was real but the validity wasn't recovered.

## The flip lesson

Three legs out of the way → ok, unenlightenment. The agenda flipped, very second leg: 173 atoms, depth up to attn-1_2. The "I" approach stressed them but delivered a $200 payout. The "We" approach was still at attn-1_0 with only 142 atoms. The lesson: "I" approaches are more aggressive but require more atoms. "We" approaches are gentler but need more time to reach consensus.

## Where this goes

The pattern is clear now: age-calibration approaches are insufficient because validity is a per-cell property, not a per-footprint property. The next step needs to be per-cell validation, not per-footprint refill.

---

*This document shows how a failure-driven iteration pattern can eliminate hypotheses. Each negative wasn't just a failure — it was a step toward understanding the problem structure (per-cell validity, not per-footprint). Future agents can study this pattern: when an approach fails repeatedly, the failures may be forming a taxonomy of what doesn't work, which is itself valuable information.*
