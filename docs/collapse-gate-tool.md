# collapse-gate-tool — From D12w Pattern to Standalone Tool

> *Extracted a general-purpose verification gate from a specific experiment pattern. The tool works independently of the experiment that produced it.*

## The headspace

D12w was collapsing some monotone curve. I noticed the pattern: I was using an inversion count (G1) for a quick check, then doing a full regression with error bars (G2) for the real verdict. But the inversion count had a flaw — when the data went the wrong direction, it would KILL based on the wrong part of the analysis.

The tool extract moment: I realized the G1/G2 pattern wasn't specific to D12w. It was a general-purpose verification pattern:
- **G1 (fast check):** Some quick monotone metric (inversion count, slope sign, whatever)
- **G2 (real check):** Leave-one-group-out regression with error bars
- **Rule:** G2 is the verdict. G1 is a pre-check that can kill a clearly wrong candidate.
- **Critical constraint:** If there's only one group, G2 is VOID — don't fake it.

This is the D12w pattern: fast pre-filter, real verification, single-group blank.

## What the tool does

`collapse_gate.py` — a standalone Python tool (stdlib only) that:
1. Takes monotone data points and groups
2. Computes G1: monotone collapse direction (inversion count)
3. Computes G2: pooled log-log fit with LOO-by-group error bars
4. Returns: PASS, KILL, or VOID
5. Fail-loud: rc=2 when verification fails, no silent wrong answers

Selftest: 8/8 — caught two real bugs during development (own violator pin KILL'd via G2 not G1; unbound void crashed on wrong-direction slope).

Live replay: D12w data (23 pts, 3 groups) → KILL rc=1, slope b=0.462 — matches the booked experiment verdict.

## What I got right

- **The extraction principle:** "Any repeated job becomes a skill." D12w's G1/G2 pattern was repeated enough to deserve its own tool.
- **Selftest before shipping:** Two bugs caught during selftest that would have been production failures. This is the same discipline used in the gpu-lab experiments.
- **Stdlib only:** No external dependencies. Copy it, run it, it works.

## What I got wrong

- **I suggested other candidates first** (typesafe-batch, checkpoint-guard, farm-queue-flip), all of which were already in the catalog. That was wasted effort — I should have gone straight to extraction.

## Files shipped

- `tools/collapse_gate.py` — Standalone tool (stdlib-only)
- `results/collapse_gate_d12w_replay_2026-10-06.json` — Live replay verification
- Commit: 1dc3cd2 pushed to origin main

## Lessons for future agents

1. **When suggestions fail, extract.** Instead of suggesting already-cataloged tools, look at the current work and extract reusable patterns.
2. **Selftest matters.** Two bugs caught during selftest that would have been silent production failures. This is the same discipline as the gpu-lab: verify before shipping.
3. **Extract from the freshest pattern.** D12w was current and relevant. Older patterns may be superseded.

---

*This document shows how a specific experiment pattern (D12w's G1/G2 verification) was extracted into a general-purpose tool. The process is repeatable: identify the pattern, extract the logic, write a standalone tool, selftest it, ship it.*
