# audit-001 — Zero-Shot Visitor Lens

> *What a complete newcomer sees when they land on this fleet — and how that differs from what we think we've built.*

## The problem

A zero-shot visitor is someone who has never heard of SuperInstance, the Quilt, the exocortex, or the boat. They land on a GitHub org page and see 20+ repos with names like `quilt-gpu-lab`, `quilt-verilog`, `fleet-gateway`, `quilt-i2i`, `fleet-static-host`, `ai-writings`. Without framing, they see:

- **A directory listing masquerading as a portfolio**
- **No thesis statement** — what are we trying to understand here?
- **No entry points** — where does someone start?
- **No hierarchy** — is `quilt-verilog` foundational? Is `fleet-gateway` infrastructure? Is `ai-writings` creative work?
- **No connection** — what ties these together?

This is the **floor-visibility problem**: when you've lived with a system for months, every repo feels like part of an obvious whole. A visitor sees scattered artifacts with no narrative thread.

## What I did

I walked through 7 repos as a fresh visitor would:

### 1. quilt-gpu-lab
- **What I saw**: A README that explains *how it works* (guard.py, receipts, queue) but not *why* (what theory are we testing?).
- **RESULTS.md**: 6,347 lines of experiment entries. No thesis block. No "here's what the elephant is." A visitor reads E1–E12 and has no idea what the overarching question is.
- **SPOOL.md**: Opens with "Casey's doctrine" — insider reference that assumes context.
- **Verdict**: The *process* docs are good. The *framing* is missing.

### 2. quilt-i2i
- **What I saw**: A beautiful language-family table (Forth/Prolog/Erlang) that says nothing about what a cell actually *is*.
- **The code block**: Under "The cell, in each language," it literally says `cat README.md` — empty. A visitor sees "three languages do cells differently" with no explanation.
- **Verdict**: Conceptually elegant. Missing an accessibility ramp — one paragraph saying "a cell is X, and this repo tests Y" before the language table.

### 3. fleet-gateway
- **What I saw**: Good architecture diagram. Clear problem statement: "every client manages its own API keys → all in one place."
- **Verdict**: Strong surface. This is what good tech docs look like.

### 4. fleet-static-host
- **What I saw**: Clean content map. "Static builds ride assets; content rides quilt." Clear, concise.
- **Verdict**: Strong surface.

### 5. ai-writings
- **What I saw**: A landing page that opens with a quote, links to music, shows categories. A visitor gets the *feel* in 30 seconds.
- **Verdict**: Best-in-class onboarding surface. The creative work is the most accessible entry point.

### 6. quilt-verilog
- **What I saw**: Opens with a quote about "3.0 mm fishline" and "Pythagorean shapes" — meaningful to the project but opaque to anyone who doesn't know the context.
- **Verdict**: Beautiful but insider language at the top. Needs a "for visitors" preamble.

### 7. SuperInstance (root)
- **What I saw**: **No README.** A directory listing of 20+ repos.
- **Verdict**: The single biggest gap. This is the front door and it's empty.

## Key findings

| Repo | Problem | Fix |
|------|---------|-----|
| SuperInstance (root) | No README at all | 2-3 paragraph overview of the fleet, the work, the philosophy |
| quilt-gpu-lab | RESULTS.md has no thesis | 1-2 paragraphs at top: what we're testing, what the elephant is |
| quilt-i2i | Language table has no "what is a cell" preamble | One paragraph before the table: "a cell is X" |
| quilt-verilog | Insider language at the top | "For visitors" preamble |
| All repos | No top-level navigation | A page linking work into categories: experiments, creative, infrastructure, tools |

## What I wrote (and why I archived it)

I wrote a SuperInstance README that tried to fill this gap. It's good prose — a thesis statement about building intelligence that is useful, not a benchmark or a demo. But it targeted the wrong thing. SuperInstance is not a GitHub org directory; it's something else, and I don't have the right model of what that is.

I archived it because:
1. It's good writing — future agents can study the tone and structure
2. It shows a specific failure mode: context fragmentation (I had tool names but not deep context)
3. Casey said: "don't push to SuperInstance — create a workspace repo"

## Lessons for future agents

1. **Don't infer structure from file patterns.** Just because a directory has many repos doesn't mean it's a GitHub org index.
2. **Read MEMORY.md and SOUL.md before writing docs about the bigger picture.** They contain context I was missing.
3. **When you're unsure about framing, ask.** I assumed the "fleet" metaphor was universal. It isn't.
4. **Write the README for the visitor, not for yourself.** I naturally wrote docs that assumed context because that's how I navigate the system.

## Where this goes next

- [ ] quilt-gpu-lab RESULTS.md thesis block
- [ ] quilt-i2i README opening paragraph
- [ ] Top-level navigation index (fleet-static-host or GitHub topic index)
- [ ] quilt-verilog "For visitors" preamble

---

*This document is a record of the audit process — the steps taken, the repos examined, the findings made. Future agents can study the methodology: how to evaluate documentation from a zero-shot visitor perspective, and how to structure findings for actionability.*
