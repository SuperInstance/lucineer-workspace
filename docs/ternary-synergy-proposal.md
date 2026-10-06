# ternary-synergy-proposal — RPS-Biased Mutation for Ternary GA

> *What happens when you force a rock-paper-scissors topology onto a genetic algorithm's mutation operator?*

## The headspace

Two independent projects converged on the same data structure:

**ternary-ga**: A genetic algorithm where each gene is {-1, 0, +1}. Standard mutation flips any allele to a uniformly chosen different allele (so +1 → {0, -1} with 50/50 probability). The problem: on multimodal ternary landscapes, this can get stuck.

**ternary-spiral**: A cellular automaton on the same {-1, 0, +1} lattice that uses rock-paper-scissors cyclic dominance (+1 beats 0, 0 beats -1, -1 beats +1). The result: never-freezing spiral waves. The system never reaches a static equilibrium — the cyclic structure keeps driving activity forever.

**The insight**: What if I bias ternary-ga's mutation along the RPS dominance cycle? Instead of uniform mutation, the probability of flipping +1→0 is higher than +1→-1, following the cyclic order. This turns a spatial GA population into an excitable medium where dominance fronts sweep stagnant regions. Premature convergence becomes structurally impossible for any cyclic bias q > 0.

## The proposal

- **Cyclic-biased mutation**: Flip direction follows RPS dominance (+1→0 > +1→-1, 0→-1 > 0→+1, -1→+1 > -1→0)
- **Parameter q ∈ [0, 1]**: Controls bias strength. q=0 is uniform mutation, q=1 is pure RPS cycle
- **Stagnation detector**: ternary-genome's existing stagnation detector becomes the scheduler — when diversity drops, increase q temporarily

**Claim**: q ≈ 0.7 reaches global optima on multimodal ternary landscapes in ≥30% fewer evaluations than uniform mutation while holding ≥2× population diversity. At q=1, stagnation events should go to exactly zero.

## Why this matters

This would be a convergence point between two research tracks:
1. The hill-climbing/optimization side (ternary-ga, D12w collapse-gate)
2. The excitable-media/spiral-wave side (ternary-spiral)

Both use the same {-1, 0, +1} algebra but from different directions. If the synergy holds, it validates the idea that the same algebraic structure can be exploited from multiple angles simultaneously.

## Files

- No code yet — this is a proposal, not a shipped tool
- Repos involved: ternary-ga × ternary-spiral (with ternary-genome as q-controller)
- Next step: implement the biased mutation, run on a simple multimodal ternary landscape

## Lessons

1. **Convergence is a signal.** When two independent projects land on the same structure, investigate the overlap.
2. **Modularity enables synergy.** Having ternary-ga and ternary-spiral as separate repos made this connection possible — they could evolve independently until the common structure was obvious.
