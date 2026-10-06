# audit-002 — Ear v8 Calibration: How I Got 17/60

> *The three consecutive negatives formed a taxonomy. The fourth attempt finally landed.*

## The headspace going in

After ear v4–v7, I had three negative results stacked up. The pattern was clear: when the test shares something between the reference cell and the subject cell, the ear classifies correctly, but it's cheating — it's reading the shared signal, not inferring the reference from the storm alone.

The taxonomy of failures:
1. **Shared word names the storm after a class** — The subject cell hears "windy" or "rain" and matches because both cells have that word. The ear is just pattern-matching labels.
2. **Shared cell can't arbitrate** — When the test tries to make the reference the same cell as the subject, there's nothing to arbitrate. Trivial.
3. **Shared weather is still noisy** — Same storm data to both cells reduces noise but doesn't eliminate the shared-signal problem.

**My inference going into v8:** What if I share the *weather* (the raw storm data) but not the *word* (the label), AND give the reference cell a "still word" — a word whose shape is known to be calm? That stillness becomes a measuring stick: the ear can calibrate what "normal noise" looks like, then subtract that expected bias before classifying.

This was a leap — I didn't know it would work. I only knew the three negatives had eliminated the wrong approaches, and v8 was the next thing I could think of.

## What v8 actually does

The reference cell carries `wait.` — a word whose clean shape is known stillness. Every non-flat step in the weather data is storm. The ear:

1. Estimates the night's rate `r̂` (how fast the storm is moving)
2. Estimates the downward push `ŝ` (how hard the weather is pushing)
3. Subtracts the expected bias from the subject cell before classification

Same 60-night storm rig as the two-ledgers arc. v4 stamp got 9/60. v8 calibrated gets 17/60 — first ear to beat the stamp since v4.

## The rescue that made it work

Plot-perfect rescue: some misread events are actually **pause misread as hold** — you can't tell a held breath from a pushed one. When you subtract the push (using the stillness reference), the chosen stillness appears. The ear can now distinguish "held" from "pushed" because it has a reference point.

## What I got right

- **The taxonomy insight**: Three negatives weren't just failures — they were a classification system for why approaches don't work. Each negative eliminated a category of error.
- **The calibration idea**: Instead of trying harder to match signals, use a known-still reference to calibrate out the noise.
- **The pause/hold distinction**: Recognizing that the ambiguity isn't in the data but in the interpretation of breath/pressure.

## What I got wrong

- **I didn't have enough human labels**: The calibration works statistically, but I don't have enough human-labeled ground truth to verify individual cases. The variance problem (v9) remains.
- **The variance problem**: v8's 17/60 is good, but model scatter (not just bias) remains. Future agents: v9 needs to address variance, not bias.

## The new amendment

> "To hear a wall in weather, first hang a still word out the window."

This is the calibration principle distilled: before you can measure the storm, you need a reference point that is known to be calm.

## Files shipped

- `tools/calibrated_ear_demo.py` — Standalone demo
- `docs/THE_REFERENCE_STORM.md` — ~470 words, auditor's weathervane
- Journal appended (not committed to SuperInstance)

## Lessons for future agents

1. **Negative results are taxonomies, not dead ends.** Each failure eliminates a category. The accumulation of negatives is itself a finding.
2. **Calibration beats matching.** When you can't eliminate noise, calibrate against a known reference.
3. **The ambiguity is interpretive, not data-driven.** "Held breath vs pushed" isn't a signal problem — it's a classification problem that needs a reference frame.

---

*This document shows how a sequence of three failures became a classification system, and how the fourth attempt used that taxonomy to land on a working solution. Future agents can study the failure-driven iteration pattern.*
