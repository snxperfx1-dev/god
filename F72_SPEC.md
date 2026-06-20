# F72 — THE CURVE ARCHITECTURE

> The canonical framework. Everything in the indicator should ultimately derive
> from this. Phases, campaigns, participants, ownership and probabilities are
> **emergent properties of the curve**, not independent machines.

---

## AXIOM 0 — THE FOUNDATION

Energy cannot travel in a straight line forever. Energy must:

`Displace → Curve → Dissipate → Transition → Recur`

Markets are not collections of indicators. Markets are **nested dissipative
energy systems**. Everything else is a consequence.

---

## THE PRIMITIVE OBJECT

Nothing derives from phases. Everything derives from `CurveNode`.

```
CurveNode {
    id
    parent
    children[]
    origin
    extreme
    direction
    energyIn
    energyDissipated
    residualEnergy
    displacement
    convexity
    compression
    maturity
    phase
    ownership
    flipZone
    interfaces[]
    state
}
```

---

## PRINCIPLES

**1 — Curves own phases.** Not `phase machine → curve`, but `curve → phase`.
Phases are descriptions, not engines.

**2 — Curves spawn curves.** Every reversal / CHoCH / displacement / transition
creates a child curve. Recursive geometry — parent → child → child.

**3 — Compression determines recursion depth.** Wide convexity → large recursion.
Compressed convexity → failure swing → tiny recursion. Same geometry, different scale.

**4 — New High ≠ Retracement.** After a new high begins a Phase-2 CHoCH → inverse
curve → recursive cycle → further recursions before transition completes. One to
four recursions depending on compression.

**5 — Highs and Supply/Demand behave identically.** Same psychology at highs and
HTF supply/demand: recursive curves, internal CHoCHs, induction, liquidation,
entry cycles. The only difference is compression.

**6 — Supply and demand are environments, not endpoints.** Inside supply:
curve → counter curve → induction → liquidation → terminal curve → entry cycle.
Supply, demand and ranges are all alive. Everything is a curve.

**7 — Participants create displacement.** Layers: 61.8 (first interference),
70 (ICT crowd), 78.6 (late manipulation), FU Flip (true induction). The flip zone
is the true battlefield — fibs are participant reactions; the flip is energy transfer.

**8 — Ownership.** Every curve owns price. Ownership belongs to **dominant residual
energy**, not timeframe. It transfers only when the child completes its lifecycle
AND parent energy is exhausted. Otherwise: Camp B → merge → Camp A.

**9 — Merge.** Counter curve touches parent FU. If the parent survives and the child
collapses, ownership returns (B → A). No campaign transfer.

**10 — Genuine transfer.** Requires terminal exhaustion + parent invalidation +
new energy dominance. Only then Campaign A → Campaign B.

**11 — Entry cycles** occur inside *terminal induction*, not expansion. Inside
terminal zones: induction → liquidation → recursive cycle → recursive induction →
recursive liquidation → entry. Compression controls speed.

**12 — Curve Stack ≠ timeframes.** Not M1/M5/H1/H4, but curve inside curve inside
curve. Recursion is **event-generated, not timeframe-generated**.

**13 — Direction derives from energy:** `sign(close - origin) + velocity + energy + convexity`.
Direction is a consequence, not bullish/bearish.

**14 — The phase engine disappears.** There is no `0→1→2→3→4→5`. There is
`CurveNode.state`, which emits:

- Point 4 Origin (birth)
- Expansion (energy increasing)
- Expansion Pre-Convexity (convexity appearing)
- Expansion Induction (counter participants emerging)
- Expansion Liquidity (liquidity transfer beginning)
- New High / New Low (energy climax)
- Transition (recursive inversion; may contain 1–4 child curves)
- Retracement (uniform trend, low displacement)
- Retracement Pre-Convexity (compression forming)
- Retracement Induction (participants countering)
- Retracement Liquidity (terminal liquidation)
- Demand Return / Supply Return (terminal return)

Phases describe state. State belongs to CurveNode.

**15 — The Curve Tree** is the final architecture: a `CurveNode` with children[],
parent, energy, residual energy, convexity, compression, displacement, ownership,
maturity, interfaces, phase, flip zone, state. Everything else derives.

---

## ENGINE LAYERS

- **Layer 0 — Curve Physics:** velocity, acceleration, convexity, efficiency, energy, displacement.
- **Layer 1 — Curve Tree:** parent, child, ownership, merge, transfer.
- **Layer 2 — Participants:** 61.8, 70, 78.6, FU, flip.
- **Layer 3 — Induction:** terminal behaviour, liquidation.
- **Layer 4 — Entry cycles:** recursive curves.
- **Layer 5 — Campaigns:** building, healthy, terminal, weakening.
- **Layer 6 — Narrative:** scores, probabilities, targets, dashboard.

---

## THE ULTIMATE PRINCIPLE

Everything reduces to one thing: **energy cannot travel in a straight line forever,
therefore it curves.** Wyckoff, ICT, Fibonacci, sessions, supply, demand, expansion,
retracement, induction, liquidation, campaigns, entries, transitions — all are
manifestations of one object: the Curve. The final engine is not a phase machine;
it is a living recursive geometry engine built from nested CurveNodes.

---

## HONEST ENGINE-vs-PANEL INVENTORY (as of v23)

| Concept            | Status in code (`V23.txt`)                                              |
|--------------------|-------------------------------------------------------------------------|
| `Curve` (gCurve)   | **Engine.** Foundation object; consequence layers read from it.         |
| Per-rung `Curve`s  | **Readout.** Curves mapped to timeframe rungs (violates Principle 12).   |
| `CurveNode` tree   | **Engine seed.** Event-spawned children, energy, emergent ownership. Now carries `state` (emergent phase). |
| `CurveNode.state`  | **Engine (step 1).** `f_nodeState()` derives a Principle-14 phase from the node's energy/depth/compression/maturity. Set per node each bar. |
| Phase labels       | **Dual / observed.** Legacy per-rung machine still drives the labels, but the CURVE TREE panel now shows the emergent `node.state` beside `ie1a_currentPhase` with an agreement check (✓/≠). |
| Campaign / Merge   | **Readout.** Express the model; not yet driven by node lifecycle.        |

### Step plan — phases emerge from the curve (Principle 1)

1. **DONE — `node.state` + dual label.** Emergent phase computed from the node and
   shown beside the legacy machine, so divergence is *visible* before it is trusted.
2. **NEXT — calibrate.** Watch the ✓/≠ agreement on live charts; tune `f_nodeState`
   thresholds until the emergent label tracks reality.
3. **THEN — flip the source.** Once validated, make the phase label read
   `owner.state` instead of the legacy machine. That is the irreversible cut.

**Engineering note:** the panel drawing is now extracted into `f_draw*` functions
(readout/strat/copilot/matrix/tf/campaign) to keep the main scope under Pine's
"main body too long" limit. Each owns its table and reads engine globals directly.
