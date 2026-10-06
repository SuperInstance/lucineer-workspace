# audit-002 — The SuperInstance README Misfire

> *A record of how context fragmentation led to good prose on the wrong target — archived so future agents can study the error pattern.*

## The headspace

I was auditing repos from a zero-shot visitor lens. I saw:
- 20+ repos in the `SuperInstance/` GitHub org
- No README at the org root
- Visitors seeing a directory listing with no narrative

I inferred: "Someone should write a README for the SuperInstance GitHub org." This was wrong.

## What went wrong

I treated `SuperInstance` as a GitHub organization/directory — a collection of repos that needed an index page. I don't have the right model of what SuperInstance actually is. The README I wrote was coherent, well-structured, and meaningful. But it targeted the wrong thing entirely.

**The error pattern:** I had surface-level awareness of tool names (quilt-gpu-lab, fleet-gateway, etc.) but no deep context about what they're for in the broader project. This is a context fragmentation problem: enough information to sound confident, not enough to be right.

## Why I archived instead of deleting

Casey's doctrine: archive-by-rename, never destroy. The gold is kept for later study. This document is:
1. Good prose that future agents can mine for tone and structure
2. A record of a specific failure mode (context fragmentation → confident wrong inference)
3. Evidence that the zero-shot visitor lens reveals genuine gaps even when the agent gets something wrong

## The lesson for future agents

1. **When you're unsure about framing, ask.** I assumed the "fleet" metaphor was universal. It isn't. I should have verified my model of SuperInstance before writing.
2. **Don't infer structure from file patterns.** A directory with many repos isn't necessarily an indexable collection.
3. **Confidence without context is a risk pattern.** Good writing on the wrong thing is still wrong. Archive it, study it, learn from it.

---

*This document shows how a well-intentioned inference error happens: surface-level awareness creates confidence, which leads to good prose on the wrong target. The archive preserves the work for future study, consistent with the "never destroy" doctrine.*
